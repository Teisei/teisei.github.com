---
layout: post
location: Shanghai, China
tldr: false
audio: false
title: Combine two strings
categories: interview
---

### Problem Definition

We are given 3 strings: str1, str2, and str3. Str3 is said to be a shuffle of str1 and str2 if it can be formed by interleaving the characters of str1 and str2 in a way that maintains the left to right ordering of the characters from each string. For example, given str1=”abc” and str2=”def”, str3=”dabecf” is a valid shuffle since it preserves the character ordering of the two strings. So, given these 3 strings write a function that detects whether str3 is a valid shuffle of str1 and str2.

<br>
<br>

---


### Analysis


<br>
<br>

---


### Solution 1 : Backtracking

{% highlight java %}
public boolean isCombined(String s1, String s2, String s3){
	if(s1.length()+s2.length() != s3.length()) return false;
	if(s1.equals("")) return s2.equals(s3);
	if(s2.equals("")) return s1.equals(s3);

	int len1 = s1.length(), len2 = s2.length();

	int p1 = 0, p2 = 0, p3 = 0;
	//int start1 = -1, start2 = -1;
	char x, y;
	while(p3 < s3.length()){

		if(p1==len1){
			while(p2<len2){
				if(s2.charAt(p2)!=s3.charAt(p3)) return false;
				p2++;
				p3++;
			}
			return true;
		}
		if(p2==len2){
			while(p1<len1){
				if(s1.charAt(p1)!=s3.charAt(p3)) return false;
				p1++;
				p3++;
			}
			return true;
		}

			
		//find common
		int start1 = p1, start2 = p2, len = 0;
		while(p1<len1 && p2<len2){
			if(s1.charAt(p1) == s3.charAt(p3) 
				&& s2.charAt(p2) == s3.charAt(p3)){
				len++; p1++; p2++; p3++;
			}else{
				break;
			}
		}
		System.out.println("**** "+len+" ****");		//p1,p2,p3

		if(len==0){
			//only one can match
			if(s1.charAt(p1) == s3.charAt(p3)) p1++;
			else if(s2.charAt(p2) == s3.charAt(p3)) p2++;
			else return false;
			p3++;

		}else{
			//check s3[p3] == ?
			if(p1==len1 && p2==len2){
				p2 = start2;
			}else if(p1==len1){
				p1 = start1;
			}else if(p2==len2){
				p2 = start2;
			}else{
				if(s1.charAt(p1)==s3.charAt(p3)){
					p2 = start2;
				}else{
					p1 = start1;
				}
			}
		}
		//p3++;
		System.out.println(p1+"\t"+p2+"\t"+p3);
	}
	return true;
}
{% endhighlight %}

<br>
<br>

---


### Solution 2 : Dynamic Programming

{% highlight java %}

{% endhighlight %}

<br>
<br>

---

### Solution 3 : Path search

{% highlight java %}
class MyNode{
	public int i, j, k;
	MyNode(int i, int j, int k){
		this.i = i;
		this.j = j;
		this.k = k;
	}
}
public boolean isCombined2(String s1, String s2, String s3){
	int len1 = s1.length(), len2 = s2.length(), len3 = s3.length();
	/* special case */
	if(len1 + len2 != len3) return false;

	List<MyNode> queue = new ArrayList<MyNode>();
	/* initial state */
	int start1 = -1, start2 = -1, start3 = -1;
	int end1 = len1-1, end2 = len2-1, end3 = len3-1;
		
	MyNode root = new MyNode(start1, start2, start3);
	queue.add(root);

	while(queue.size()>0){
		List<MyNode> new_queue = new ArrayList<MyNode>();

		for(MyNode node: queue){

			int i = node.i, j = node.j, k = node.k;
				
			// if finished
			if(k == end3) return true;

			//find common with length: len				
			int len = 0;
			while(i + len + 1 <= end1 && j + len + 1 <= end2){
				if(s1.charAt(i + len + 1) != s3.charAt(k + len + 1) 
					|| s2.charAt(j + len + 1) != s3.charAt(k + len + 1))
					break;
				len++;
			}

			if(len > 0){
				// if find the same string, add both of them as possibility
				new_queue.add(new MyNode(i, j + len, k + len));
				new_queue.add(new MyNode(i + len, j, k + len));
			}else{
				if(i < end1)
					if(s1.charAt(i+1) == s3.charAt(k+1))
						new_queue.add(new MyNode(i+1, j, k+1));

				if(j < end2)
					if(s2.charAt(j+1) == s3.charAt(k+1))
						new_queue.add(new MyNode(i, j+1, k+1));
			}

			queue = new_queue;
		}
	}
	return false;
}
{% endhighlight %}


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