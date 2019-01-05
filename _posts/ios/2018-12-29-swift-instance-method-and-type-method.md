---
layout: post
title: "Instance Method vs Type method"
date: 2018-12-30 11:30:00 +0800
tag: [Swift]
---

- `Instance methods` are functions that belong to instances of a particular class, structure, or enumeration.

- `type methods` You can also define methods that are called on the type itself. These kinds of methods are called type methods. You indicate type methods by writing the static keyword before the method’s func keyword. Classes may also use the class keyword to allow subclasses to override the superclass’s implementation of that method.

---

`static` `class` : type property

- static, class method 는 타입 메서드, class 메서드는 오버라이딩 가능

- `Instance methods` are called on an individual instance of one unique/chosen type.
- `Type methods` are called on the actual type, in and of itself.

- Swift 에서는 클래스나 struct 를 타입으로 생각한다.