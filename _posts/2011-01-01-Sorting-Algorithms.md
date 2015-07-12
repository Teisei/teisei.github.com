---
layout: post
title: "Sorting Algorithms"
date: 2011-01-01 18:43:00
categories: algorithm sorting
---  

* content
{:toc}


## Selection Sort  

### Basic idea

### Analysis

### C code

	#include <iostream>
    #include <cstdio>
    #include <cstring>
    
    using namespace std;
    
    
    void print_the_array(int a[], int len){
    	for(int i=0;i<len;i++)
    		printf("%2d, ",a[i]);
    	printf("\n");
    }
    
    void swap(int *a, int *b){
    	int t = *a;
    	*a=*b;
    	*b=t;
    }
    
    int find_max(int a[], int l, int r){
    	int max = -1, max_inx = -1;
    	for(int i=l;i<=r;i++){
    		if(a[i]>max){
    			max = a[i];
    			max_inx = i;
    		}
    	}
    	return max_inx;
    }
    
    void selection_sort(int a[], int l, int r){
    	for(int i=r;i>l;i--){
    		int p = find_max(a,l,i);
    		swap(&a[p], &a[i]);	
    	}
    }
    
    int main(){
    	int a[] = {12, 11, 13, 5, 6, 7, 1, 34, 4, 19, 24243, 88};
    	int len = sizeof(a)/sizeof(a[0]);
    	print_the_array(a, len);
    
    	selection_sort(a, 0, len-1);
    	print_the_array(a, len);
    
    	return 0;
    }

---

## Bubble Sort  

---

## Insertion Sort  

---

## Merge Sort  

### Basic idea   

#### Given a array of length n, we do not try to sort it.
* **Divide**:  Divide it into two sub-array a[left,...,median], a[median+1,...,right];
* **Conquer**: Recursively solve each of the two sub-problems;
* **Combine**: Since Two sub-problems are sorted, we combine the two sub-solutions.

#### How to combine?
* **1** Given two sorted sub-array, we want to combine them into a whole sorted array.
* **2** We create a new array with length of the sum of the two sub-arrays for the combined results;
* **3** Each time we pick the smaller(bigger) one between the head of two sub-array, and add it to the new array from head to tail;
* **4** We repeat doing **step3** until there is no element left to pick in one of the two sub-arrays. 
* **5** We add the left elements in the original sub-array into the new array. And we get the whole sorted array.

### Analysis
* T(n) = 2T(n/2) + n
* O(n Log n)

### C code

	#include <iostream>
    #include <cstdio>
    #include <cstring>
    #include <cstdlib>
    
    using namespace std;
    
    void print_the_array(int a[], int len){
    	for(int i=0;i<len;i++)
    		printf("%2d ",a[i]);
    	printf("\n");
    }
    
    void swap(int *a, int *b){
    	int t=*a;
    	*a=*b;
    	*b=t;
    }
    
    int find_median(int l, int r){
    	return (l+r)/2;
    }
    
    void combine(int a[], int l1, int r1, int l2, int r2){
    	int b[r1-l1+r2-l2+4];
    	int inx1 = l1, inx2 = l2, inx0 = 0;
    	while(inx1<=r1&&inx2<=r2)
    		if(a[inx1]<=a[inx2])
    			b[inx0++]=a[inx1++];
    		else
    			b[inx0++]=a[inx2++];
    	while(inx1<=r1) b[inx0++]=a[inx1++];
    	while(inx2<=r2) b[inx0++]=a[inx2++];
    	for(int i=0;i<inx0;i++)
    		a[i+l1] = b[i];
    }
    
    void conquer(int a[], int l, int r){
    	if(l == r) return;
    	else{
    		/**  divide and conquer */
    		int median = find_median(l, r);
    		conquer(a, l, median);
    		conquer(a, median+1,r);
    		/**  combine the results */
    		combine(a, l, median, median+1, r);
    	}
    }
    
    
    
    void merge_sort(int a[], int l, int r){
    	conquer(a, l, r);
    }
    
    int main(){
    	// int a[] = {12, 11, 13, 5, 6, 7};
    	int a[] = {12, 11, 13, 5, 6, 7, 1, 34, 4, 19, 24243, 88};
    	// int a[] = {12, 11, 13};
    	int len = sizeof(a)/sizeof(a[0]);	
    	print_the_array(a, len);
    
    	merge_sort(a, 0, len-1);
    	print_the_array(a, len);
    	return 0;
    }



---

## Heap Sort  
Heap sort is a comparison based sorting technique based on Binary Heap data structure. 
It is similar to selection sort where we first find the maximum element and place the maximum element at the end. 
We repeat the same process for remaining element.

#### What is a binary heap
* a binary heap is a complete binary tree, in which every level except possibly the last, be completely filled.
* A Binary Heap is a Complete Binary Tree where items are stored in a special order such that value in a parent node is greater(or smaller) than the values in its two children nodes. 
The former is called as max heap and the latter is called min heap. 
The heap can be represented by binary tree or array.
* We can easily extract maximun or minimun element of the heap by using binary heap data structure.

#### Heap sort for increasing order
* Build a max heap from the input data (array);
* At this point, the max element is at the root of heap. 
We replace the root with the last element of heap;
* reduce the size of heap by 1;
* Re-heapify the root of heap;
* repeat the above steps until there is only one element left in heap (size 1). 

#### How to build a binary heap
Heapify procedure can be applied to a node only if its children nodes are heapified. So the heapification must be performed in the bottom up order.

### Analysis
O(n Log n)

### C code

	#include <iostream>
    #include <cstdio>
    #include <cstring>
    
    using namespace std;
    
    int getLeft(int p){	return p*2+1;}
    int getRight(int p){	return 2*p+2;}
    int getParent(int c){	return (c-1)/2;}
    
    bool compare(int a, int b, bool increase){
    	return increase?a>b:a<b;
    }
    
    /**  heapify parent node if and only if two children are heapifies. */
    void heapify(int a[], int p, int len, bool incre){
    	int l = getLeft(p);//left child
    	int r = getRight(p);
    	//if the parent itself is in the bottom level
    	if(l>len-1) return;
    	//if the parent has only left child
    	else if(r>len-1){
    		if(!compare(a[p], a[l], incre)){
    			int tmp = a[l];a[l]=a[p];a[p]=tmp;
    			heapify(a, l, len, incre);
    		}
    	}
    	else{
    		if(compare(a[p], a[l], incre)&& compare(a[p], a[r], incre)){
    		}else if(compare(a[l], a[r], incre)){
    			int tmp=a[l];a[l]=a[p];a[p]=tmp;
    			heapify(a, l, len, incre);
    		}else{
    			int tmp=a[r];a[r]=a[p];a[p]=tmp;
    			heapify(a, r, len, incre);
    		}
    	}
    }
    
    
    /**  O(n) */
    void make_heap(int a[], int len, bool incre){
    	printf("\n*** make heap ***\n");
    	//bottom up order
    	int last_inx = getParent(len-1);
    	for(int i=last_inx;i>=0;i--){
    		heapify(a, i, len, incre);
    	}
    }
    
    /**  O(n Log n) */
    void heap_sort(int a[], int len, bool incre){
    	printf("\n*** heap sort ***\n");
    	make_heap(a, len, incre);
    	while(len>0){
    		int top = a[0];a[0]=a[len-1];a[len-1]=top;
    		len--;
    		heapify(a, 0, len, incre);
    	}
    }
    
    /**  Auxiliary functions */
    int find_depth(int a[], int p, int len, int depth){
    	if(getLeft(p)>len-1) return depth;
    	else return find_depth(a, getLeft(p), len, depth+1);
    }
    int find_total_depth(int a[], int len){
    	int parent = 0;
    	if(getLeft(parent)>len-1) return 0;
    	else return find_depth(a, getLeft(parent), len, 1);
    }
    
    void print_heap(int a[], int len){
    	printf("\n*** print the heap ***\n");
    	int depth = find_total_depth(a, len);
    	int parent = 0;
    	for(int i=0;i<=depth;i++){
    		for(int j=parent;j<getLeft(parent)&&j<len;j++){
    			printf("(%2d) ", a[j]);
    		}
    		printf("\n");
    		parent = getLeft(parent);
    	}
    }
    
    int main(){
    	// int a[] = {12, 11, 13, 5, 6, 7};
    	int a[] = {12, 11, 13, 5, 6, 7, 1, 34, 4, 19};
    	// int a[] = {12, 11, 13};
    	int n = sizeof(a)/sizeof(a[0]);
    	printf("length of a is %d\n", n);
    	bool incre = true;// max heap, sort the array in an increasing order
    
    	printf("number = %d   depth = %d\n", n ,find_total_depth(a, n));
    	print_heap(a, n);
    
    
    	heap_sort(a, n, incre);
    	for(int i=0;i<n;i++){
    		printf("%d ", a[i]);
    	}
    	printf("\n");
    	return 0;
    }


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

#### Worst case:  
Every time we divide the whole problem with length n, into one sub-problem with length n-1, and another sub-problem with length 1;

#### Best case:  
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








{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}