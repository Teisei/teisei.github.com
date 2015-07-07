---
layout: post
title: Runnable-or-Thread
description: This article introduces two ways to implement Java multithreading, 
extending a Java class Thread or implementing a Java interface Runnable.
A Comparison between these two ways are given.
keywords: Java, Multithreading
---


# Java multithreading  
Thread is a block of code which can be execute concurrently with other threads in the JVM.
To implement Java thread is just to specify what code a thread should run.  

## extends Thread class  
create a subclass of Thread and override the run() method:  
{% highlight java %}  
  public class MyThread extends Thread {
    public void run(){
      System.out.println("MyThread running");
    }
  }
  public class Teisei {
    public static void main(String args[]){
      Thread thread = new MyThread();
      thread.start();
    }
  }
{% endhighlight %}  
you can also create an anonymous subclass of Thread like this:    
{% highlight java %}
  Thread thread = new Thread(){
    public void run(){
      System.out.println("Thread Running");
    }
  }
thread.start();
{% endhighlight %}




## implement interface  java.lang.Runnable  
{% highlight java %}
  public class MyRunnable implements Runnable {
    public void run(){
       System.out.println("MyRunnable running");
    }
  }
{% endhighlight %}  
To have the run() method executed by a thread, pass an instance of MyRunnable to a Thread in its constructor.  
{% highlight java %}
   Thread thread = new Thread(new MyRunnable());
   thread.start();
{% endhighlight %}  
You can also create an anonymous implementation of Runnable, like this:  
{% highlight java %}
  Runnable myRunnable = new Runnable(){
    public void run(){
      System.out.println("Runnable running");
    }
  }
  Thread thread = new Thread(myRunnable);
  thread.start();
{% endhighlight %}    


## Subclass or Runnable?  
### The most common difference is  
+ extend **Thread** class, you can't extend any other class which you required.  
+ implement **Runnable** interface, you can save a space for your class to extend any other class in future or now.  
### The significant difference is  




# 这是 H1   
## This is H2   
### This is H3

>## 这是一个标题

* Red
* Green
* blue

- 红色
- 绿色
- 蓝色

+ Red
+ Green
+ Blue

1. Bird
2. Cat
3. Dog

这是一个普通段落：
    这是一个代码区块。
    
这是一个普通段落:
    这是一个代码区块.
    
***
* * *
*****
* * * * *
- - -
--------------------

This is [an example](http://teisei.github.io "Title")inline link.

[This link](http://teisei.github.io) has no title attribute.

See my [About](/about/) page for details.

This is [an example][id] reference-style link.

THis is [an example] [id] reference-style link.

[id]: http://example.com/ "optional title here"

[Google][]

[Google]: http://www.google.com

Visit [Daring Fireball][]  for more information.


强调：  
*single asterisks*

_single underscores_

**double asterisks**

__double underscores__


代码：  
Use the `print()` function  

<p>Use the <code>print()</code></p>

如果要在代码中插入反引号
``There is a literal backtick (`) here.``

A single backtick in a code span. `` ` ``

A backtick-delimited string in a code span. `` `foo` ``



图片：   
1  
![Alt text](images/work/i-pizn.jpg)     
2  
![Alt text](images/work/Campus_App.png "Optional title")   
3   
![Alt text][id]    
4    
[i-pizn.jgp]: images/work/i-pizn.jpg   "optional attribute"

<div class="dp-highlighter"><div class="bar"></div><ol class="dp-j" start="1"><li class="alt"><span><span class="keyword">public</span><span>&nbsp;</span><span class="keyword">class</span><span>&nbsp;C{&nbsp;&nbsp;</span></span></li><li class=""><span>&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword">public</span><span>&nbsp;</span><span class="keyword">static</span><span>&nbsp;</span><span class="keyword">void</span><span>&nbsp;main(String&nbsp;args[]){&nbsp;&nbsp;</span></span></li><li class="alt"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;System.out.println(<span class="string">"hello&nbsp;world!"</span><span>);&nbsp;&nbsp;</span></span></li><li class=""><span>&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;&nbsp;</span></li><li class="alt"><span>}&nbsp;&nbsp;</span></li></ol></div>


{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}