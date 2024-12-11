---
tags:
  - concept
  - information_retrieval/index
  - information_retrieval/search
  - algorithm/search
  - algorithm/tree_based_search
  - algorithm/tree
keywords:
  - ball_tree_search
topics:
  - information_retrieval/search
  - algorithmt/tree_based_search
name: Ball Tree Structure for Approximate Nearest Neighbor Search
date of note: 2024-11-29
---

## Concept Definition

>[!important]
>**Name**: Ball Tree Structure for Approximate Nearest Neighbor Search

![[Approximate Nearest Neighbor Search#^fb4fa7]]

- [[Approximate Nearest Neighbor Search]]

>[!important] Definition


- [[Binary Search Tree Data Structure]]

- [[k-d Tree Structure for ANN Search]]


![[ball_tree_search.png]]





### Approximate Nearest Neighbor Search in k-d Tree



### Insert Operation



### FindMin Operation




### Deletion Operation


#### General Idea



#### Case: No Right Subtree



## Explanation

>[!important]
>The search complexity is the equivalent to the **height** of the search tree
>- In the **worst-case** the tree would essentally be a linked list and the height would be $$O(n).$$
>- In the **best case** it would be *well-balanced* and the height would be $$O(\log n)$$



-----------
##  Recommended Notes and References


- [[Similarity Search]]
- [[Binary Tree Order and Traversal]]
- [[Information Retrieval]]

- [[Introduction to Algorithms by Cormen]]
- [[Algorithm Design Manual by Skiena]] pp 460 - 463, 638 - 647


- Notes
	- [UMD course note on SG-KD-Tree](https://www.cs.umd.edu/class/fall2019/cmsc420-0201/Handouts/sg-kd-tree.pdf)
	- [UMD Matth kd-trees](https://www.math.umd.edu/~immortal/CMSC420/notes/kdtrees.pdf)
	- [CMU Course note kdtrees](https://www.cs.cmu.edu/~ckingsf/bioinfo-lectures/kdtrees.pdf)
- Wikipedia [K-d_tree](https://en.wikipedia.org/wiki/K-d_tree)
- Youtube 
	- [KD-Tree Nearest Neighbor Data Structure](https://www.youtube.com/watch?v=Glp7THUpGow)
- Medium
	- [Ball tree and KD Tree Algorithms](https://medium.com/@geethasreemattaparthi/ball-tree-and-kd-tree-algorithms-a03cdc9f0af9)