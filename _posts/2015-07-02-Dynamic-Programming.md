---
layout: post
title:  "Dynamic Programming"
date:   2015-02-10 15:14:54
categories: algorithm
---
    
# Dynamic Programming: A good algorithm design paradigm  
+ correctness: get all the answer of the whole problem;  
+ efficiency: avoid re-computation.  


#Key ingredients of Dynamic Programming:   
1. identify a small number of sub-problems;   
2. can quickly and correctly solve "larger problems" given the solutions of "smaller subproblems";   
3. After solving all subproblems, can quickly compute the final solution.   

#What is the difference between Dynamic Programming and Divide and Conquer?   
1. dynamic programming solve small sub-problems, which may lead to re-compute the same sub-problem if we do not cache the answers;   
2. divide and conquer just solve unique sub-problems and combine the answers.   

---
#Example1: Longest Commen Sequence



---
##leetcode 32 Longest Valid Parentheses

###Problem description: 
Given a string containing '(' or ')', find the length of longest valid well-formed parentheses substring.
###input
(()
###output
2
###input
)()())
###output
4
###Solution: O(N)
For each of the characters in the string, c[i], we use dp[i] to represent length the longest well-formed parentheses ended by c[i]. Properties:

* '(' cannot be end of a valid parentheses;
* dp[i] should be a even number;
* If dp[i] equals 0, there is no valid substring ended by c[i].


Suppose we know answers for dp[0-i-1], we want to compute the answer for c[i]:
	
	if c[i] == '('
		dp[i] = 0
	else
		int p = i - dp[i-1] - 1;
		if p < 0 or c[p]==')'
			dp[i] = 0
		else
			dp[i] = (i-p+1) + dp[p-1];
To answer is the largest number in dp.

to compute the dp array, we can scan through the 


---

##leetcode 53 Maximum Subarray

###Problem description
Find the contiguous subarray within an array(containing at least one number) which has the largest sum.
###Input
[-2,1,-3,4,-1,2,1,-5,4]
###Output
6
###hint
the subarray with the largest sum is [4,-1,2,1]
###Solution: 



##leetcode 62 Unique Paths




{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}