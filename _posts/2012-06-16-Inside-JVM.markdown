---
layout: post
title: Inside-Java-Virtual-Machine
description: This article is an Introduction to Java Virtual Machine.
keywords: Java
---
# Java: JVM

标签（空格分隔）： Java JVM

---
JVM is a abbreviation of Java Virtual Machine.
JVM is a abstract computer where java byte codes are executed.
It offer a platform that separate the java compiled byte codes and the underlying hardware.

three concepts:

**JVM specification**;
**one JVM implementation**;
**a JVM runtime instance**.

we are going to talk about JVM specification.

A JVM consists of 1) ClassLoader; 2)runtime data areas; 3)execute engine.
1)**ClassLoader**
bootstrap: system class loader;
subclass of java.lang.ClassLoader: user defined class loader:

2)**runtime data area**:
common area(multi-threads accessible)
a)method area: the area in memory to store method information;
b)heap: the area in memory to store java class instances;
private area(single-thread accessible)
a)java stack
b)pc register
other:
native stacks

3)**execute engine**:
one execute engine instance in JVM is a Java thread.

Suppose we have a compiled java class file whose main method is the entrance of one java application.
Lifetime of a java type(class):
1)loaded by one class loader:
2)Linking：
    verification;
    preparation;
    resolution;
3)initialization:


{% highlight java %}
public class Teisei {
    public static void main(String args[]){
        System.out.println("Hello world! This is Teisei's blog");
    }
}
{% endhighlight %}