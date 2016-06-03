---
layout: post
title:  "Dynamic Programming"
date:   2015-02-10 15:14:54
categories: algorithm
---
    
## A good algorithm design paradigm 
 
+ correctness: get all the answer of the whole problem;  
+ efficiency: avoid re-computation.  


## Key ingredients   

1. identify a small number of sub-problems;   
2. can quickly and correctly solve "larger problems" given the solutions of "smaller subproblems";   
3. After solving all subproblems, can quickly compute the final solution.   

## Difference: DP and Divide and Conquer?   

1. dynamic programming solve small sub-problems, which may lead to re-compute the same sub-problem if we do not cache the answers;   
2. divide and conquer just solve unique sub-problems and combine the answers.   






---

## Examples



### leetcode 32 Longest Valid Parentheses

#### Problem description: 

Given a string `s`, containing '(' or ')', find the length of longest valid well-formed parentheses substring.

Input	|Output
------- |  ---------
(()	| 2
)()())	| 4

#### Solution: O(N)

> Check if the `i`th element is `end` of a valid substring, if yes find the length. 

Properties for an `end` elemenet `cj`:

* not the first element
* equals to `)`
* can find privous `ci` equals `(` to match
* substring between `ci` and `cj` is valid
	
If `cj` satisfies all the privous properties, `s[i~j]` is at least a valid substring. And also, if there is a valid substring `s[x~i-1]` left to `s[i~j]`, so that `s[x~j]` is the longest substring ended by `cj`.

Below is the Pseudo code for check and compute for `cj`: 
	
	check_if_end(j):
		if c[j] == '('
			dp[j] = 0
		else
			int i = j - dp[j-1] - 1;
			if i < 0 or c[i]==')'
				dp[j] = 0
			else
				dp[j] = (j-i+1) + dp[i-1];
				
	//edge case: i or i-1 is left out of boundary


Edge case:

* the '(' index i will match, p, is left out of boundary

Pseudo code for the whole problem

	solution():
		res = 0
		for each j in s.length
			len = check_if_end(j)
			res =  max(res, len)
		return res





---

### leetcode 53 Maximum Subarray

#### Problem description
Find the contiguous subarray within an array(containing at least one number) which has the largest sum.

#### Input
[-2,1,-3,4,-1,2,1,-5,4]

#### Output
6

#### hint
the subarray with the largest sum is [4,-1,2,1]

#### Solution: 



### leetcode 62 Unique Paths




{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}