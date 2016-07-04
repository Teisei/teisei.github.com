---
layout: post
location: Shanghai, China
tldr: false
audio: false
title: Solutions for Cracking the Coding Interview
categories: Java
---

### Content

[目录](#jump1)

---

### Chapter 1 Arrays and Strings

#### 1.1 Implement an algorithm to determine if a string has all unique characters. What if you can not use additional data structures?

Solution:
For simplicity, assume char set if ASCII (if not, we need to increase the storage size. The rest logic would be the same). NOTE: This is a great thing to point out to your interviewer!

	public static boolean isUniqueChars(String str) {
		boolean[] char_set = new boolean[256];
		for (int i = 0; i < str.length(); i++) {
			int val = str.charAt(i);
			if (char_set[val]) return false;
			char_set[val] = true;
		}
		return true;
	}
	time: O(n)
	space: O(n)
	
We can reduce the space usage a little bit by using a bit vector. We will assume, in the below code, that the string is only lower case 'a' through 'z'. This will allow us to use just a single int

	public static boolean isUniqueChars(String str) {
		int checker = 0;
		for (int i = 0; i < str.length(); ++i) {
			int val = str.charAt(i) - 'a';
			if((checker & (1 << val)) > 0) return false;
			checker |= (1 << val);
		}
		return true;
	}
	Alternatively, we could do the following:
	1. Check every char of the string with every other char of the string for duplicate occurences. This will take O(n^2) time and no space;
	2. If we are allowed to destroy the input string, we could sort the string in O(n log n) time and then linearly check the string for neighboring characters that are identical. Careful, though - many sorting algorithms take up extra space.

<br>

#### 1.2 Write code to reverse a C-Style String. (C-Style means that "abcd" is represented as five characters, including the null character.)

<br>

#### 1.3 

<br>

---

<br>

### Chapter 2 Linked Lists


### Chapter 3 Stack and Queues


### Chapter 4 Tree and Graphs


### Chapter 5 Bit Manipulation


### Chapter 6 Brain Teasers


### Chapter 7 Object Oriented Design


### Chapter 8 Recursion


### Chapter 9 Sorting and Searching


### Chapter 10 Mathematical


### Chapter 11 System Design and Memory Limits


### Chapter 12 Testing


### Chapter 13 C++


### Chapter 14 Java


### Chapter 15 Databases


### Chapter 16 Low Level


### Chapter 17 Networking


### Chapter 18 Threads and Locks


### Chapter 19 Moderate


### Chapter 20 Hard


<a name='#jump1'>跳转到这里：</a>


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