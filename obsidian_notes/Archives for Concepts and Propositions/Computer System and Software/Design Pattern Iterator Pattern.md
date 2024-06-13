---
tags:
  - concept
  - software_engineering/design_pattern
keywords: 
topics: 
name: "Design Pattern: Iterator Pattern"
date of note: 2024-04-27
---

## Concept Definition

>[!important]
>**Name**: Iterator Pattern
>
>**Also Known As**: *Cursor*
>
>**Intent**:
>- Provide a way to **access the elements** of an aggregate object sequentially *without exposing its underlying representation*.

### Structure

![[iterator.png]]

- **`Iterator`**:
	- defines an *interface* for *accessing and traversing* elements.
- **`ConcreteIterator`**:
	- *implements* the `Iterator` interface.
	- keeps track of *the current position* in the traversal of the aggregate.
- `Aggregate`:
	- Define an *interface* for *creating an Iterator object*.
- `ConcreteAggregate`:
	- inherits from `Aggregate`
	- `ConcreteAggregate` cannot exist without `ConcreteIterator` (i.e. ***Composition*** relationship)
	- `ConcreteAggregate` create `ConcreteIterator`
	- implements *the `Iterator` creation interface* to return an instance of the proper `ConcreteIterator`

### Applicability

Use the Iterator pattern 

- to **access** an aggregate object's contents **without exposing its internal representation**. 
- to **support multiple traversals** of aggregate objects.
- to provide a **uniform interface** for *traversing different aggregate structures* (that is, to support polymorphic iteration).

## Explanation

>[!quote]
>An aggregate object such as a list should give you a way to **access its elements without exposing its internal structure**. Moreover, you might want to **traverse the list in different ways**, depending on what you want to accomplish. But you probably don't want to bloat the List interface with operations for different traversals, even if you could anticipate the ones you will need. You might also need to have more than one traversal pending on the same list. 
>
>**The Iterator pattern** lets you do all this. The key idea in this pattern is to **take the responsibility for access and traversal out of the list object** and put it into an **iterator object**. The Iterator class defines **an interface** *for accessing the list's elements*. An iterator object is responsible for keeping track of the current element; that is, it knows which elements have been traversed already.
>
>-- *pp 257, ITERATOR, Design Patterns: Element of Reusable Object-Oriented Software*

## Benefits

- The Iterator pattern has three important consequences:
	- **It supports variations in the traversal of an aggregate.** 
		- Complex aggregates may be traversed in many ways. 
			- For example, code generation and semantic checking involve traversing parse trees. 
			- Code generation may traverse the parse tree in order or preorder. 
			- Iterators make it easy to change the traversal algorithm: Just replace the iterator instance with a different one. 
		- You can also define Iterator subclasses to support new traversals.
	- **Iterators simplify the Aggregate interface.** 
		- Iterator's traversal interface obviates the need for a similar interface in Aggregate, thereby *simplifying the aggregate's interface*.
	- **More than one traversal can be pending on an aggregate.** 
		- An iterator keeps track of its own traversal state. Therefore you can have *more than one traversal* in progress at once.





-----------
##  Recommended Notes and References

- Youtube
	- [8 Design Patterns EVERY Developer Should Know](https://www.youtube.com/watch?v=tAuRQs_d9F8&ab_channel=NeetCode)
	- [10 Design Patterns Explained in 10 Minutes](https://www.youtube.com/watch?v=tv-_1er1mWI&ab_channel=Fireship)
	- [Iterator Pattern – Design Patterns (ep 16)](https://www.youtube.com/watch?v=uNTNEfwYXhI&list=PLrhzvIcii6GNjpARdnO4ueTUAVR9eMBpc&index=16&ab_channel=ChristopherOkhravi)
	- [Design Patterns in Plain English | Mosh Hamedani](https://www.youtube.com/watch?v=NU_1StN5Tkk&ab_channel=ProgrammingwithMosh)