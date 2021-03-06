---
layout: post
tldr: false
audio: false
title: "Divide and Conquer"
date: 2011-1-01 18:43:00
categories: algorithm
---

## Divide-and-Conquer
It is a program design Paradigm.
It is a recursive algorithm. 
We do not know how to slove the big problem that is size of n, then we try to slove the subproblems in the size of n/2. If we can slove the sub-problem size of n/2, then we can combine these two sub-problems to the answer of the whole problem.


### MergeSort is a algorithm for sorting.
> **Input**:  *a[1...n]* (un-sorted)  
> **Output**: *a[1...n]* (sorted)

### three steps
* **Step one**: Divide the array into two parts: a[1...n/2],a[n/2+1,n].
* **Step two**: Sort both the left and the right part sub-array and return the sorted sub-array; if the sub-array size of 1(length is 1), return it directly.
* **Step three**: Combine the two sorted sub-array. Now we have two sorted sub-arrays, we want to merge these two sub-arrays and make a new big array.

### Analysis
* Best case == Average case = O(n Log n)
* take a O(n) size auxiliary space

### Java Code

    public class MergeSort<T extends Comparable<? super T>> {
        /**
         * Merge Sort algorithm.
         */
        public void mergeSort(T[] a) {
            T[] tmpArray = (T[]) new Comparable[a.length];
            mergeSort(a, tmpArray, 0, a.length - 1);
        }
    
        /**
         * Internal method that makes recursive calls. *
         */
        private void mergeSort(T[] a,
                               T[] tmpArray, int left, int right) {
            if (left < right) {
                int center = (left + right) / 2;
    
                mergeSort(a, tmpArray, left, center);
                mergeSort(a, tmpArray, center + 1, right);
                merge(a, tmpArray, left, center + 1, right);
            }
        }
    
        /**
         * Internal method that merges two sorted halves of a subarray.*
         */
        private void merge(T[] a,
                           T[] tmpArray, int leftPos, int rightPos, int rightEnd) {
            int leftEnd = rightPos - 1;
            int tmpPos = leftPos;
            int numElements = rightEnd - leftPos + 1;
    
            // Main loop
            while (leftPos <= leftEnd && rightPos <= rightEnd) {
                if (a[leftPos].compareTo(a[rightPos]) <= 0) {
                    tmpArray[tmpPos++] = a[leftPos++];
                } else {
                    tmpArray[tmpPos++] = a[rightPos++];
                }
            }
    
            // Copy rest of left half
            while (leftPos <= leftEnd) {
                tmpArray[tmpPos++] = a[leftPos++];
            }
    
            // Copy rest of right half
            while (rightPos <= rightEnd) {
                tmpArray[tmpPos++] = a[rightPos++];
            }
    
            // Copy tmpArray back
            for (int i = 0; i < numElements; i++, --rightEnd) {
                a[rightEnd] = tmpArray[rightEnd];
            }
        }
    }