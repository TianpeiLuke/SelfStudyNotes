---
tags:
  - concept
  - software_engineering/design_pattern
keywords: 
topics: 
name: "Design Pattern: Abstract Factory Pattern"
date of note: 2024-04-27
---

## Concept Definition

>[!important]
>**Name**: Abstract Factory Pattern
>
>**Also Known as**:  *Kit* 
>
>**Intent**:
>- Provide an **interface** for **creating families** of *related or dependent objects* **without specifying** their concrete classes.


### Structure

![[abstract_factory.png]]

- **`AbstractFactory`**:
	- Declares an interface for operations that *create **`AbstractProduct` objects***.
- **`ConcreteFactory`**:
	- Implements the operations to *create **`ConcreteProduct` objects***.
- **`AbstractProduct`**:
	- Declare an interface for a type of product object.
- **`ConcreteProduct`**:
	- defines a product object to be created by the corresponding `ConcreteFactory`.
	- implements the `AbstractProduct` interface.
- `Client`:
	- uses only interfaces declared by `AbstractFactory` and `AbstractProduct` classes.



### Applicability

Use the Abstract Factory pattern when:

- a system should be **independent** of *how* its products are *created, composed, and represented*.
- a system should be *configured* with one of **multiple families of products**.
- a family of *related product objects* is designed to be used **together**, and you need to enforce this constraint.
- you want to provide **a class library** of products, and you want to **reveal just their interfaces**, not their implementations.


## Explanation



-- pp 87, ABSTRACT FACTORY, 


## Benefits

The Abstract Factory pattern has the following benefits:

- **It isolates concrete classes**. 
	- The Abstract Factory pattern helps you control the classes of objects that an application creates.
	- Because a factory *encapsulates the responsibility* and *the process of creating product objects*, it isolates clients from implementation classes. 
	- Clients manipulate instances through their *abstract interfaces*. 
	- Product class names are isolated in the implementation of the concrete factory; they do *not appear in client code*.
- **It makes exchanging product families easy**. 
	- The class of a concrete factory appears only once in an application—that is, where it's *instantiated*. 
	- This makes it easy to change the concrete factory an application uses. It can use different *product configurations* simply by changing the concrete factory. 
	- Because an abstract factory creates a complete family of products, *the whole product family changes at once*. 
	- In our user interface example, we can switch from Motif widgets to Presentation Manager widgets simply by switching the corresponding factory objects and recreating the interface.
- **It promotes consistency among products**. 
	- When product objects *in a family* are *designed to work together*, it's important that an application use objects from *only one family at a time*. `AbstractFactory` makes this easy to enforce.


## Drawbacks

The Abstract Factory pattern has the following liabilities:

- **Supporting new kinds of products is difficult**. 
	- Extending abstract factories to produce new kinds of Products *isn't easy*. That's because the `AbstractFactory` interface *fixes the set of products* that can be created. 
	- Supporting new kinds of products requires *extending the factory interface*, which involves changing the `AbstractFactory` class and all of its subclasses. 




-----------
##  Recommended Notes and References

- Abstract Factory implements using Factory Method
	- [[Design Pattern Factory Method Pattern]]

- Youtube
	- [8 Design Patterns EVERY Developer Should Know](https://www.youtube.com/watch?v=tAuRQs_d9F8&ab_channel=NeetCode)
	- [10 Design Patterns Explained in 10 Minutes](https://www.youtube.com/watch?v=tv-_1er1mWI&ab_channel=Fireship)
	- [Abstract Factory Pattern – Design Patterns (ep 5)](https://www.youtube.com/watch?v=v-GiuMmsXj4&list=PLrhzvIcii6GNjpARdnO4ueTUAVR9eMBpc&index=5&ab_channel=ChristopherOkhravi)
	- [Design Patterns in Plain English | Mosh Hamedani](https://www.youtube.com/watch?v=NU_1StN5Tkk&ab_channel=ProgrammingwithMosh)