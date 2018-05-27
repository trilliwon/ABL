---
layout: post
title:  "Functional Programming Concepts"
date:   2018-03-14 01:00:00 +0900
tag: [Programming]
---

# First class functions

> 함수가 expression 으로 사용될 있으면 일급함수이다. 오브젝트로서 사용될 수 있으면 일급함수.
> 함수를 값으로써 변수에 대입하거나 함수의 리턴값으로 사용되면 일급함수다.

---

# Higher-Order Functions (고차함수)

> 고차함수란 함수(일급함수)를 인자로 받거나 결과로 리턴할 수 있는 함수를 말한다.

---

# Immutability

> 생성된 후에 상태를 변경할 수 없는 성질을 말한다. ex) immutable object.

---

# Currying

> 여러개의 인수를 받는 함수를 단일 인수를 받는 함수들로 만드는 기법.

---

# Side Effect

> 부가작용, 원하는 작용 이외의 작용을 하는 것. 함수가 불려지면 외부의 특정 상태를 변경시키는 것.

---

# Recursion

> 함수가 자기 자신을 호출함으로서 문제를 해결하는 기법.

---

# Lazy Evaluation

> 계산 결과가 필요할 때까지 계산을 늦추는 것이다. 필요할 때 메모리를 할당하거나 하는것.
> (a and b)가 있을 때 a 가 거짓이면 b는 호출하지 않아도 된다. b가 lazy 이면 작업을 줄일 수 있다.

---

# Stream

> 무한한 sequence를 말한다. 리스트로 사용될 수 있고 필요할 때만 계산할 수 있다. lazy sequence 라 불리기도 한다.

---

# Closure

> 실행되는 코드의 블럭이다. 함수는 이름이 있는 클로져라고 할 수 있다.

---

# Trunk

>

---
