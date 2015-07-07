---
layout: post
title: Analysis of Algorithms
description: This article introduce analysis of algorithms.
keywords: Algorithm
---

Suppose we have two algorithms, algoA and algoB, which can be used to solve a same problem with certain input data.   
How can we compare the efficiency of these two algorithms? 
    
##naive idea: running time   
implement both the algorithms and run the two grograms on your computer for different inputs and see which one takes less time.

##Here comes the problem:   
+ Running on same computer: algoA performs better for data1, while algoB performs better for data2;  
+ Running the same input: algoA performs better on pc1, while algoB performs better on pc2.   


##Asymptotic Analysis:   
+ Time of a program scales with the input data.  
+ How does the time(or space) taken by an algorithm increases with the input size.  
+ As the input gets bigger, how much longer will the program take?Just a litte bit? A lot longer?  


##Worst Case, Average Case and Best Case:  
+ **Worst Case**: upper bound on running time of an algorithm:  
causes maximun number of operations to be executed.  
+ **Average Case**: expected running time of an algorithm:  
we take all inputs and calculate computing time for all of the inputs. Sum all the calculated values and divide the sum by total number of inputs. 
We must know(or predict) distribution of cases.  
+ **Best Case**: lower bound on running time of an algorithm:  
We must know the case that causes minimun number of operations to be executed.  
***Most of the times, we do worst case analysis to analyze algorithms.***

**Note:**  
For some algorithms, all the cases are asymptotic same, i.e., there are no worst and best cases. For example, Merge Sort.


##Asymptotic notation  
1. **Θ Notation**: bounds a function from above and below.  
 Θ((g(n)) = {f(n): there exist positive constants c1, c2 and n0 such that
                   0 <= c1*g(n) <= f(n) <= c2*g(n) for all n >= n0}   
                   
2. **Big O Notation**: defines an upper bound of an algorithm.  
 O(g(n)) = { f(n): there exist positive constants c and n0 such that 
                   0 <= f(n) <= cg(n) for all n >= n0}    
3. **Ω Notation**: provides an asymptotic lower bound.    
 Ω (g(n)) = {f(n): there exist positive constants c and n0 such that 
                   0 <= cg(n) <= f(n) for all n >= n0}.  
   
  
  
##Analysis of loops  
1. **O(1)**  
 if it doesn’t contain loop, recursion and call to any other non-constant time function;  
 A loop or recursion that runs a constant number of times is also considered as O(1). For example the following loop is O(1).  
>for (int i = 1; i <= c; i++) {}  
2. **O(n)**  
if the loop variables is incremented / decremented by a constant amount.  
>for (int i = 1; i <= n; i += c) {}  
3. **O(n^c)**  
Time complexity of nested loops is equal to the number of times the innermost statement is executed.  
>for (int i = 1; i <=n; i += c) {  
>for (int j = 1; j <=n; j += c) {  
>           // some O(1) expressions  
>        }  
>    }      
4. **O(Logn)**  
if the loop variables is divided / multiplied by a constant amount.  
>for (int i = 1; i <=n; i *= c) {}   
5. **O(LogLogn)**   
if the loop variables is reduced / increased exponentially by a constant amount.  
>for (int i = 2; i <=n; i = pow(i, c)) { }    
  
**Note:**  
**combine time complexities of consecutive loops**  
   calculate the sum of time complexities of individual loops.  
**calculate time complexity when there are many if, else statements inside loops**  
   worst case.  
**calculate time complexity of recursive functions**  
   we must know how to solve recurrences.    
  
   
##Solving Recurrences  
**Problem:** Given the time complexity of an algorithm as the form T(n) = 2T(n/2) + cn, try to solve the recurrence.   
   
There are mainly **3 ways** for solving recurrences.  
  
1. **Substitution Method**  
 We make a guess for the solution and then we use mathematical induction to prove the the guess is correct or incorrect.  
  
2. **Recurrence Tree Method**  
In this method, we draw a recurrence tree and calculate the time taken by every level of tree. 
Finally, we sum the work done at all levels. 
To draw the recurrence tree, we start from the given recurrence and keep drawing till we find a pattern among levels. 
The pattern is typically a arithmetic or geometric series.  
  
3. **Master Method**  
Master Method is a direct way to get the solution. 
The master method works only for following type of recurrences or for recurrences that can be transformed to following type.  
`T(n) = aT(n/b) + f(n) where a >= 1 and b > 1`  
There are following three cases:    
1) If f(n) = Θ(nc) where c < Log(b)a then T(n) = Θ(n^Log(b)a)  
2) If f(n) = Θ(nc) where c = Log(b)a then T(n) = Θ(n^c * Logn)  
3) If f(n) = Θ(nc) where c > Log(b)a then T(n) = Θ(f(n))  


##Amortized Analysis  

##What does 'Space Complexity' mean  

##NP-Completeness Introduction  

##A Time Complexity Question  

##Time  Complexity of building a heap  

   
{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}