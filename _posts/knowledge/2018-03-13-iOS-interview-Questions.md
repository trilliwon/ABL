---
layout: post
title:  "iOS Interview Questions"
date:   2018-03-13 10:00:00 +0900
tag: [Study, Interview]
---

# iOS Interview Questions

### How could you setup Live Rendering ?
> The attribute `@IBDesignable` lets Interface Builder perform live updates on a particular view.

---

### What is the difference between Synchronous & Asynchronous task ?
> *Synchronous*: waits until the task has completed
*Asynchronous*: completes a task in background and can notify you when complete

---

### What Are B-Trees?
> B-trees are search trees that provide an ordered key-value store with excellent performance characteristics. In principle, each node maintains a sorted array of its own elements, and another array for its children.

---

### What is Enum ?
> Enum is a type that basically contains a group of related values in same umbrella.

---

### What is bounding box?
> Bounding box is a term used in geometry; it refers to the smallest measure (area or volume) within which a given set of points.

---

### Why do we use synchronized ?
> synchronized guarantees that only one thread can be executing that code in the block at any given time.

---

### What is the difference `strong`, `weaks`, `read only` and `copy` ?
> `strong`, `weak`, `assign` property attributes define how memory for that property will be managed.

  - *Strong* means that the reference count will be increased and the reference to it will be maintained through the life of the object
  - *Weak*, means that we are pointing to an object but not increasing its reference count. It’s often used when creating a parent child relationship. The parent has a strong reference to the child but the child only has a weak reference to the parent.
  - *Read only*, we can set the property initially but then it can’t be changed.
  - *Copy*, means that we’re copying the value of the object when it’s created. Also prevents its value from changing.

---

### What is Dynamic Dispatch ?
> Dynamic Dispatch is the process of selecting which implementation
of a polymorphic operation that’s a method or a function to call at run time. This means, that when we wanna invoke our methods like object method. but Swift does not default to dynamic dispatch

---

### What’s Code Coverage?
> Code coverage is a metric that helps us to measure the value of our unit tests.

---

### What’s Completion Handler ?
> Completion handlers are super convenient when our app is making an API call, and we need to do something when that task is done, like updating the UI to show the data from the API call. We’ll see completion handlers in Apple’s APIs like dataTaskWithRequest and they can be pretty handy in your own code.

---

### What is Responder Chain ?
> A ResponderChain is a hierarchy of objects that have the opportunity to respond to events received.

---

### What is Regular expressions ?
> Regular expressions are special string patterns that describe how to search through a string.
  - closure, concatenation, ...

---

### What is Operator Overloading ?
> Operator overloading allows us to change how existing operators behave with types that both already exist.

---

### What is Functions ?
> Functions let us group a series of statements together to perform some task. Once a function is created, it can be reused over and over in your code. If you find yourself repeating statements in your code, then a function may be the answer to avoid that repetition.
Pro Tip, Good functions accept input and return output. Bad functions set global variables and rely on other functions to work.

---

### What is API?
>ABIs are important when it comes to applications that use external libraries. If a program is built to use a particular library and that library is later updated, you don’t want to have to re-compile that application (and from the end-user’s standpoint, you may not have the source). If the updated library uses the same ABI, then your program will not need to change.

---

### Why is design pattern very important ?
> Design patterns are reusable solutions to common problems in software design. They’re templates designed to help you write code that’s easy to understand and reuse. Most common Cocoa design patterns:

  - Creational: Singleton.
  - Structural: Decorator, Adapter, Facade.
  - Behavioral: Observer, and, Memento

---

### What is Singleton Pattern ?
> The Singleton design pattern ensures that only one instance exists for a given class and that there’s a global access point to that instance. It usually uses lazy loading to create the single instance when it’s needed the first time.

---

### What is Facade Design Pattern ?  //TODO
> The Facade design pattern provides a single interface to a complex subsystem. Instead of exposing the user to a set of classes and their APIs, you only expose one simple unified API.

---

### What is Decorator Design Pattern ? // TODO
> The Decorator pattern dynamically adds behaviors and responsibilities to an object without modifying its code. It’s an alternative to subclassing where you modify a class’s behavior by wrapping it with another object.

> In Objective-C there are two very common implementations of this pattern: Category and Delegation. In Swift there are also two very common implementations of this pattern: Extensions and Delegation.

---

### What is Adapter Pattern ?
> An Adapter allows classes with incompatible interfaces to work together. It wraps itself around an object and exposes a standard interface to interact with that object.

---

### What is Observer Pattern ?
> In the Observer pattern, one object notifies other objects of any state changes.

> Cocoa implements the observer pattern in two ways: Notifications and Key-Value Observing (KVO).

---

### What is Memento Pattern ?
> In Memento Pattern saves your stuff somewhere. Later on, this externalized state can be restored without violating encapsulation; that is, private data remains private. One of Apple’s specialized implementations of the Memento pattern is Archiving other hand iOS uses the Memento pattern as part of State Restoration.

---

### Explain MVC
  - **Models** — responsible for the domain data or a data access layer which manipulates the data, think of ‘Person’ or ‘PersonDataProvider’ classes.
  - **Views** — responsible for the presentation layer (GUI), for iOS environment think of everything starting with ‘UI’ prefix.
  - **Controller/Presenter/ViewModel** — the glue or the mediator between the Model and the View, in general responsible for altering the Model by reacting to the user’s actions performed on the View and updating the View with changes from the Model.

---

### Explain MVVM
> UIKit independent representation of your View and its state. The View Model invokes changes in the Model and updates itself with the updated Model, and since we have a binding between the View and the View Model, the first is updated accordingly.

> Your view model will actually take in your model, and it can format the information that’s going to be displayed on your view.

> There is a more known framework called RxSwift. It contains RxCocoa, which are reactive extensions for Cocoa and CocoaTouch.

---

### What is JSON/PLIST limits ?
>
- We create your objects and then serialized them to disk..
- It’s great and very limited use cases.
- We can’t obviously use complex queries to filter your results.
- It’s very slow.
- Each time we need something, we need to either serialize or deserialize it.
- it’s not thread-safe.

---

### What is SQLite limits ?
>
- We need to define the relations between the tables. Define the schema of all the tables.
- We have to manually write queries to fetch data.
- We need to query results and then map those to models.
- Queries are very fast.

---

### What is Realm benefits ?
>
- An open-source database framework.
- Implemented from scratch.
- Zero copy object store.
- Fast.

---

### How many are there APIs for battery-efficient location tracking ?
> There are 3 apis.
- Significant location changes — the location is delivered approximately every 500 metres (usually up to 1 km)
- Region monitoring — track enter/exit events from circular regions with a radius equal to 100m or more. Region monitoring is the most precise API after GPS.
- Visit events — monitor place Visit events which are enters/exits from a place (home/office).

---

### What is the Swift main advantage ?
>
To mention some of the main advantages of Swift:
- Optional Types, which make applications crash-resistant
- Built-in error handling
- Closures
- Much faster compared to other languages
- Type-safe language
- Supports pattern matching

---

### Explain generics in Swift ?
> Generics create code that does not get specific about underlying data types. Don’t catch this article.

---

### Explain lazy in Swift ?
> An initial value of the `lazy` stored properties is calculated only when the property is called for the first time. There are situations when the `lazy` properties come very handy to developers.

---

### Explain what is defer ?
> `defer` keyword which provides a block of code that will be executed in the case when execution is leaving the current scope.


---

### How to pass a variable as a reference ?
> We need to mention that there are two types of variables: **reference and value types**.
> The difference between these two types is that by passing value type, the variable will create a copy of its data, and the reference type variable will just point to the original data in the memory.

---

### Why it is better to use higher order functions?
> Functions that take another function as a parameter, or return a function, as a result, are known as higher-order functions. Swift defines these functions as `CollectionType`.

The very basic higher order function is a `filter`.

---

### What is Concurrency?
> Concurrency is dividing up the execution paths of your program so that they are possibly running at the same time. The common terminology: process, thread, multithreading, and others. Terminology;
- **Process**, An instance of an executing app
- **Thread**, Path of execution for code
- **Multithreading**, Multiple threads or multiple paths of execution running at the same time.
- **Concurrency**, Execute multiple tasks at the same time in a scalable manner.
- **Queues**, Queues are lightweight data structures that manage objects in the order of First-in, First-out (FIFO).
- **Synchronous vs Asynchronous** tasks

---

### Grand Central Dispatch (GCD)
> **GCD** is a library that provides a low-level and object-based API to run tasks concurrently while managing threads behind the scenes. Terminology;
- **Dispatch Queues**, A dispatch queue is responsible for executing a task in the first-in, first-out order.
- **Serial Dispatch Queue**, A serial dispatch queue runs tasks one at a time.
- **Concurrent Dispatch Queue**, A concurrent dispatch queue runs as many tasks as it can without waiting for the started tasks to finish.
- **Main Dispatch Queue**, A globally available serial queue that executes tasks on the application’s main thread.

---

### Readers-Writers
> Multiple threads reading at the same time while there should be only one thread writing. The solution to the problem is a readers-writers lock which allows concurrent read-only access and an exclusive write access. Terminology;
- **Race Condition**, A race condition occurs when two or more threads can access shared data and they try to change it at the same time.
- **Deadlock** A deadlock occurs when two or sometimes more tasks wait for the other to finish, and neither ever does.
- **Readers-Writers problem** Multiple threads reading at the same time while there should be only one thread writing.
- **Readers-writer lock** Such a lock allows concurrent read-only access to the shared resource while write operations require exclusive access.
- **Dispatch Barrier Block** Dispatch barrier blocks create a serial-style bottleneck when working with concurrent queues.

---

### KVC — KVO
> **KVC** adds stands for Key-Value Coding. It’s a mechanism by which an object’s properties can be accessed using string’s at runtime rather than having to statically know the property names at development time.
> **KVO** stands for Key-Value Observing and allows a controller or class to observe changes to a property value. In KVO, an object can ask to be notified of any changes to a specific property, whenever that property changes value, the observer is automatically notified.

---

### Please explain Swift’s pattern matching techniques

- **Tuple patterns** are used to match values of corresponding tuple types.
- **Type-casting patterns** allow you to cast or match types.
- **Wildcard patterns** match and ignore any kind and type of value.
- **Optional patterns** are used to match optional values.
- **Enumeration case patterns** match cases of existing enumeration types.
- **Expression patterns** allow you to compare a given value against a given expression.

---

### What are benefits of Guard ?
> There are two big benefits to guard. One is avoiding the pyramid of doom, as others have mentioned — lots of annoying if let statements nested inside each other moving further and further to the right. The other benefit is provide an early exit out of the function using `break` or using `return`.

---

### Please explain Method Swizzling in Swift
> Method Swizzling is a well known practice in Objective-C and in other languages that support dynamic method dispatching.

> Through swizzling, the implementation of a method can be replaced with a different one at runtime, by changing the mapping between a specific #selector(method) and the function that contains its implementation.

> To use method swizzling with your Swift classes there are two requirements that you must comply with:
- The class containing the methods to be swizzled must extend NSObject
- The methods you want to swizzle must have the dynamic attribute

---

### What is the difference Non-Escaping and Escaping Closures ?

> The lifecycle of a non-escaping closure is simple:
1. Pass a closure into a function
2. The function runs the closure (or not)
3. The function returns

> **Escaping closure means**, inside the function, you can still run the closure (or not); the extra bit of the closure is stored some place that will outlive the function. There are several ways to have a closure escape its containing function:
>> **Asynchronous execution**: If you execute the closure asynchronously on a dispatch queue, the queue will hold onto the closure for you. You have no idea when the closure will be executed and there’s no guarantee it will complete before the function returns.
>> Storage: Storing the closure to a global variable, property, or any other bit of storage that lives on past the function call means the closure has also escaped.
>> [link](https://swiftunboxed.com/lang/closures-escaping-noescape-swift3/)

---

### Explain `[weak self] and [unowned self]` ?
> **unowned** does the same as weak with one exception: The variable will not become nil and therefore the variable must not be an optional.

> But when you try to access the variable after its instance has been deallocated. That means, you should only use **unowned** when you are sure, that this variable will never be accessed after the corresponding instance has been deallocated.

> However, if you don’t want the variable to be weak AND you are sure that it can’t be accessed after the corresponding instance has been deallocated, you can use unowned.
> By declaring it **[weak self]** you get to handle the case that it might be nil inside the closure at some point and therefore the variable must be an optional. A case for using **[weak self]** in an asynchronous network request, is in a **view controller** where that request is used to populate the view.

---

###  What is ARC ?
> ARC is a compile time feature that is Apple’s version of automated memory management. It stands for Automatic Reference Counting. This means that it **only** frees up memory for objects when there are **zero strong** references/ to them.

---

###  Explain #keyPath() ?
> Using #keyPath(), a static type check will be performed by virtue of the key-path literal string being used as a StaticString or StringLiteralConvertible. At this point, it’s then checked to ensure that it
A) is actually a thing that exists and
B) is properly exposed to Objective-C.

---

### What is the Test Driven Development of three simple rules ?
Red, Green, Refactor
1. You are not allowed to write any production code unless it is to make a failing unit test pass.
2. You are not allowed to write any more of a unit test than is sufficient to fail; and compilation failures are failures.
3. You are not allowed to write any more production code than is sufficient to pass the one failing unit test.

---

### Please explain final keyword into the class ?
>
By adding the keyword final in front of the method name, we prevent the method from being overridden. If we can replace the final class keyword with a single word static and get the same behavior.


---

### What is the difference open & public access level ?
> **open** allows other modules to use the class and inherit the class; for members, it allows others modules to use the member and override it.

> **public** only allows other modules to use the public classes and the public members. Public classes can no longer be subclassed, nor public members can be overridden.

---

### What is the difference fileprivate, private and public private(set) access level ?

> **fileprivate** is accessible within the current file, private is accessible within the current declaration.

> **public private(set)** means getter is public, but the setter is private.

---

### What is Internal access ?

> Internal access enables entities to be used within any source file from their defining module, but not in any source file outside of the module.

> Internal access is the default level of access. So even though we haven’t been writing any access control specifiers in our code, our code has been at an internal level by default.

---

### What is difference between BDD and TDD ?

> The main difference between BDD and TDD is the fact that BDD test cases can be read by non-engineers, which can be very useful in teams.

> iOS I prefer Quick BDD framework and its “matcher framework,” called Nimble.

---

### What is the benefit writing tests in iOS apps ?

> Writing tests first gives us a clear perspective on the API design, by getting into the mindset of being a client of the API before it exists.
> Good tests serve as great documentation of expected behavior.
> It gives us confidence to constantly refactor our code because we know that if we break anything our tests fail.
> If tests are hard to write its usually a sign architecture could be improved. Following RGR ( Red — Green — Refactor ) helps you make improvements early on.

---

### What is five essential practical guidelines to improve your typographic quality of mobile product designs ?

1. Start by choosing your body text typeface.
2. Try to avoid mixing typefaces.
3. Watch your line length.
4. Balance line height and point size.
5. Use proper Apostrophes and Dashes.

---

### Explain Forced Unwrapping

> When we defined a variable as optional, then to get the value from this variable, we will have to unwrap it. This just means putting an exclamation mark at the end of the variable.

---

###  Explain Swift Standart Library Protocol ?

> There are a few different protocol.
> **Equatable** protocol, that governs how we can distinguish between two instances of the same type. That means we can analyze. If we have a specific value is in our array.
> The **comparable** protocol, to compare two instances of the same type and sequence protocol: prefix(while:) and drop(while:) [SE-0045].

> Swift 4 introduces a new **Codable** protocol that lets us serialize and deserialize custom data types without writing any special code.

---

### What is the difference CollectionViews & TableViews ?

> **TableViews** display a list of items, in a single column, a vertical fashion, and limited to vertical scrolling only.

> **CollectionViews** also display a list of items, however, they can have multiple columns and rows.

---

### What is Alamofire doing ?
> Alamofire uses URL Loading System in the background, so it does integrate well with the Apple-provided mechanisms for all the network development. This means, It provides chainable request/response methods, JSON parameter and response serialization, authentication, and many other features. It has thread mechanics and execute requests on a background thread and call completion blocks on the main thread.

---

### REST, HTTP, JSON — What’s that?

> **HTTP** is the application protocol, or set of rules, web sites use to transfer data from the web server to client. The client (your web browser or app) use to indicate the desired action:

- **GET**: Used to retrieve data, such as a web page, but doesn’t alter any data on the server.
- **HEAD**: Identical to GET but only sends back the headers and none of the actual data.
- **POST**: Used to send data to the server, commonly used when filling a form and clicking submit.
- **PUT**: Used to send data to the specific location provided.
- **DELETE**: Deletes data from the specific location provided.

> **REST**, or REpresentational State Transfer, is a set of rules for designing consistent, easy-to-use and maintainable web APIs.
> **JSON** stands for JavaScript Object Notation; it provides a straightforward, human-readable and portable mechanism for transporting data between two systems. Apple supplies the JSONSerialization class to help convert your objects in memory to JSON and vice-versa.

---

### What problems does delegation solve?
>
- Avoiding tight coupling of objects
- Modifying behavior and appearance without the need to subclass objects
- Allowing tasks to be handed off to any arbitrary object

---

### What is the major purposes of Frameworks?

> Frameworks have three major purposes:

- Code encapsulation
- Code modularity
- Code reuse

> You can share your framework with your other apps, team members, or the iOS community. When combined with Swift’s access control, frameworks help define strong, testable interfaces between code modules.

---

### Explain Swift Package Manager

> The Swift Package Manager will help to vastly improve the Swift ecosystem, making Swift much easier to use and deploy on platforms without Xcode such as Linux. The Swift Package Manager also addresses the problem of dependency hell that can happen when using many interdependent libraries.

> The Swift Package Manager only supports using the master branch. Swift Package Manager now supports packages with Swift, C, C++ and Objective-C.

---

###  What is the difference between a delegate and an NSNotification?

> Delegates and NSNotifications can be used to accomplish nearly the same functionality. However, delegates are one-to-one while NSNotifications are one-to-many.

---

### Why do we use a delegate pattern to be notified of the text field’s events?
> Because at most only a single object needs to know about the event.

---

### How is an inout parameter different from a regular parameter?

> A Inout passes by reference while a regular parameter passes by value.

---

### Explain View Controller Lifecycle events order ?
There are a few different lifecycle event
- loadView
- viewDidLoad
- viewWillAppear
- viewWillLayoutSubviews
- viewDidLayoutSubviews
- viewDidAppear
- viewWillDisappear
- viewDidDisappear

---

### What is the difference between LLVM and Clang?

> Clang is the front end of LLVM tool chain ( “clang” C Language Family Frontend for LLVM ). Every Compiler has three parts .
1. Front end ( lexical analysis, parsing )
2. Optimizer ( Optimizing abstract syntax tree )
3. Back end ( machine code generation )

> Front end ( Clang ) takes the source code and generates abstract syntax tree ( LLVM IR ).

---

### What is Class ?
> A **class** is meant to define an object and how it works. In this way, a class is like a blueprint of an object.

---

### What is Object?

> An **object** is an instance of a class.

---

### What is interface?

> The **@interface** in Objective-C has nothing to do with Java interfaces. It simply declares a public interface of a class, its public API.

---

### When and why do we use an object as opposed to a struct?

> Structs are value types. Classes(Objects) are reference types.

---

###  What is UIStackView?
> UIStackView provides a way to layout a series of views horizontally or vertically. We can define how the contained views adjust themselves to the available space.
> [link](https://www.raywenderlich.com/160646/uistackview-tutorial-introducing-stack-views-2)

---

### What are the states of an iOS App?
1. **Non-running** — The app is not running.
2. **Inactive** —  The app is running in the foreground, but not receiving events. An iOS app can be placed into an inactive state, for example, when a call or SMS message is received.
3. **Active** — The app is running in the foreground, and receiving events.
4. **Background** — The app is running in the background, and executing code.
5. **Suspended** — The app is in the background, but no code is being executed.

---

### What does code signing do?
> Signing our app allows iOS to identify who signed our app and to verify that our app hasn’t been modified since you signed it. The **Signing Identity** consists of a **public-private key pair** that Apple creates for us.

---

### What is the difference between property and instance variable?

> A property is a more abstract concept. An instance variable is literally just a storage slot, like a slot in a struct. Normally other objects are never supposed to access them directly. Usually a property will return or set an instance variable, but it could use data from several or none at all.

---

### Explain difference between SDK and Framework ?

> SDK is a set of software development tools. This set is used for creation of applications. Framework is basically a platform which is used for developing software applications. It provides the necessary foundation on which the programs can be developed for a specific platform. SDK and Framework complement each other, and SDKs are available for frameworks.

---

### What is Downcasting ?
> When we’re casting an object to another type in Objective-C, it’s pretty simple since there’s only one way to do it. In Swift, though, there are two ways to cast — one that’s safe and one that’s not .

- as used for upcasting and type casting to bridged type
- as? used for safe casting, return nil if failed
- as! used to force casting, crash if failed. should only be used when we know the downcast will succeed.

---

### Why is everything in a do-catch block?

> In Swift, errors are thrown and handled inside of do-catch blocks.

---

### What is Nil Coalescing & Ternary Operator ?
> It is an easily return an unwrapped optional, or a default value. If we do not have value, we can set zero or default value.

---

###  What kind of JSONSerialization have ReadingOptions ?

- **mutableContainers** Specifies that arrays and dictionaries are created as variables objects, not constants.
- **mutableLeaves** Specifies that leaf strings in the JSON object graph are created as instances of variable String.
- **allowFragments** Specifies that the parser should allow top-level objects that are not an instance of Array or Dictionary.

---

### Explain subscripts ?

> Classes, structures, and enumerations can define subscripts, which are shortcuts for accessing the member elements of a collection, list, or sequence.

---

### What is DispatchGroup ?

> **DispatchGroup** allows for aggregate synchronization of work. We can use them to submit multiple different work items and track when they all complete, even though they might run on different queues. This behavior can be helpful when progress can’t be made until all of the specified tasks are complete. — Apple’s Documentation

> The most basic answer: If we need to wait on a couple of asynchronous or synchronous operations before proceeding, we can use **DispatchGroup**.

---


### Where do we use Dependency Injection ?

> We use a storyboard or xib in our iOS app, then we created IBOutlets. IBOutlet is a property related to a view. These are injected into the view controller when it is instantiated, which is essentially a form of Dependency Injection.

> There are forms of dependency injection: constructor injection, property injection and method injection.

---

### Please explain types of notifications.
> There are two type of notifications: Remote and Local. Remote notification requires connection to a server. Local notifications don’t require server connection. Local notifications happen on device.

---

### What kind of order functions can we use on collection types ?
>
- `map(_:):` Returns an array of results after transforming each element in the sequence using the provided closure.
- `filter(_:):` Returns an array of elements that satisfy the provided closure predicate.
- `reduce(_:_:):` Returns a single value by combining each element in the sequence using the provided closure.
- `sorted(by:):` Returns an array of the elements in the sequence sorted based on the provided closure predicate.

[Sequence docs](http://swiftdoc.org/v3.0/protocol/Sequence/).

---

### What is the difference ANY and ANYOBJECT ?

> According to Apple’s Swift documentation:
- **Any** can represent an instance of any type at all, including function types and optional types.
- **AnyObject** can represent an instance of any class type.

---

### What is CoreData ?

> Core data is an object graph manager which also has the ability to persist object graphs to the persistent store on a disk. An object graph is like a map of all the different model objects in a typical model view controller iOS application. CoreData has also integration with Core Spotlight.

---

### Could you explain Associatedtype ?
> If you want to create Generic Protocol we can use associatedtype.
> [link](https://krakendev.io/blog/generic-protocols-and-their-shortcomings)

---

###  What is Hashable ?

> Hashable allows us to use our objects as keys in a dictionary. So we can make our custom types.

---

###  When do you use optional chaining vs. if let or guard ?

> We use optional chaining when we do not really care if the operation fails; otherwise, we use `if let` or `guard`. Optional chaining lets us run code only if our optional has a value.
> Optional chaining is a process for querying and calling properties, methods, and subscripts on an optional that might currently be nil. If the optional contains a value, the property, method, or subscript call succeeds; if the optional is nil, the property, method, or subscript call returns nil. Multiple queries can be chained together, and the entire chain fails gracefully if any link in the chain is nil.

---

### How many different ways to pass data in Swift ?

> There are many different ways such as Delegate, KVO, Segue, and NSNotification, Target-Action, Callbacks.

---

### What’s the difference optional between `nil` and `.None`?

> There is no difference. `Optional.None` (`.None` for short) is the correct way of initializing an optional variable lacking a value, whereas `nil` is just syntactic sugar for .None.


---

### Explain Common features of Protocols & superclasses
>
- implementation reuse
- provide points for customization
- interface reuse
- supporting modular design via dynamic dispatch on reused interfaces

---

### Explain Linked List

> Linked List basically consist of the structures we named the Node. These nodes basically have two things. The first one is the one we want to keep. (we do not have to hold single data, we can keep as much information as we want), and the other is the address information of the other node.

> **Disadvantages** of Linked Lists, at the beginning, there is extra space usage. Because the Linked List have an address information in addition to the existing information. This means more space usage.

---

### Explain AutoLayout

> AutoLayout provides a flexible and powerful layout system that describes how views and the UI controls calculates the size and position in the hierarchy.

---

### What is Pointer ?

> A pointer is a direct reference to a memory address. Whereas a variable acts as a transparent container for a value, pointers remove a layer of abstraction and let you see how that value is stored.

---

### What is Keychain ?
> Keychain is an API for persisting data securly in iOS App.

---

### Explain the difference between atomic and nonatomic synthesized properties

> **atomic** : It is the default behaviour. If an object is declared as atomic then it becomes thread-safe. Thread-safe means, at a time only one thread of a particular instance of that class can have the control over that object.

> **nonatomic**: It is not thread-safe. We can use the nonatomic property attribute to specify that synthesized accessors simply set or return a value directly, with no guarantees about what happens if that same value is accessed simultaneously from different threads. For this reason, it’s faster to access a nonatomic property than an atomic one.

---

### Explain throw

> We are telling the compiler that it can throw errors by using the throws keyword. Before we can throw an error, we need to make a list of all the possible errors you want to throw.

---

###  What is Instruments?

> Instrument is a powerful performance tuning tool to analyze that performance, memory footprint, smooth animation, energy usage, leaks and file/network activity.

---

### What is Optional Binding ?

> We are going to take optional value and we are going to bind it non optional constant. We used If let structure or Guard statement.


---

### What is Protocol?
> A protocol defines a blueprint of methods, properties and other requirements that suit a particular task or piece of functionality. The protocol can then be adopted by a class, structure, or enumeration to provide an actual implementation of those requirements.

---

### Explain Sequence in Swift
> Sequence is a basic type in Swift for defining an aggregation of elements that distribute sequentially in a row. All collection types inherit from Sequence such as Array, Set, Dictionary.

---

### What’s the difference between a xib and a storyboard?

> Both are used in Xcode to layout screens (view controllers). A xib defines a single View or View Controller screen, while a storyboard shows many view controllers and also shows the relationship between them.
