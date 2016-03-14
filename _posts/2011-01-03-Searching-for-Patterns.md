---
layout: post
title: "Searching for Patterns"
date: 2011-1-03 18:43:00
categories: algorithm
---

## Searching for Pattern

input: two arrays of characters T[1,...,n], P[1,...,m], m<n; 
find all sub-array in T[] that match P[].

### Naive Method

#### Basic idea
We check every i, from 0 to (n-m+1), if T[i, ..., i+m] matches P[0, ..., m];
If some element in T[i, ..., i+m] does not match, we retry from i+1.

#### Analysis
* best case
    + the first character in P[] does not exist in T[].
* worst case
    + When all the characters of T[] and P[] are same;
    + The last character is different.

#### C code

    void search4pattern(char a[], char p[]){
    	int n = strlen(a);
    	int m = strlen(p);
    	for(int i=0;i<n-m+1;i++){
    		bool flag = true;
    		//compare all the m chars
    		for(int j=0;j<m;j++){
    			if(a[i+j]!=p[j]){
    				flag = false;
    				break;
    			}
    		}
    		if(flag)
    			printf("position %d in a[] is a match!\n", i);
    	}
    }
    

---


### KMP method
* Suppose this time we start match at the **i**th element in **T[]**, and have already matched the first **(x-1)** chars.
We failed to match T[i+x] and P[x].  
  That means  
  + `T[i+j] == P[j], j from 0 to x-1`;
  + `T[i+x] != P[x]`;
* At this time, someone tell us that in `P[0, ..., x-1]`(matched, length l), exist a **good-prefix** that matches a suffix;  
  Here **good-prefix** means,
  + **good-prefix** = P[0, ..., l-1], with length l;
  + A P_suffix = P[x-l, ..., x-1] matches **good prefix**;
  + easily leads to **good-prefix** matches T[i+0, ..., i+l-1] matches T[i+x-l, ..., i+x-1];
  + No longer prefix satisfies these conditions.
* A this point, if we fail at index (x), we don't have to start from index (i+1) in T[] one by one, 
we can easily skip to compare T[i+x] and P[l];

#### Basic idea
* Though this **good-prefix** helps us a lot in skip some indexes which can not lead to whole match, 
we can not compute the **good-prefix** every time we encount a mis-match.
* Sicne the pattern string mostly has a smaller length, We can compute it before we do a pattern searching, with a small complexity; 
* We create an auxiliary array of numbers lps[0,...,m-1], where lps[i] means the length of the **good prefix** in P[0, ..., i];
* how to compute the **good-prefix** for each element in P[];
    + lps[0] = 0
    + Suppose lps[i-1]=l, we want to get lps[i] based on **good-prefix** of P[0, ..., i-1].
    if P[i]==P[l], then lps[i]=l+1; 
    else we can only recursively try to get lps[i] based on **sub-good-prefix** of **good-prefix**,
    until there is no **good-prefix** for P[i];
    + at that time, we can only set P[i] 0.
* Now we can start pattern-searching from index 0 in T[], suppose we compare T[i+x] and P[x] and fail, 
we restart by comparing T[i+x] and P[lps[x-1]];
* If we compare the P[m-1] and it matches, we get a matched-pattern.

#### Analysis
O(n)

#### C code

    void search4pattern_KMP(char T[], char P[]){
    	int n = strlen(T);
    	int m = strlen(P);
    	
    	//compute lps first
    	int lps[m];
    	int pos = 0;
    	lps[pos] = 0;
    	if(m>1){
    		int i = 1;
    		while(i<m){
    			if(P[i]==P[pos])
    				pos++,lps[i++] = pos;
    			else
    				if(pos!=0)
    					pos = lps[pos-1];
    				else
    					lps[i++]=0;
    		}
    	}
    
    	int i = 0;
    	int j=0;
    	while(i<n){
    		if(T[i]==P[j]){
    			i++;
    			j++;
    		}else{
    			if(j==0)
    				i++;
    			else{
    				j = lps[j-1];
    			}
    		}
    		if(j==m){
    			printf("here is a good match [%d, ...]!\n", i-j);
    			j = lps[m-1];
    		}
    	}
    }
    
---




{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}