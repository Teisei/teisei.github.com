---
layout: post
location: Shanghai, China
tldr: false
audio: false
title: Leetcode Locked Problems
categories: algorithm interview
---

### References


[Jianchao's Blog][ln1]

[Doufu][ln2]

[ln1]:	http://www.cnblogs.com/jcliBlogger/category/697022.html
[ln2]:	http://blog.csdn.net/xudli/article/category/1357585

<br><br>

---


### Problems


##### [1] 156	Binary Tree Upside Down

* 	38.7%		Medium

	
Given a binary tree where all the right nodes are either leaf nodes 
with a sibling (a left node that shares the same parent node) or empty, 
flip it upside down and turn it into a tree where the original right nodes 
turned into left leaf nodes. Return the new root.

	For example:
	Given a binary tree {1,2,3,4,5},
	    1	
	   / \ 
	  2   3
	 / \
	4  5
	
	return the root of the binary tree [4,5,2,#,#,3,1].
	    4
	   / \
	  5   2
	 / \
	3   1

<br>

---

##### [2]	157	Read N Characters Given Read4

* 29.4%		Easy

The API: int read4(char *buf) reads 4 characters at a time from a file.

The return value is the actual number of characters read. For example, it returns 3 if there is only 3 characters left in the file.

By using the read4 API, implement the function int read(char *buf, int n) that reads n characters from the file.

Note: The read function will only be called once for each test case.

<br>

---

##### [3]	158	Read N Characters Given Read4 II - Call multiple times 

---

##### [4]	159	Longest Substring with At Most Two Distinct Characters 

---

##### [5]	161	One Edit Distance 

---

##### [6]	163	Missing Ranges 

---

##### [7] 167	Two Sum II - Input array is sorted 

Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.
The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.
You may assume that each input would have exactly one solution.

	Input: numbers={2, 7, 11, 15}, target=9
	Output: index1=1, index2=2

<br>

---

##### [8] 170	Two Sum III - Data structure design 

Design and implement a TwoSum class. It should support the following operations:add and find.
add - Add the number to an internal data structure.
find - Find if there exists any pair of numbers which sum is equal to the value.

	For example,
	add(1); add(3); add(5);
	find(4) -> true
	find(7) -> false

<br>

---

##### [9] 186	Reverse Words in a String II 

---

##### [10]	243	Shortest Word Distance 	

* 47.0%		Easy

Given a list of words and two words word1 and word2, return the shortest distance between these two words in the list.

	For example,
	Assume that words = ["practice", "makes", "perfect", "coding", "makes"].

	Given word1 = "coding", word2 = "practice", return 3.
	Given word1 = "makes", word2 = "coding", return 1.

Note:
You may assume that word1 does not equal to word2, and word1 and word2 are both in the list.

<br>

---

##### [11] 244	Shortest Word Distance II 	

* 35.4%		Medium

This is a follow up of Shortest Word Distance. The only difference is now you are given the list of words and your method will be called repeatedly many times with different parameters. How would you optimize it?

Design a class which receives a list of words in the constructor, and implements a method that takes two words word1 and word2 and return the shortest distance between these two words in the list.

	For example,
	Assume that words = ["practice", "makes", "perfect", "coding", "makes"].

	Given word1 = "coding”, word2 = "practice”, return 3.
	Given word1 = "makes", word2 = "coding", return 1.

Note:
You may assume that word1 does not equal to word2, and word1 and word2 are both in the list.

<br>

---

##### [12] 245	Shortest Word Distance III 	

* 46.4%		Medium

This is a follow up of Shortest Word Distance. The only difference is now word1 could be the same as word2.

Given a list of words and two words word1 and word2, return the shortest distance between these two words in the list.

word1 and word2 may be the same and they represent two individual words in the list.

	For example,
	Assume that words = ["practice", "makes", "perfect", "coding", "makes"].

	Given word1 = “makes”, word2 = “coding”, return 1.
	Given word1 = "makes", word2 = "makes", return 3.

Note:
You may assume word1 and word2 are both in the list.

<br>

---

##### [13] 246	Strobogrammatic Number 	

* 36.8%		Easy

A strobogrammatic number is a number that looks the same when rotated 180 degrees (looked at upside down).

Write a function to determine if a number is strobogrammatic. The number is represented as a string.

	For example, the numbers "69", "88", and "818" are all strobogrammatic.


---

##### [14] 247	Strobogrammatic Number II 	 	
* 34.7%		Medium

This problem can be solved easily once you find the regularities :-) This link has done it for you. You may refer to its Python version.


---

##### [15] 248	Strobogrammatic Number III 	 	

* 27.4%		Hard

---

##### [16] 249	Group Shifted Strings 	 	

* 31.9%		Easy

---

##### [17] 250	Count Univalue Subtrees 	 	

* 36.9%		Medium

---

##### [18] 251	Flatten 2D Vector 	 	

* 34.6%		Medium

---

##### [19] 252	Meeting Rooms 	 	

* 42.1%		Easy

---

##### [20] 253	Meeting Rooms II 	 	

* 35.0%		Medium

---

##### [21] 254	Factor Combinations 	 	

* 35.3%		Medium

---

##### [22] 255	Verify Preorder Sequence in Binary Search Tree 	 	
* 37.4%		Medium

---

##### [23] 256	Paint House 

---

##### [24] 259	3Sum Smaller 

---

##### [25] 261	Graph Valid Tree 

---

##### [26] 265	Paint House II 

---

##### [27] 266	Palindrome Permutation 

---

##### [28] 267	Palindrome Permutation II 

---

##### [29] 269	Alien Dictionary 	 	

* 23.4%		Hard

---

##### [30] 270	Closest Binary Search Tree Value	 	

* 34.8%		Easy

---

##### [31] 271	Encode and Decode Strings 	 	

* 27.2%		Medium

---

##### [32] 272	Closest Binary Search Tree Value II 

---

##### [33] 276	Paint Fence 	 	

* 31.2%		Easy

---

##### [34] 277	Find the Celebrity 


---

##### [35] 280	Wiggle Sort 	 	

* 49.9%		Medium

---

##### [36] 281	Zigzag Iterator 

---

##### [37] 285	Inorder Successor in BST 	 	

* 35.8%		Medium

---

##### [38] 286	Walls and Gates 

---

##### [39] 288	Unique Word Abbreviation 

---

##### [40] 291	Word Pattern II 

---

##### [41] 293	Flip Game 	 	

* 50.3%		Easy

---

##### [42] 294	Flip Game II 

---

##### [43] 296	Best Meeting Point 

---

##### [44] 298	Binary Tree Longest Consecutive Sequence

---

##### [45] 302	Smallest Rectangle Enclosing Black Pixels 

---

##### [46] 305	Number of Islands II 

---

##### [47] 308	Range Sum Query 2D - Mutable

---

##### [48] 311	Sparse Matrix Multiplication

---

##### [49] 314	Binary Tree Vertical Order Traversal 

---

##### [50] 317	Shortest Distance from All Buildings 

---

##### [51] 320	Generalized Abbreviation 

---

##### [52] 323	Number of Connected Components in an Undirected Graph 

---

##### [53] 325	Maximum Size Subarray Sum Equals k 

---

##### [54] 333	Largest BST Subtree 

---

##### [55] 339	Nested List Weight Sum	

* 55.3%		Easy

Given a nested list of integers, return the sum of all integers in the list weighted by their depth.

Each element is either an integer, or a list -- whose elements may also be integers or other lists.

	Example 1:
	Given the list [[1,1],2,[1,1]], return 10. (four 1's at depth 2, one 2 at depth 1)

	Example 2:
	Given the list [1,[4,[6]]], return 27. (one 1 at depth 1, one 4 at depth 2, and one 6 at depth 3; 1 + 4*2 + 6*3 = 27)

---

##### [56] 340	Longest Substring with At Most K Distinct Characters 

---

##### [57] 346	Moving Average from Data Stream 

---

##### [58] 348	Design Tic-Tac-Toe 

---

##### [59] 351	Android Unlock Patterns 

---

##### [60] 353	Design Snake Game 


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