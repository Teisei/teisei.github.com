---
layout: post
tldr: false
audio: false
title:  "Runnable or Thread"
date:   2015-07-05 15:14:54
categories: java multithreading
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


{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}