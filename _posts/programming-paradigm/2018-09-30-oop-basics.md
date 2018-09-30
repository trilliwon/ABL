---
layout: post
title:  "OOP Basic Concepts"
date:   2018-09-30 14:59:00 +0900
tag: [OOP]
---

# Object Oriented Programming

---

> 실 세계의 개체(Entity)를 속성(Attribute)와 메소드(Method)가 결합된 형태의 객체(Object)로 표현하는 개념. 실 세계의 문제영역에 대한 표현을 소프트웨어 해결 영역으로 mapping 하는 방법으로 객체간에 메시지를 주고받는 형태로 시스템 구성.

### 객체지향 프로그래밍 : 객체, 관계 중심

- 객체지향은 사람의 추상능력, 인식방법에 가까운 개발 방법론.
- attributes와 behavior로 이루어진 객체를 만드는 것
- 프로그램을 독립된 단위인 객체로 보고 각각 객체는 메시지를 주고 받고 데이터를 처리한다.

### 장점
- 소프트웨어 공학의 관점에서 볼 때 S/W의 질을 향상하기 위해 강한 응집력(Strong Cohesion)과 약한 결합력(Weak Coupling)을 지향해야 한다.
- OOP의 경우 클래스에 하나의 문제 해결을 위한 데이터를 모아 놓은 데이터형을 사용함으로써 응집력을 강화하고, 클래스간에 독립적으로 디자인함으로써 결합력을 약하게 할 수 있다.
- 재활용 가능
- 유지보수 가 쉽다
- 대형 프로젝트에 적합
- 코딩이 간단

### 단점
- 처리속도 느림
- 설계가 어려움. 잘 짜는게 어렵다.


### Terms
- attribute = data      = member variable = state = field
- behavior  = operation = member function = method
- class     = concept   = type
- object    = instance  = variable


---

## Fundamental Principles of OOP 

- 클래스 (Class), 객체 (Object), 인스턴스 (Instance)
- 추상화 (Abstraction)
- 상속 (Inheritance)
- 캡슐화 (Encapsulation)
- 다형성 (Polymorphism)

## Abstraction - Class, 추상, 
- Define and execute abstract actions
- 표현 대상의 특징에 대한 서술을 말한다.
- procedural abstraction : 함수
- data abstraction : 구조체, 배열, 포인터

### Object, instance, 실체
- instance of class
- object 는 클래스의 instance 이다. 클래스가 실제로 만들어진것.

## Encapsulation
- Hide the internals of a class
- **Access Control** : public, internal, private ..
- 데이터와 데이터를 다루는 방법을 묶는것
- **내부의 구현은 감추고 모듈 내에서 응집도를 높이며 외부로부터의 노출을 줄여 모듈간의  결합도를 떨어뜨리는 개념**

## Inheritance
- Inherit members from parent class
- 하나의 클래스가 가지고 있던 특징들을 그대로 다른 클래스가 물려 받는것
- 재사용, 유연성
- Overriding : 부모 클래스의 메서드와 같은 메서드를 재정의 하는것, 같은 이름의 메소드가 여러 클래스에서 다른 기능을 하는 것

## Polymorphism
- Access a class through its parent interface
- 상속의 계층을 따라서 각각의 클래스에 한가지 이름을 줄 수 있다. 같은 명령을 다른 오브젝트에 줄수 있다
- Message passing 객체지향관점에서 프로그램은 오브젝트에 message를 보내는 것으로 실행
- `a.method()` : `a` 에 `method()` 라는 메시지를 보낸다.
- Overloading : 같은 이름의 메소드가 인자의 갯수나 자료형에 따라서 다른 기능을 하는 것
- method overloading
- operator overloading

---

# SOLID 원칙

---

## 1. SRP : 단일 책임 원칙 (Single Responsibility Principle)
- 객체는 하나의 책임만을 맡아야 함
- DB 정규화와 비슷함
- 목적: 변화에의 유연성 확보
- 낮은 결합도, 높은 응집도 추구

## OCP : 개방-폐쇄 원칙 (Open Closed Principle)
- 모듈은 확장에는 열려있어야 하고 변경에는 닫혀있어야 함

## LSP : 리스코프 치환 원칙 (Liskov Substitution Principle)
- 자식 클래스는 언제나 자신의 부모 클래스를 대체할 수 있다는 원칙이다.
- 즉, 인터페이스만 알면 구현체를 몰라도 사용 가능해야 함

## ISP : 인터페이스 분리 원칙 (Interface Segregation Principle)
- 클라이언트에서 사용하지 않는 메서드는 사용해선 안된다. 그러므로 인터페이스를 다시 작게 나누어 만든다.
- 하나의 일반적인 인터페이스보다는 구체적인 여러 개의 인터페이스가 나음
- 파생 클래스 입장에서 사용할 때 100% 구현할 수 있는 인터페이스만 사용해야 한다.
- 두 개 이상의 인터페이스가 필요한 경우 다중 인터페이스 상속으로 구현하는 것이 좋다.

## DIP : 의존성 역전 원칙 (Dependency Inversion Principle)
- 클라이언트는 구체 클래스가 아닌 인터페이스나 추상 클래스에 의존해야 함


---

- [ ] [oop swift](https://www.raywenderlich.com/599-object-oriented-programming-in-swift)


---

#OOP

