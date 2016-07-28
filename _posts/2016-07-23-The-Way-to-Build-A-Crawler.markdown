---
layout: post
location: Shanghai, China
tldr: false
audio: false
title: The Way to Build a Crawler
categories: Java
---
### References

[1] [硅谷之路爬虫系列][ln1]

[ln1]:	https://zhuanlan.zhihu.com/p/20821699

<br>

---

### Introduction

How can we fetch the data from the Internet and extract useful information from the data to help decision making?

<br>

---

### Basic Crawler

##### Two types of crawlers:

1. Crawlers downloading web pages;
2. Crawlers extracting links from the pages.

##### Work flow

1. loads the crawling task (url list, common resources) into memory;
2. scan through the url list, for each url the crawler does the following steps:
	- first check if it is connected to the server, if not create one;
	- then sends a http request to the sever to download data;
	- label the current url is completed;
	- parses the data and extract urls, add them into the url list.
4. continue doing this util no urls to be crawled.

##### Discussion

1. What if the crawling task is too huge?
2. How to store the states for the urls?
3. How to crawl pages from different site with different page schemas?

##### Maybe

1. Divide them into pieces?
2. Store it in memory, file, database?
3. Define different parsing strategies and pass them into the crawlers?


<br>

---

### Multithread

##### Main idea

1. A thread runs a crawler;
2. To run multiple crawlers using multithreading programming.
3. Scheduling

##### Issue

taskTable and pageTable is shared;

##### Three types of solutions

1. 睡眠（Sleep）
2. 条件变量（Conditional Variable)
3. 信号量（Semaphore）

##### Pub/Sub Model

LMAX Disruptor这套最快的无锁生产者消费者的模型



<br>

---

### Distributed

##### 4 Components

1. Crawlers: 
2. Database: the place to store the tasks and pages;
3. Sender: 
4. Receiver

<br>

---

### Conclusion



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

