---
layout: post
location: Shanghai, China
tldr: false
audio: false
title: Solutions for Cracking the Coding Interview
categories: Java
---

### Content

[1. Array and String](#chapter1)

[2. Linked Lists](#chapter2)

[3. Stack and Queues](#chapter3)

[4. Tree and Graphs](#chapter4)

[5. Bit Manipulation](#chapter5)

[6. Brain Teasers](#chapter6)

[7. Object Oriented Design](#chapter7)

[8. Recursion](#chapter8)

[9. Sorting and Search](#chapter9)

[10. Mathematical](#chapter10)

[11. System Design and Memory Limits](#chapter11)

[12. Testing](#chapter12)

[13. C++](#chapter13)

[14. Java](#chapter14)

[15. Databases](#chapter15)

[16. Low Level](#chapter16)

[17. Networking](#chapter17)

[18. Threads and Locks](#chapter18)

[19. Moderate](#chapter19)

[20. Hard](#chapter20)

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

Solution:
This is a classic interview question. The only "gotcha" is to try to do it in place, and to be careful for the null character.

	void reverse(char *str) {
		char * end = str;
		char tmp;
		if (str) {
			while (*end) {
				++end;
			}
			--end;
			while (str < end) {
				tmp = *str;
				*str++ = *end;
				*end-- = tmp;
			}
		}
	}


<br>

#### 1.3 Design an algorithm and write code to remove the duplicate characters in a string without using any additional buffer. NOTE: One or two additional variables are fine. An extra copy of the array is not.
FOLLOW UP: Write the test cases for this method.

Solution:
First, ask yourself, what does the interviewer mean by an additional buffer? Can we use an additional array of constant size?

Algorithm - No (large) Additional Memory:
1. For each character, check if it is a duplicate of already found characters.
2. Skip duplicate characters and update the non duplicate characters.

Time complexity is O(n^2).

	public static void removeDuplicates(char[] str) {
		if (str == null) return;
		int len = str.length;
		
		int tail = 1;
		
		for (int i = 1; i < len; ++i) {
			int j;
			for (j = 0; j < tail; ++j) {
				if (str[i] == str[j]) break;
			}
			if(j == tail) {
				str[tail] = str[i];
				++tail;
			}
		}
		str[tail] = 0;
	}
	
	Test case:
	1. String does not contain any duplicates, e.g.: abcd
	2. String contains all duplicates, e.g.: aaaa
	3. Null string
	4. String with all continuous duplicates, e.g.:aaabbb
	5. String with non-contiguous duplicates, e.g.: abababa

Algorithm - With additional memory of constant size

	public static void removeDuplicatesEff(char[] str) {
		if (str == null) return;
		int len = str.length;
		if (len < 2) return;
		boolean[] hit = new boolean[256];
		for (int i = 0; i < 256; ++i) {
			hit[i] = false;
		}
		hit[str[0]] = true;
		int tail = 1;
		for (int i = 1; i < len; ++i) {
			if (!hit[str[i]]) {
				str[tail] = str[i];
				++tail;
				hit[str[i]] = true;
			}
		}
		str[tail] = 0;
	}
	Test cases:
	1. String does not contain any duplicates, e.g. :abcd
	2. String contains all duplicates, e.g. : aaaa	3. Null string	4. Empty string	5. String with all continuous duplicates, e.g. : aaabbb	6. String with non-contiguous duplicates, e.g. : abababa


<br>

#### 1.4 Write 








[Back to Content](#content)

<br>

---

### Chapter2

<font size='4'>Linked Lists</font>










[Back to Content](#content)

<br>

---

### Chapter3

<font size='4'>Stack and Queues</font>










[Back to Content](#content)

<br>

---

### Chapter4

<font size='4'>Tree and Graphs</font>













[Back to Content](#content)

<br>

---

### Chapter5


<font size='4'>Bit Manipulation</font>













[Back to Content](#content)

<br>

---

### Chapter6


<font size='4'>Brain Teasers</font>













[Back to Content](#content)

<br>

---

### Chapter7


<font size='4'>Object Oriented Design</font>













[Back to Content](#content)

<br>

---

### Chapter8


<font size='4'>Recursion</font>













[Back to Content](#content)

<br>

---

### Chapter9


<font size='4'>Sorting and Searching</font>













[Back to Content](#content)

<br>

---

### Chapter10


<font size='4'>Mathematical</font>













[Back to Content](#content)

<br>

---

### Chapter11


<font size='4'>System Design and Memory Limits</font>













[Back to Content](#content)

<br>

---

### Chapter12


<font size='4'>Testing</font>













[Back to Content](#content)

<br>

---

### Chapter13


<font size='4'>C++</font>













[Back to Content](#content)

<br>

---

### Chapter14


<font size='4'>Java</font>













[Back to Content](#content)

<br>

---

### Chapter 15 Databases


<font size='4'>Tree and Graphs</font>













[Back to Content](#content)

<br>

---

### Chapter16


<font size='4'>Low Level</font>













[Back to Content](#content)

<br>

---

### Chapter17


<font size='4'>Networking</font>













[Back to Content](#content)

<br>

---

### Chapter18


<font size='4'>Threads and Locks</font>













[Back to Content](#content)

<br>

---

### Chapter19


<font size='4'>Moderate</font>













[Back to Content](#content)

<br>

---

### Chapter20

<font size='4'>Hard</font>













[Back to Content](#content)

<br>

---





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

