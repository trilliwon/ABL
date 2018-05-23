---
layout: post
title:  "PyTorch: Autograd Mechanics"
date:   2018-05-15 15:00:00 +0900
tags: [Pytorch]
---

## [Autograd mechanics](http://pytorch.org/docs/stable/notes/autograd.html)

---

This note will present an overview of how **autograd** works and records the operations.
- autograd 작동방법에 대한 overview

It’s not strictly necessary to understand all this, but we recommend getting familiar with it, as it will help you write more efficient, cleaner programs, and can aid you in debugging.
- 모든 것을 이해할 필요는 없지만, 이해하면 디버깅할 때, 좋은 프로그램 개발할 때 도움이 됨.

---

## Excluding subgraphs from backward (subgraphs를 배제?)

Every Tensor has a flag: `requires_grad` that allows for fine grained exclusion of subgraphs from gradient computation and can increase efficiency.

- 모든 Tensor는 `requires_grad` flag를 가지고 있다. 이 flag는 gradient 계산으로 부터 subgraph를 fine grained exclusion 할 수 있게 해주고 효율성을 향상시킨다.

---

### `requires_grad`
If there’s a single input to an operation that requires gradient, its output will also require gradient. 
- `requires gradient`한  operation에 대해 한개의 input 이 있다면, 그 operation의 output도 `require gradient` 다.

Conversely, only if all inputs don’t require gradient, the output also won’t require it.
- 반대로, 모든 입력에 gradient가 필요하지 않는 경우에만, output도 gradient를 필요로 하지 않는다.
Backward computation is never performed in the subgraphs, where all Tensors didn’t require gradients.
- Backward computation(그래디언트를 계산하기 위한 계산)은 모든 텐서가 gradient를 필요로 하지 않은 subgraphs에서느 실행되지 않는다.

```
>>> x = torch.randn(5, 5)  # requires_grad=False by default
>>> y = torch.randn(5, 5)  # requires_grad=False by default
>>> z = torch.randn((5, 5), requires_grad=True)
>>> a = x + y
>>> a.requires_grad
False
>>> b = a + z
>>> b.requires_grad
True

```

---

This is especially useful when you want to freeze part of your model, or you know in advance that you’re not going to use gradients w.r.t. some parameters.
- 이것은 모델의 특정 부분에서 정지 시킬때, 미리 일부 parameters들에 대해서 gradient를 사용하지 않으려 할때 특별히 실용적이다.

For example if you want to finetune a pretrained CNN, it’s enough to switch the `requires_grad` flags in the frozen base, and no intermediate buffers will be saved, until the computation gets to the last layer, where the affine transform will use weights that require gradient, and the output of the network will also require them.

- 예로, pretrained CNN에 대해 fintune 이 필요할때, frozen base  에서 `requires_grad` flag를 false로 하면 affine transform 이 gradient가 필요한 weights를 사용할 마지막 layer까지 계산될 때까지,  중간 버퍼가 저장되지 않는다.
- 네트워크의 output은 gradient가 필요하다.

```
model = torchvision.models.resnet18(pretrained=True)
for param in model.parameters():
    param.requires_grad = False
# Replace the last fully-connected layer
# Parameters of newly constructed modules have requires_grad=True by default
model.fc = nn.Linear(512, 100)

# Optimize only the classifier
optimizer = optim.SGD(model.fc.parameters(), lr=1e-2, momentum=0.9)
```
---

### How autograd encodes the history

Autograd is reverse automatic differentiation system.
- autograd 는 역 자동 미분 시스템 이다.


Conceptually, autograd records a graph recording all of the operations that created the data as you execute operations, giving you a directed acyclic graph whose leaves are the input tensors and roots are the output tensors.
- 개념적으로 autograd는 graph를 기록한다. graph는 operation을 실행하면서 생성된 데이터인 모든 operations 를 recoding 한다. graph는 방향이 있는 비순환 그래프이고 roots는 output tensors 이고 leaves는 input tensors 이다.

By tracing this graph from roots to leaves, you can automatically compute the gradients using the chain rule.

- 이 그래프를 roots 부터 leaves 까지 추적함으로써, 자동으로 chain rule 을 사용해 gradients를 계산할 수 있다.

---

Internally, autograd represents this graph as a graph of `Function` objects (really expressions), which can be apply() ed to compute the result of evaluating the graph.
- 내부적으로 autograd 는 Function objects (really expressions) 의 그래프로 표현한다. Function objects는 그래프의 값을 구한 결과를 계산 할때 `apply()`될 수 있다.

When computing the forwards pass, autograd simultaneously performs the requested computations and builds up a graph representing the function that computes the gradient (the .grad_fn attribute of each torch.Tensor is an entry point into this graph).
- forwards pass를 계산 할 때, autograd는 즉각적으로 요청된 계산들을 처리하고 gradient를 계산할 함수를 표현하는 그래프를 build up 한다.
- torch.Tensor의 `.grad_fn` 속성은 이 그래프에 대한 시작 point이다.

When the forwards pass is completed, we evaluate this graph in the backwards pass to compute the gradients.
- forward pass 가 완료되면, backwards pass 에서 gradient를 계산 하기 위해 이 그래프를 사용한다.

---

An important thing to note is that the graph is recreated from scratch at every iteration, and this is exactly what allows for using arbitrary Python control flow statements, that can change the overall shape and size of the graph at every iteration.
- 중요한것은 그래프가 매 iteration마다 새로 생성된다는 것이다. 이것은 정학하게 python은 control flow 를 사용할 수 있다는 것이다. 이것을 이용하면 그래프의 전체 size나 shape 를 매 iteration마다 변경시킬 수 있다.

You don’t have to encode all possible paths before you launch the training - what you run is what you differentiate.
- training을 시작하기 전에 모든 가능한 paths를 encode할 필요가 없다. 해야 하는것은 미분해야할 것들이다.

---

### In-place operations with autograd (in-place operation 을 autograd로 한다.)

Supporting in-place operations in autograd is a hard matter, and we discourage their use in most cases.
- autograd에서 in-place operations를 지원하는 것은 어려운것이다. 그리고 대부분의 경우에 in-place operations 사용을 권하지 않는다.

Autograd’s aggressive buffer freeing and reuse makes it very efficient and there are very few occasions when in-place operations actually lower memory usage by any significant amount.
- aggressive buffer 를 비우고 재사용하는 것은 효율적이다. 매우 적은 경우에 in-place operations 가 더 적은 메모리를 사용하낟.
Unless you’re operating under heavy memory pressure, you might never need to use them.
- 메모리가 부족하지 않으면 사용할 필요가 없을 수 있다.

1. There are two main reasons that limit the applicability of in-place operations: In-place operations can potentially overwrite values required to compute gradients.
2. Every in-place operation actually requires the implementation to rewrite the computational graph. Out-of-place versions simply allocate new objects and keep references to the old graph, while in-place operations, require changing the creator of all inputs to the Function representing this operation. This can be tricky, especially if there are many Tensors that reference the same storage (e.g. created by indexing or transposing), and in-place functions will actually raise an error if the storage of modified inputs is referenced by any other Tensor.











