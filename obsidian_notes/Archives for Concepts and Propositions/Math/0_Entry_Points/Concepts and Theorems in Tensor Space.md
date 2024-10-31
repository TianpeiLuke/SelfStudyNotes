---
tags:
  - entry_point
  - concept
  - math/differential_geometry
  - math/linear_algebra
keywords: 
topics:
  - linear_algebra
  - differential_geometry
name: 
date of note: 2024-05-06
---
## Background

>[!info]
>The concept of **tensor** generalize two concepts:
>- It generalize a **vector** in vector space
>- It generalize a **linear function** in function space
>  
>Instead of focusing on one object at a time, the concept of **tensor** provides a **perspective** of **parallelism** in our analysis. 
>- Instead of one *vector* in one *vector space*, we **simultaneously** study **multiple vectors** in **multiple vector spaces**.
>- Instead of one *linear function* in one *function space*, we **simultaneously** study **multiple linear functions** in **multiple function spaces**.

>[!info]
>In tensor algebra, we study *the entire system's behavior* by analyzing its *parallel components*. In particular, we are interested in **the output of the overall system** as *compared to* **the output of individual parallel components.**
>- **symmetric**: means that the system output is invariant to the ordering swap of inputs
>- **alternating / antisymmetric**: means that the system output would switch sign as the ordering of inputs swaps
>- **tensor product** merge the output of all of parallel objects into one via element-wise direct product. 
>- **wedge product** apply additional alternating weights for each term of tensor product.
>- **interior product** overwrite the output of one parallel component with a fixed function. 
>- **trace operation** consumes one component's output with another component's output before passing to the output of system. This way, it simultaneously cancelled two components' output from the system.
>- **exterior derivative** create a new parallel component by detaching the output weight component from the tensor product, taking derivation of component function and treat it as an additional independent component, before merging all components in system output.


>[!info]
>When apply the system of tensor on manifold, we acknowledge that *the individual component's behavior would vary at each operation point*, but we are still interested in how the overall system output is manipulated based on the output of each component.  

##  List of Concepts

### Background on Vector Fields, Vector Bundle

- [[Concepts and Theorems of Vector Field Covector Field and Bundle]]

### Tensor and Tensor Product

- [[Multilinear Function]]
- [[Tensor Product]]
- [[Abstract Tensor Product]]

- [[Contravariant Tensor on Vector Space]]
- [[Covariant Tensor on Vector Space]]
- [[Mixed Tensor on Vector Space]]
- [[Coordinate Representation of Tensor]]

- [[Invariant under Change of Variable]]


### Tensor Bundle and Tensor Field

- [[Vector Bundle of Covariant k-Tensor]]
- [[Vector Bundle of Contravariant k-Tensor]]
- [[Vector Bundle of Mixed Tensor of Type]]

- [[Tensor Field on Manifold]]
- [[Space of all Smooth Tensor Fields on a Manifold]]
- [[Coordinate Representation of Tensor Field]]
- [[Pullback of Tensor Fields]]
- [[Coordinate Representation of Pullback of Tensor Field]]
- [[Change of Coordinates between Tensor Fields]]

### Symmetric Tensor

- [[Symmetric Tensor]]
- [[Projection of Tensor on Symmetric Tensor Space]]
- [[Symmetric Product]]
- [[Symmetric Tensor Field on Manifold]]


### Symmetric Tensor Field

- [[Riemannian Metric and Riemannian Manifold]]


### Alternating Tensor

- [[Alternating Tensor]]
- [[Exterior Forms]]
	- [[Determinant of Linear Transformation]]
	- [[Elementary Alternating Tensor]]
- [[Projection of Tensor on Alternating Tensor Space]]
- [[Wedge Product]]
- [[Grassmann Algebra]]
- [[Interior Multiplication]]
- [[Coordinate Representation of Interior Multiplication]]


### Differential Forms (Alternating Tensor Field)

- [[Vector Bundle of all Exterior Forms on Manifold]]
- [[Differential k-Form on Manifold]]
- [[Space of all Smooth k-Forms on a Manifold]]
- [[Coordinate Representation of k-Forms]]
- [[Coordinate Representation of Pullback of k-Forms]]
- [[Change of Coordinates for Differential k-Forms]]
- [[Trace of Mixed Tensor]]

### Exterior Derivative of Differential Form

- [[Exterior Derivatives of Differential Form]]

### Integration on Manifold

- [[Orientation for Vector Space]]
- [[Orientation of Manifolds]]
- [[Differential k-Form as Infinitesimal Volume]]
- [[Hodge Star Operator on Riemannian Manifold]]

### Stokes Theorem

- [[Stokes Theorem]]

## Explanation





-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]



- [[Introduction to Smooth Manifolds by Lee]]