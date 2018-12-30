---
layout: post
title: "Swift Closure"
date: 2018-12-30 3:00:00 +0900
tag: [Swift]
---

## Capturing Values

- 현재 컨텍스트에서 값들을 캡쳐한다. 
- 클로져 자체는 environment 와 state
- A closure is a record storing a function together with an environment.
- A closure—unlike a plain function—allows the function to access those captured variables through the closure's copies of their values or references, even when the function is invoked outside their scope.

## Escaping Closures

> A closure is said to escape a function when the closure is passed as an argument to the function, but is called after the function returns.

---

## autoclosures

- function type 의 파라미터를 클로져로 사용할 수 있도록 해준다.

