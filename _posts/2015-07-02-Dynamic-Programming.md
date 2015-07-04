--
layout: post
title: Dynamic Programming
description: This article introduce Dynamic Programming, a useful programming design paradigm.
keywords: Algorithm
---
# Dynamic Programming

标签（空格分隔）： Java Algorithm

---
##Dynamic Programming: A good algorithm design paradigm  
+ correctness: get all the answer of the whole problem;  
+ efficiency: avoid re-computation.  


##Key ingredients of Dynamic Programming:   
1. identify a small number of sub-problems;   
2. can quickly and correctly solve "larger problems" given the solutions of "smaller subproblems";   
3. After solving all subproblems, can quickly compute the final solution.   

##What is the difference between Dynamic Programming and Divide and Conquer?   
1. dynamic programming solve small sub-problems, which may lead to re-compute the same sub-problem if we do not cache the answers;   
2. divide and conquer just solve unique sub-problems and combine the answers.   

##Example: Longest Commen Sequence




{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}