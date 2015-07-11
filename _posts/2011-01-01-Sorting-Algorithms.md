---
layout: post
title: "Sorting Algorithms"
date: 2011-01-01 18:43:00
categories: algorithm sorting
---  

* content
{:toc}


## Selection Sort  

---

## Bubble Sort  

---

## Insertion Sort  

---

## Merge Sort  

---

## Heap Sort  

---

## QuickSort  

### A 'divide and conquer' algorithm
* Divide:
  + Given a int array, we pick an element as pivot;
  + put elements smaller than pivot left to pivot,
  + put elements bigger than pivot right to pivot;
  + return the position of the pivot;
* Conquer:
  + Recursively do the same thing on the left part and right part;
* Combine:
  + We do not have the sub-solutions, because the array is already sorted.

### Analysis of quick-sort algorithm:  

### Worst case:  
Every time we divide the whole problem with length n, into one sub-problem with length n-1, and another sub-problem with length 1;

### Best case:  
Every time the pivot we pick luckily divide the whole problem into two relatively equal length.

### C code:  

    /*
    	4 ways to pick pivot:
    	1)always pick the left most element;
    	2)always pick the right most element;
    	3)pick a random element as the pivot;
    	4)pu=ick the median element.
    */
    
    #include <iostream>
    #include <cstdio>
    #include <cstring>
    #include <cstdlib>
    
    using namespace std;
    
    bool compare(int a, int b, bool increase){
    	return increase?a>=b:a<=b;
    }
    
    void print_the_array(int a[], int len){
    	for(int i=0;i<len;i++)
    		printf("%2d ",a[i]);
    	printf("\n");
    }
    
    void swap(int *a, int *b){
    	int t = *a;
    	*a = *b;
    	*b = t;
    }
    
    /**  choose pivot element randomly */
    int partition(int a[], int l, int r, bool incre){
    	
    	int random = rand() % (r - l + 1) + l;
    	swap(&a[random], &a[r]);
    	
    	int pivot = r;
    	int pivot_value = a[pivot];
    	
    	int cursor = l;
    	
    	for(int i=l;i<r;i++){
    		if(compare(a[i], pivot_value, incre)){
    			swap(&a[cursor++], &a[i]);
    		}
    	}
    	swap(&a[pivot], &a[cursor]);
    	return cursor;
    }
    
    /**  O(n Log n) */
    void quicksort(int a[], int left, int right, bool incre){
    	int pivot;
    	if(left<right){
    		pivot = partition(a, left, right, incre);
    		quicksort(a,left,pivot-1,incre);
    		quicksort(a,pivot+1,right,incre);
    	}
    }
    
    int main(){
    	// int a[] = {12, 11, 13, 5, 6, 7};
    	int a[] = {12, 11, 13, 5, 6, 7, 1, 34, 4, 19, 24243, 88};
    	// int a[] = {12, 11, 13};
    
    	int len = sizeof(a)/sizeof(a[0]);	
    	bool incre = false;// max heap, sort the array in an increasing order
    
    	print_the_array(a, len);
    	quicksort(a, 0, len-1, incre);
    	print_the_array(a, len);
    
    	return 0;
    }
---

## BUcket Sort  

---

## ShellSort  

---

## Stability in sorting algorithms  

---

## Lower bound for comparison based sorting algorithms  

---







# 这是 H1   
## This is H2   
### This is H3

>## 这是一个标题

* Red
* Green
* blue

- 红色
- 绿色
- 蓝色

+ Red
+ Green
+ Blue

1. Bird
2. Cat
3. Dog

这是一个普通段落：
    这是一个代码区块。
    
这是一个普通段落:
    这是一个代码区块.
    
***
* * *
*****
* * * * *
- - -
--------------------

This is [an example](http://teisei.github.io "Title")inline link.

[This link](http://teisei.github.io) has no title attribute.

See my [About](/about/) page for details.

This is [an example][id] reference-style link.

THis is [an example] [id] reference-style link.

[id]: http://example.com/ "optional title here"

[Google][]

[Google]: http://www.google.com

Visit [Daring Fireball][]  for more information.


强调：  
*single asterisks*

_single underscores_

**double asterisks**

__double underscores__


代码：  
Use the `print()` function  

<p>Use the <code>print()</code></p>

如果要在代码中插入反引号
``There is a literal backtick (`) here.``

A single backtick in a code span. `` ` ``

A backtick-delimited string in a code span. `` `foo` ``



图片：   
1  
![Alt text](images/work/i-pizn.jpg)     
2  
![Alt text](images/work/Campus_App.png "Optional title")   
3   
![Alt text][id]    
4    
[i-pizn.jgp]: images/work/i-pizn.jpg   "optional attribute"




{% highlight bash lineno %}
public class C{
    public static void main(String args[]){
        System.out.println("Hello World!");
    }
}
{% endhighlight %}



{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}