---
layout: post
title:  "Trees and Graphs"
date:   2018-10-31 01:16:00 +0900
tags: [Algorithm]
---


# Tree-and-Graph

---  

# Tree

## What is Tree?

- 그래프의 일종이다.
- 트리는 하나의 **root node** 를 가진다.
- 루트 노드는 0개 이상의 자식 노드를 갖는다.
- 자식노드 또한 0개 이상의 자식노드를 갖고 있고, 이는 반복적으로 정의 된다.
- **child node** 가 없는 노드를 **leaf node** 라고 한다.
- **leaf node** 가 아닌 노드를 **internal node** 라고 한다.
- 트리는 acyclic 해야 한다.


```swift

class Node {
	public String name;
	public Node[] children;
}

class Tree {
	public Node root;
}

```


## Binary Tree

- **Binary Tree** 는 자식노드가 최대 두 개인 트리를 말한다.

```swift

class Node {
	public String name;
	public Node left;
	public Node right;
}

```

## Binary Search Tree

- 'all left child nodes <= `n` < all right child nodes' for all Node `n`


## Balanced Tree

- Complete Binary Tree, AVL Tree, Red-Black Tree

## Complete Binary Tree

- 트리의 모든 노드의 높이가 꽉 차 있는 Binary Tree 를 말한다.
- 마지막 level 까지 꽉 차 있지 않아도 되지만 노드가 왼쪽에서 오른쪽으로 채워져야 한다.

## Full Binary Tree

- 모든 노드의 자식노드가 없거나 정확히 두 개 있는 경우

## Perfect Binary Tree

- Complete Binary Tree **and** Full Binary Tree


## Tree Traversals

### In-order Traversal
- left branch, node, right branch

### Pre-order Traversal
- node, left branch, right branch

### Post-order Traversal
- left branch, right branch, node


## Binary Heaps (Min, Max)
- Complete Binary Tree
- 각 노드의 원소가 자식들의 원소보다 작다(크다)
- **root node** 는 전체 트리에서 가장 작은(큰) 원소가 된다.
- `insert` `O(log n)`
- `extract_min` `O(log n)`

  
---

# Trie (prefix tree)

- Seach Tree 이다.
- n-ary tree 이다.
- 각 노드는 문자를 저장한다.
- 스트링을 키로하는 동적 집합(dynamic set)이나 연관 배열(associative array)로 사용됨.
- root is empty string


---

# Graph

- 노드와 그 노드를 연결하는 edge 를 하나로 모아 놓은 것
- 모든 pair of vertices 간에 경로가 존재하는 그래프는 Connected Graph
- acyclic or cyclic 할 수 있다.
- 그래프를 표현할 때는 `Adjacency list`, `Adjacency matrix` 를 사용한다.
- `Adjacency matrix` 는 비효율 적이다.

## Adjacency list

```

class Graph {
	public Node[] nodes;
}

class Node {
	public String name;
	public Node[] children;
}

```

## Adjacency matrix

- NxN boolean matrix 이다. 간선이 존재하면 `matrix[i][j]` 는 `true` 아니면 `false`

---

# Graph Search

## DFS
- 깊이 우선 탐색은 시작 노드에서 다음 분기로 넘어가기 전에 시작한 분기를 완벽하게 탐색한다.

## BFS
- 너피 우선 탐색은 시작 노드에서 시작해 인접한 노드를 먼저 탐색한다.
- Bidirectional BFS : \\( O(K^{d/2}) \\)

> Cyclic Graph 를 탐색할 때에는 visit 을 체크해줘야 한다.


#ds #tree #graph
