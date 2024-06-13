---
tags:
  - concept
  - software_engineering/design_pattern
keywords: 
topics: 
name: "Design Pattern: Builder Pattern"
date of note: 2024-04-27
---

## Concept Definition

>[!important]
>**Name**: Builder Pattern
>
>**Intent**:
>- **Separate** the **construction** of a *complex object* **from its representation** so that the *same* construction process can create *different representations*.

### Structure

![[builder.png]]

- **`Builder`**:
	- specifies an abstract interface for *creating parts* of a `Product` object
- **`ConcreteBuilder`**:
	- *constructs* and *assembles parts* of the product by implementing the Builder interface.
	- *defines* and keeps track of the *representation* it creates
	- provides an interface for *retrieving* the product. 
- **`Director`**:
	- `Builder` is a part of `Director`
	- *constructs* an object using the Builder interface.
- `Product`:
	- represents the complex object under construction.
	- `ConcreteBuilder` builds product's internal representation and defines the process by which it's assembled
	- includes classes that *define the constituent parts*, including interfaces for assembling the parts into the final result.


### Applicability

Use the Builder pattern when:

- The algorithm for **creating a complex object** should be **independent** of the **parts** that make up the object and **how** they're **assembled**.
- The **construction process** must allow **different representations** for the object that's constructed.

## Explanation


-- pp 97, BUILDER,  


## Consequences

Here are key consequences of the Builder pattern:

- **It lets you vary a product's internal representation.** 
	- The `Builder` object provides the `Director` with an *abstract interface* for constructing the product. 
	- The interface lets the builder *hide the representation* and *internal structure* of the `Product`. 
	- It also *hides* how the product gets assembled. 
	- Because the product is constructed through an abstract interface, all you have to do to change the product's internal representation is define a new kind of builder.
- **It isolates code for construction and representation.** 
	- The `Builder` pattern improves **modularity** by *encapsulating* the way a complex object *is constructed and represented*. 
	- Clients needn't know anything about the classes that define the product's internal structure; such classes don't appear in Builder's interface. 
	- Each `ConcreteBuilder` contains all the code to create and assemble a particular kind of product. 
	- The code is *written once*; then different `Director`s can *reuse* it to build `Product` variants from the same set of parts.
- **It gives you finer control over the construction process.** 
	- Unlike **creational patterns** that construct products *in one shot*, the **Builder pattern** constructs the product step by step *under the director's control*. 
	- Only when the product is finished does the director retrieve it from the builder. 
	- Hence the `Builder` interface reflects *the process of constructing* the product more than other creational patterns. 
	- This gives you **finer control** over *the construction process* and consequently *the internal structure* of the resulting product.
  



-----------
##  Recommended Notes and References

- Youtube
	- [8 Design Patterns EVERY Developer Should Know](https://www.youtube.com/watch?v=tAuRQs_d9F8&ab_channel=NeetCode)
	- [10 Design Patterns Explained in 10 Minutes](https://www.youtube.com/watch?v=tv-_1er1mWI&ab_channel=Fireship)
	- [Design Patterns in Plain English | Mosh Hamedani](https://www.youtube.com/watch?v=NU_1StN5Tkk&ab_channel=ProgrammingwithMosh)