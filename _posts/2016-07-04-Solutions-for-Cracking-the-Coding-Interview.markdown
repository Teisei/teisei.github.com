---
layout: post
location: Shanghai, China
tldr: false
audio: false
title: Solutions for Cracking the Coding Interview
categories: Java
---

### Content

[1. Array and String](#Chapter1)

[2. Linked Lists](#Chapter2)

[3. Stack and Queues](#Chapter3)

[4. Tree and Graphs](#Chapter4)

[5. Bit Manipulation](#Chapter5)

[6. Brain Teasers](#Chapter6)

[7. Object Oriented Design](#Chapter7)

[8. Recursion](#Chapter8)

[9. Sorting and Search](#Chapter9)

[10. Mathematical](#Chapter10)

[11. System Design and Memory Limits](#Chapter11)

[12. Testing](#Chapter12)

[13. C++](#Chapter13)

[14. Java](#Chapter14)

[15. Databases](#Chapter15)

[16. Low Level](#Chapter16)

[17. Networking](#Chapter17)

[18. Threads and Locks](#Chapter18)

[19. Moderate](#Chapter19)

[20. Hard](#Chapter20)

<br>

---

### Chapter1

<font size='4'>Array and Strings</font>


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

[Back to Content](#content)

### Chapter2

<font size='4'>Linked Lists</font>










---

[Back to Content](#content)

### Chapter3

<font size='4'>Stack and Queues</font>










---

[Back to Content](#content)

### Chapter4

<font size='4'>Tree and Graphs</font>













---

[Back to Content](#content)

### Chapter5


<font size='4'>Bit Manipulation</font>













---

[Back to Content](#content)

### Chapter6


<font size='4'>Brain Teasers</font>













---

[Back to Content](#content)

### Chapter7


<font size='4'>Object Oriented Design</font>













---

[Back to Content](#content)

### Chapter8


<font size='4'>Recursion</font>













---

[Back to Content](#content)

### Chapter9


<font size='4'>Sorting and Searching</font>













---

[Back to Content](#content)

### Chapter10


<font size='4'>Mathematical</font>













---

[Back to Content](#content)

### Chapter11


<font size='4'>System Design and Memory Limits</font>













---

[Back to Content](#content)

### Chapter12


<font size='4'>Testing</font>













---

[Back to Content](#content)

### Chapter13


<font size='4'>C++</font>













---

[Back to Content](#content)

### Chapter14


<font size='4'>Java</font>













---

[Back to Content](#content)

### Chapter 15 Databases


<font size='4'>Tree and Graphs</font>













---

[Back to Content](#content)

### Chapter16


<font size='4'>Low Level</font>













---

[Back to Content](#content)

### Chapter17


<font size='4'>Networking</font>













---

[Back to Content](#content)

### Chapter18


<font size='4'>Threads and Locks</font>













---

[Back to Content](#content)

### Chapter19


<font size='4'>Moderate</font>













---

[Back to Content](#content)

### Chapter20

<font size='4'>Hard</font>













---

[Back to Content](#content)





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
{% endhighlight %}<font size='4'>Tree and Graphs</font>













---

[Back to Content](#content)

