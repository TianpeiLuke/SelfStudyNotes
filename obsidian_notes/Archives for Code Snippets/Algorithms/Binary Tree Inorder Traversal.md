---
tags:
  - code
  - code_snippet
  - algorithm/binary_tree
  - leetcode/algorithm
  - c_plus
keywords: 
topics:
  - leetcode
  - binary_tree
language: c++
date of note: 2024-03-22
---

## Code Snippet Summary

- Given a binary tree, print out the output according to *in-order-traversal*
- **In-Order-Traversal**: first visit root, then left-subtree and then right-subtree.  Within each subtree, recursively following the same ordering.
	- root -> left-subtree -> right-subtree


## Code

>[!important] Highlight
>- This implementation use **Stack** data structure (**Last-In-First-Out array**)
>- **Stack** is by default used in compiler if choose to implement it by recursively calling the same functions


```c++

vector<int> inorderTraversal(TreeNode* root) {

	vector<int> result;
	vector<TreeNode*> array;
	TreeNode* cur;
	cur = root;
	
	while(!array.empty() || cur != NULL ){
		if(cur){
			array.push_back(cur);
			// since this is in-order so after root, visit left-subtree
			cur = cur->left;
		}else if (array.size()!=0){
			cur = array.back();
			array.pop_back();
			result.push_back(cur->val);
			// track the root of the immediate right-subtree in stack in order to jump to right subtree when the left-subtree is traversed.
			cur = cur->right;
		}
	}
	
return result;
}
```




-----------
##  Recommended Notes

