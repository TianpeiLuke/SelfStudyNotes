---
tags:
  - code
  - code_snippet
  - algorithm/backtracking
  - leetcode/algorithm
  - c_plus
keywords: 
topics:
  - leetcode
  - recursion
  - depth-first-search
language: c++
date of note: 2024-03-23
---

## Code Snippet Summary

>[!todo] Problem Statement
>The **_n_-queens puzzle** is the problem of placing _n_ queens on an _n_×_n_ chessboard such that no two queens attack each other.
>![[n-queen.png]]
>
>- Given an integer _n_, return all distinct solutions to the _n_-queens puzzle.
>- Each solution contains a distinct board configuration of the _n_-queens' placement, where *'Q' *and *'.'* both indicate a queen and an empty space respectively.

>[!example]
>There exist two distinct solutions to the 4-queens puzzle:
> ```
> [  
> [".Q..",  // Solution 1
>  "...Q",
>  "Q...",
>  "..Q."],
> 
> ["..Q.",  // Solution 2
>   "Q...",
>   "...Q",
>   ".Q.."]
> ]
> ```


## Code

>[!important] Highlight
>- This is a classical **Back-Tracking problem**. We apply **depth-first-search (DFS)** to retrieve all solutions in **recursion**.
>- Note that by queen move, *each row and column can only have one queen.*
>- Thus each row can *at most have one queen*. so the recursion used row number as index.
>- Define the recursion function `NQueenSolver` with three inputs 
>	- `pos` for all candidate positions for queens in current chess board, indexed by row number: `pos[row] = col` represents one queue placed at `(row, col)`, 
>	- `row` for the current row, 
>	- `res` is the solution set which contains all completed solutions; 



```c++
class Solution {
public:
	vector<vector<string>> solveNQueens(int n) {
		vector<vector<string>> res;
		if(n ==0) return res;
		vector<int> pos(n, -1); //store the column pos for each row of queen
		NQueensSolver(pos, 0, res);
		return res;
	}
	
	void NQueensSolver(vector<int>& pos, int row, vector<vector<string>>& res){
		int n = pos.size();
		if(row == n){
			//if is a solution
			vector<string> one_solution(n, string(n,'.'));
			for(int i=0; i< n; i++){
				one_solution[i][pos[i]] = 'Q';
			}
			res.push_back(one_solution);
		} else {//loop over all candidates columns
			for(int col=0; col<n; col++){
			
				if(isvalid(pos, row, col)){
					pos[row] = col;//make move
					
					NQueensSolver(pos, row+1, res); //recursion, indexed by row
					
					pos[row] = -1; //unmake move
				}
			}
		}
	}
	
	bool isvalid(vector<int> pos, int row, int col){
		// check if queen at position (row, col) can be attacked based on existing positions pos
		int n = pos.size();
		bool res = true;
		
		for(int i=0; i< row; i++){
			if(pos[i] == col || abs(row - i) == abs(pos[i] - col)){
				res = false;
				return res;
			}
		}
		return res;
	}
};
```




-----------
##  Recommended Notes


- [[Backtracking]]
- [[Depth-First Search]]

- [[Constraint Satisfaction Problem CSP]]