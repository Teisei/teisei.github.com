---
layout: post
location: Shanghai, China
tldr: false
audio: false
title: Programming Interview Questions
categories: algorithm interview
---

### Reference

[programming-interview-questions][ln1]
	
[ln1]:http://www.ardendertat.com/2012/01/09/programming-interview-questions/

<br>
<br>
<br>


### Problems

---

<br>

##### 1. Array Pair Sum

Given an integer array, output all pairs that sum up to a specific value k.

---

##### 2. Matrix Region Sum

Given a matrix of integers and coordinates of a rectangular region within the matrix, find the sum of numbers falling inside the rectangle. Our program will be called multiple times with different rectangular regions from the same matrix.

---

##### 3. Largest Continuous Sum

Given an array of integers (positive and negative) find the largest continuous sum.

---

##### 4. Find Missing Element

There is an array of non-negative integers. A second array is formed by shuffling the elements of the first array and deleting a random element. Given these two arrays, find which element is missing in the second array.

---

##### 5. Linked List Remove Nodes

Given a linkedlist of integers and an integer value, delete every node of the linkedlist containing that value.

---

##### 6. Combine Two Strings

We are given 3 strings: str1, str2, and str3. Str3 is said to be a shuffle of str1 and str2 if it can be formed by interleaving the characters of str1 and str2 in a way that maintains the left to right ordering of the characters from each string. For example, given str1=”abc” and str2=”def”, str3=”dabecf” is a valid shuffle since it preserves the character ordering of the two strings. So, given these 3 strings write a function that detects whether str3 is a valid shuffle of str1 and str2.

---

##### 7. Binary Search Tree Check

Given a binary tree, check whether it’s a binary search tree or not.

---

##### 8. Transform Word

Given a source word, target word and an English dictionary, transform the source word to target by changing/adding/removing 1 character at a time, while all intermediate words being valid English words. Return the transformation chain which has the smallest number of intermediate words.

---

##### 9. Convert Array

Given an array [a1, a2, …, aN, b1, b2, …, bN, c1, c2, …, cN]  convert it to [a1, b1, c1, a2, b2, c2, …, aN, bN, cN] in-place using constant extra space

---

##### 10. Kth Largest Element in Array

Given an array of integers find the kth element in the sorted order (not the kth distinct element). So, if the array is [3, 1, 2, 1, 4] and k is 3 then the result is 2, because it’s the 3rd element in sorted order (but the 3rd distinct element is 3).

---

##### 11. All Permutations of String

Generate all permutations of a given string.

---

##### 12. Reverse Words in a String

Given an input string, reverse all the words. To clarify, input: “Interviews are awesome!” output: “awesome! are Interviews”. Consider all consecutive non-whitespace characters as individual words. If there are multiple spaces between words reduce them to a single white space. Also remove all leading and trailing whitespaces. So, the output for ”   CS degree”, “CS    degree”, “CS degree   “, or ”   CS   degree   ” are all the same: “degree CS”.

---

##### 13. Median of Integer Stream

Given a stream of unsorted integers, find the median element in sorted order at any given time. So, we will be receiving a continuous stream of numbers in some random order and we don’t know the stream length in advance. Write a function that finds the median of the already received numbers efficiently at any time. We will be asked to find the median multiple times. Just to recall, median is the middle element in an odd length sorted array, and in the even case it’s the average of the middle elements.

---

##### 14. Check Balanced Parentheses

Given a string of opening and closing parentheses, check whether it’s balanced. We have 3 types of parentheses: round brackets: (), square brackets: [], and curly brackets: {}. Assume that the string doesn’t contain any other character than these, no spaces words or numbers. Just to remind, balanced parentheses require every opening parenthesis to be closed in the reverse order opened. For example ‘([])’ is balanced but ‘([)]‘ is not.

---
 
##### 15. First Non Repeated Character in String

Find the first non-repeated (unique) character in a given string.

---

##### 16. Anagram Strings

Given two strings, check if they’re anagrams or not. Two strings are anagrams if they are written using the same exact letters, ignoring space, punctuation and capitalization. Each letter should have the same count in both strings. For example, ‘Eleven plus two’ and ‘Twelve plus one’ are meaningful anagrams of each other.

---

##### 17. Search Unknown Length Array

Given a sorted array of unknown length and a number to search for, return the index of the number in the array. Accessing an element out of bounds throws exception. If the number occurs multiple times, return the index of any occurrence. If it isn’t present, return -1.

---

##### 18. Find Even Occurring Element

Given an integer array, one element occurs even number of times and all others have odd occurrences. Find the element with even occurrences.

---

##### 19. Find Next Palindrome Number

Given a number, find the next smallest palindrome larger than the number. For example if the number is 125, next smallest palindrome is 131.

---

##### 20. Tree Level Order Print

Given a binary tree of integers, print it in level order. The output will contain space between the numbers in the same level, and new line between different levels.

---

##### 21. Tree Reverse Level Order Print

This is very similar to the previous post level order print. We again print the tree in level order, but now starting from bottom level to the root.

---

##### 22. Find Odd Occurring Element

Given an integer array, one element occurs odd number of times and all others have even occurrences. Find the element with odd occurrences.

---

##### 23. Find Word Positions in Text

Given a text file and a word, find the positions that the word occurs in the file. We’ll be asked to find the positions of many words in the same file.

---

##### 24. Find Next Higher Number With Same Digits

Given a number, find the next higher number using only the digits in the given number. For example if the given number is 1234, next higher number with same digits is 1243.

---

##### 25. Remove Duplicate Characters in String

Remove duplicate characters in a given string keeping only the first occurrences. For example, if the input is ‘tree traversal’ the output will be ‘tre avsl’.

---

##### 26. Trim Binary Search Tree

Given the root of a binary search tree and 2 numbers min and max, trim the tree such that all the numbers in the new tree are between min and max (inclusive). The resulting tree should still be a valid binary search tree.

---

##### 27. Squareroot of a Number

Find the squareroot of a given number rounded down to the nearest integer, without using the sqrt function. For example, squareroot of a number between [9, 15] should return 3, and [16, 24] should be 4.

---

##### 28. Longest Compound Word

Given a sorted list of words, find the longest compound word in the list that is constructed by concatenating the words in the list. For example, if the input list is: [‘cat’, ‘cats’, ‘catsdogcats’, ‘catxdogcatsrat’, ‘dog’, ‘dogcatsdog’, ‘hippopotamuses’, ‘rat’, ‘ratcat’, ‘ratcatdog’, ‘ratcatdogcat’]. Then the longest compound word is ‘ratcatdogcat’ with 12 letters. Note that the longest individual words are ‘catxdogcatsrat’ and ‘hippopotamuses’ with 14 letters, but they’re not fully constructed by other words. Former one has an extra ‘x’ letter, and latter is an individual word by itself not a compound word.

---

##### 29. Contains Duplicate

Given an array of integers, find if the array contains any duplicates.

1. Follow up: Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the difference between i and j is at most k.
2. Follow up: Given an array of integers, find out whether there are two distinct indices i and j in the array such that the difference between nums[i] and nums[j] is at most t and the difference between i and j is at most k.

---

##### 30. Sort Colors

Given an array with n objects colored red, white or blue, sort them so that objects of the same color are adjacent, with the colors in the order red, white and blue. (Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.)

1. Follow up: Can you give a one pass solution?
2. Follow up: What if there are N colors? You can use extra memory.

---

##### 31. H-Index

Given an array of citations (each citation is a non-negative integer) of a researcher, write a function to compute the researcher's h-index.

According to the definition of h-index on Wikipedia: "A scientist has index h if h of his/her N papers have at least h citations each, and the other N − h papers have no more than h citations each."

For example, given citations = [3, 0, 6, 1, 5], which means the researcher has 5 papers in total and each of them had received 3, 0, 6, 1, 5 citations respectively. Since the researcher has 3 papers with at least 3 citations each and the remaining two with no more than 3 citations each, his h-index is 3.

Note: If there are several possible values for h, the maximum one is taken as the h-index.

1. Follow up: for H-Index: What if the citations array is sorted in ascending order? Could you optimize your algorithm?

---

##### 32. Ugly Number

Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. 

	For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.

Note that 1 is typically treated as an ugly number.

<br>

Follow up: Write a program to find the n-th ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. 

	For example, 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 is the sequence of the first 10 ugly numbers.

Write a program to find the nth super ugly number.

Super ugly numbers are positive numbers whose all prime factors are in the given prime list primes of size k. 

	For example, [1, 2, 4, 7, 8, 13, 14, 16, 19, 26, 28, 32] is the sequence of the first 12 super ugly numbers given primes = [2, 7, 13, 19] of size 4.

Note:
(1) 1 is a super ugly number for any given primes.
(2) The given numbers in primes are in ascending order.
(3) 0 < k ≤ 100, 0 < n ≤ 106, 0 < primes[i] < 1000.


---

##### 33. Permutation

1. leetcode 46  Permutations
2. leetcode 47  Permutations II
3. leetcode 266 Palinarome Permutation
4. leetcode 266 Palinarome Permutation II
5. leetcode 60  Permutation Sequence
6. leetcode 31  Next Permutation

---

##### 34. Best time to buy and sell Stock

1. leetcode 121 Best Time to Buy and Sell Stock
2. leetcode 122 Best Time to Buy and Sell Stock II
3. leetcode 123 Best Time to Buy and Sell Stock III
4. leetcode 188 Best Time to Buy and Sell Stock IV
5. leetcode 309 Best Time to Buy and Sell Stock with Cooldown



<br>
<br>
<br>

---

{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}