---
tags:
  - concept
  - software_engineering/design_pattern
keywords: 
topics: 
name: "Design Pattern: Strategy Pattern"
date of note: 2024-04-27
---

## Concept Definition

>[!important]
>**Name**: Strategy Pattern
>
>**Also Known as**:  *Policy*
>
>**Intent**: 
>- Define **a family of algorithms**, *encapsulate* each one, and make them **interchangeable**. 
>- Strategy lets the algorithm **vary independently from clients** that use it.

### Structure

![[strategy.png]]

- **`Strategy`**:
	- declares an **interface common to all supported algorithms**. Context uses this interface to call the algorithm defined by `ConcreteStrategy`
- **`ConcreteStrategy`**:
	- *implements* the algorithm using the `Strategy` interface
- **`Content`**:
	- is configured with a `ConcreteStrategy` object. 
	- maintains a *reference* to a `Strategy` object. (***Aggregation*** relationship)
	- may define an interface that *lets `Strategy` access its data*.

### Applicability

Use the Strategy pattern when:

- many related classes **differ only in their behavior**. Strategies provide a way to **configure a class with one of many behaviors**.
- you need **different variants** of an algorithm. For example, you might define algorithms reflecting different space/time trade-offs. Strategies can be used when *these variants are implemented* as *a class hierarchy of algorithms*.
- an algorithm uses **data** that clients **shouldn't know about**. Use the Strategy pattern to **avoid exposing** *complex, algorithm-specific data structures*.
- a class **defines many behaviors**, and these appear as *multiple conditional statements* in its operations. Instead of many conditionals, move related conditional *branches into their own Strategy class*.


## Explanation

>[!quote]
>Many algorithms exist for **breaking a stream of text into lines**. Hard-wiring all such algorithms into the classes that require them isn't desirable for several reasons:
> - Clients that need linebreaking get *more complex* if they *include the linebreaking code*. That makes clients **bigger and harder to maintain**, especially if they support **multiple linebreaking algorithms**.
> - Different algorithms will be **appropriate at different times**. We *don't want to support multiple* linebreaking algorithms if we *don't use them all*.
> - It's **difficult to add new algorithms** and vary existing ones when linebreaking is an integral part of a client. 
>   
> We can avoid these problems by defining classes that **encapsulate** *different linebreaking algorithms*. *An algorithm that's encapsulated in this way* is called a **strategy**.
> 
> -- pp 315, STRATEGY, 

## Benefits

- The Strategy pattern has the following **benefits**:
	- **Families of related algorithms**: Hierarchies of Strategy classes define a family of algorithms or behaviors for contexts to reuse. Inheritance can help factor out common functionality of the algorithms.
	- **An alternative to subclassing**: 
		- *Inheritance* offers another way to support a variety of algorithms or behaviors. You can subclass a `Context` class directly to give it different behaviors. 
			- But this *hard-wires the behavior into `Context`*. 
			- It *mixes the algorithm implementation* with `Context`'s, making `Context` harder to *understand, maintain, and extend*. 
			- And you can't *vary the algorithm dynamically*. You wind up with many related classes whose only difference is the algorithm or behavior they employ. 
		- Encapsulating the algorithm in *separate* `Strategy` classes lets you *vary the algorithm independently of its context*, making it easier to switch, understand, and extend.
	- **Strategy eliminate conditional statements**: 
		- The Strategy pattern offers an alternative to *conditional statements* for selecting desired behavior. 
			- When different behaviors are lumped into one class, it's hard to avoid using conditional statements to select the right behavior. 
		- Encapsulating the behavior in separate Strategy classes eliminates these conditional statements.
	- **A choice of implementations**:
		- Strategies can provide *different implementations of the same behavior*. 
		- The client can *choose* among strategies with *different time and space trade-offs*.

## Drawbacks

- The Strategy pattern has the following **drawbacks**:
	- **Clients must be aware of different Strategies**: 
		- The pattern has a potential drawback in that *a client must understand how Strategies differ* before it can select the appropriate one. 
		- Clients might be *exposed to implementation issues*. 
		- Therefore you should use the Strategy pattern **only when the variation in behavior is relevant to clients**.
	- **Communication overhead between `Strategy` and `Context`**: 
		- The Strategy interface is *shared* by all `ConcreteStrategy` classes whether the algorithms they implement are trivial or complex. 
		- Hence it's likely that some `ConcreteStrategies` *won't use all the information passed* to them through this interface; simple `ConcreteStrategies` *may use none of it*! 
		- That means there will be times when the context creates and initializes parameters that *never get used*. 
		- If this is an issue, then you'll need **tighter coupling** between `Strategy` and `Context`.
	- **Increased number of objects**:
		- Strategies *increase the number of objects* in an application. 
		- Sometimes you can reduce this overhead by implementing strategies as **stateless objects** that contexts can share. 
			- Any **residual state** is maintained by the context, which passes it in each request to the Strategy.
			- *Shared* strategies should not maintain *state across invocation*.


-----------
##  Recommended Notes and References

- Youtube
	- [5 Design Patterns That Are ACTUALLY Used By Developers](https://www.youtube.com/watch?v=YMAwgRwjEOQ&ab_channel=AlexHyett)
	- [8 Design Patterns EVERY Developer Should Know](https://www.youtube.com/watch?v=tAuRQs_d9F8&ab_channel=NeetCode)
	- [10 Design Patterns Explained in 10 Minutes](https://www.youtube.com/watch?v=tv-_1er1mWI&ab_channel=Fireship)
	- [Strategy Pattern – Design Patterns (ep 1)](https://www.youtube.com/watch?v=v9ejT8FO-7I&list=PLrhzvIcii6GNjpARdnO4ueTUAVR9eMBpc&ab_channel=ChristopherOkhravi)
	- [The Strategy Pattern: Write BETTER PYTHON CODE Part 3](https://www.youtube.com/watch?v=WQ8bNdxREHU&t=259s&ab_channel=ArjanCodes)
	- [Design Patterns in Plain English | Mosh Hamedani](https://www.youtube.com/watch?v=NU_1StN5Tkk&ab_channel=ProgrammingwithMosh)