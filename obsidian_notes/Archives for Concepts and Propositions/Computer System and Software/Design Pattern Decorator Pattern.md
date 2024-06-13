---
tags:
  - concept
  - software_engineering/design_pattern
keywords: 
topics: 
name: "Design Pattern: Decorator Pattern"
date of note: 2024-04-27
---

## Concept Definition

>[!important]
>**Name**: Decorator Pattern
>
>**Also Known as**:  *Wrapper* 
>
>**Intent**: 
>- **Attach** *additional responsibilities* to an object **dynamically**. 
>- Decorator s provide a flexible alternative to *subclassing* for extending functionality.



### Structure

![[decorator_0.png]]

- **`Component`**:
	- defines the interface for objects that can have responsibilities added to them dynamically.
- `ConcreteComponent` 
	- inheritance from `Component`
	- Defines an object to which additional responsibilities can be attached.
- **`Decorator`**: 
	- `Component` is a part of `Decorator` (***Aggregation*** relationship)
	- maintains a **reference** to a `Component` object and defines an **interface** that *conforms to `Component`'s interface*
- **`ConcreteDecorator`**
	- inheritance from `Decorator`
	- adds responsibilities to the `Component`.

### Applicability

Use Decorator 

- to *add responsibilities* to individual objects **dynamically** and **transparently**, that is, *without affecting other objects*.
- for *responsibilities* that can be **withdrawn**.
- when *extension* by *subclassing* is **impractical**. Sometimes a large number of independent extensions are possible and would produce an explosion of subclasses to support every combination. Or a class definition may be hidden or otherwise unavailable for subclassing.


## Explanation

>[!quote]
>Sometimes we want to add responsibilities to individual objects , not to an entire class.
>
>One way to add responsibilities is with *inheritance*. ...
>
>A more flexible approach is to *enclose the component* in another object .. The enclosing object is called a **decorator**. The decorator conforms to the *interface* of the component it decorates so that its presence is transparent to the component's client. The decorator forwards requests to the component and may *perform additional actions* *before or after forwarding*. **Transparency** lets you *nest* decorators *recursively*, thereby allowing an *unlimited number of added responsibilities*.
>
>-- *pp 175, DECORATOR, Design Patterns: Element of Reusable Object-Oriented Software*

## Benefits

- The Decorator pattern has at least two key benefits:
	- **More flexibility than static inheritance**: 
		- The Decorator pattern provides a more flexible way to *add responsibilities* to objects than can be had with *static (multiple) inheritance*. 
		- With decorators, responsibilities can be *added and removed at run-time* simply by *attaching and detaching* them. 
		- In contrast, inheritance requires creating *a new class for each additional responsibility*. This gives rise to many classes and *increases the complexity* of a system. 
		- Furthermore, providing different Decorator classes for a specific `Component` class lets you mix and match responsibilities.
		- Decorator also make it easy to add a property *twice*. Inheriting from a base class twice is error-prone at best.  
	- **Avoid feature-laden classes high up in the hierarchy**: 
		- Decorator offers a **pay-as-you-go approach** to *adding responsibilities*. Instead of trying to *support all foreseeable features* in a complex, customizable class, you can define a simple class and add functionality incrementally with Decorator objects. 
		- *Functionality can be composed from simple pieces*. As a result, an application needn't pay for features it doesn't use. 
		- It's also easy to *define new kinds of Decorators independently* from the classes of objects they extend, even for unforeseen extensions. 
		- Extending a complex class tends to expose details unrelated to the responsibilities you're adding.



## Drawbacks

- The Decorator pattern has at least two liabilities:
	- **A decorator and its component are not identical**: 
		- A decorator acts as a **transparent enclosure.** 
		- But from an object identity point of view, *a decorated component is not identical to the component itself*. 
		- Hence you shouldn't rely on *object identity* when you use decorators.
	- **Lots of little objects**: 
		- A design that uses Decorator often results in systems composed of *lots of little objects that all look alike*. 
		- The objects differ only in the way they are interconnected, not in their class or in the value of their variables. 
		- Although these systems are easy to customize by those who understand them, they can be *hard to learn and debug*.


-----------
##  Recommended Notes and References

- Youtube
	- [5 Design Patterns That Are ACTUALLY Used By Developers](https://www.youtube.com/watch?v=YMAwgRwjEOQ&ab_channel=AlexHyett)
	- [10 Design Patterns Explained in 10 Minutes](https://www.youtube.com/watch?v=tv-_1er1mWI&ab_channel=Fireship)
	- [Decorator Pattern – Design Patterns (ep 3)](https://www.youtube.com/watch?v=GCraGHx6gso&list=PLrhzvIcii6GNjpARdnO4ueTUAVR9eMBpc&index=3&ab_channel=ChristopherOkhravi)
	- [Design Patterns in Plain English | Mosh Hamedani](https://www.youtube.com/watch?v=NU_1StN5Tkk&ab_channel=ProgrammingwithMosh)
