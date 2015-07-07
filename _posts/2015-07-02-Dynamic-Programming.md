---
layout: post
title:  "Dynamic Programming"
date:   2015-02-10 15:14:54
categories: jekyll Algorithms
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

##Example1: Longest Commen Sequence
input: sdfs


{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}