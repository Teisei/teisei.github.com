---
layout: post
location: Shanghai, China
tldr: false
audio: false
title: Popular Java Interview Questions
categories: Java
---

## Popular Java Interview Questions

#### Data types


基本类型 | 占用空间 | 表示范围 | 包装其类型
------- | ------- | ------ | ------- 
boolean	| 1/8 | true or false  | Boolean
char    |  2  | -128 ~ 127     | Character
byte    |  1  | -128 ~ 127     | Byte
short   |  2  | -2^15 ~ 2^15-1 | Short
int     |  4  | -2^31 ~ 2^31-1 | Integer
long    |  8  | -2^63 ~ 2^63-1 | Long
float   |  4  | -3.403E38 ~ 2.404E38 | Float 
double  |  8  | -1.798E308 ~ 1.798E308 | Double 


<br>

---

### Access Control

访问权限 | 类 | 包 | 子类 | 其他包
 --- | --- | --- | --- | ---
public  | yes | yes | yes | yes 
protect | yes | yes | yes | no
default | yes | yes | no  | no
private | yes | no  | no  | no

<br>

---



#### Switch能否用string做参数

C++不可以。switch的参数不可以是string。switch是用”==“进行比较，而string没有”="的概念，只有strcmp。 
Java允许的。

<br>

---

#### `equals` 与 `==` 的区别， `HashCode` 的作用

1. `==` 和 `equals()`：

    `==` 运算符只能判断值相等，而 `equals()` 方法默认对两个对象的地址值进行比较，不同的类会有不同的重载方式。 

2. `equals()` 和 `hashcode()`： 

    - 这两个方法都是从 `object` 类中继承过来的。 
    - `equals()` 是对两个对象的地址值进行的比较（即比较引用是否相同）。但是我们必需清楚，当 `String` 、 `Math`、还有 `Integer`、 `Double` 等这些封装类在使用 `equals()` 方法时，已经覆盖了 `object` 类的 `equals()` 方法。 
    - `hashcode()` 是一个本地方法，它的实现是根据本地机器相关的。同理，不同类的 `hashcode()` 方法也被覆盖，有不同的实现。 `Hashcode`主要用于查找的快捷性。 

3. 小技巧： 

    - `equals()` 相等的两个对象，`hashcode()` 一定相等；反之则不然。 
    - 在 `Java` 的集合中，判断两个对象是否相等的规则是：判断两个对象的 `hashCode`，若相等，则判断 `equals`。 
 
4. 参考链接： 

    - http://www.iteye.com/topic/257191 
    - http://blog.csdn.net/fenglibing/article/details/8905007

<br>

---

#### Object有哪些公用方法 

1．`clone()` 方法 

保护方法，实现对象的浅复制，只有实现了Cloneable接口才可以调用该方法，否则抛出CloneNotSupportedException异常。 
 
2．`getClass()` 方法 

final方法，获得运行时类型。 
 
3．`toString()` 方法 

该方法用得比较多，一般子类都有覆盖。 
 
4．`finalize()` 方法 

该方法用于释放资源。因为无法确定该方法什么时候被调用，很少使用。 
 
5．`equals()` 方法 

该方法是非常重要的一个方法。一般equals和==是不一样的，但是在Object中两者是一样的。子类一般都要重写这个方法。 
 
6．`hashCode()` 方法 

- 该方法用于哈希查找，重写了equals方法一般都要重写hashCode方法。这个方法在一些具有哈希功能的 `Collection` 中用到。 
- 一般必须满足 `obj1.equals(obj2)==true` 能够推导出 `obj1.hashCode()==obj2.hashCode()`，
- 但是 `hashCode` 相等不一定就满足 `equals` 。
- 不过为了提高效率，应该尽量使上面两个条件接近等价。
 
7．`wait()` 方法 

- `wait()` 方法就是使当前线程等待该对象的锁，当前线程必须是该对象的拥有者，也就是具有该对象的锁。
- `wait()` 方法一直等待，直到获得锁或者被中断。 
- `wait(long timeout)` 设定一个超时间隔，如果在规定时间内没有获得锁就返回。 
- 调用该方法后当前线程进入睡眠状态，直到以下事件发生。 

    1. 其他线程调用了该对象的notify方法。 
    2. 其他线程调用了该对象的notifyAll方法。 
    3. 其他线程调用了interrupt中断该线程。 
    4. 时间间隔到了。 

此时该线程就可以被调度了，如果是被中断的话就抛出一个InterruptedException异常。 
 
8．`notify()` 方法 

该方法唤醒在该对象上等待的某个线程。 
 
9．`notifyAll()` 方法 

该方法唤醒在该对象上等待的所有线程。 

<br>

---


#### Java的四种引用，强弱软虚，用到的场景 

1. 强引用（StrongReference） 

强引用是使用最普遍的引用。如果一个对象具有强引用，那垃圾回收器绝不会回收它。当内存空间不足，`Java` 虚拟机宁愿抛出 `OutOfMemoryError` 错误，使程序异常终止，也不会靠随意回收具有强引用的对象来解决内存不足的问题。  ps：强引用其实也就是我们平时 `A a = new A()` 这个意思。 

2. 软引用（SoftReference） 

如果一个对象只具有软引用，则内存空间足够，垃圾回收器就不会回收它；如果内存空间不足了，就会回收这些对象的内存。只要垃圾回收器没有回收它，该对象就可以被程序使用。软引用可用来实现 `内存敏感的高速缓存`。 

3. 弱引用（WeakReference） 

弱引用与软引用的区别在于：只具有弱引用的对象拥有更短暂的生命周期。在垃圾回收器线程扫描它所管辖的内存区域的过程中，一旦发现了只具有弱引用的对象，不管当前内存空间足够与否，都会回收它的内存。不过，由于垃圾回收器是一个优先级很低的线程，因此不一定会很快发现那些只具有弱引用的对象。 

4. 虚引用（PhantomReference） 

“虚引用”顾名思义，就是形同虚设，与其他几种引用都不同，虚引用并不会决定对象的生命周期。如果一个对象仅持有虚引用，那么它就和没有任何引用一样，在任何时候都可能被垃圾回收器回收。 
虚引用主要用来跟踪对象被垃圾回收器回收的活动。虚引用与软引用和弱引用的一个区别在于：虚引用必须和引用队列 （ReferenceQueue）联合使用。当垃圾回收器准备回收一个对象时，如果发现它还有虚引用，就会在回收对象的内存之前，把这个虚引用加入到与之 关联的引用队列中。 
 
参考链接： 

    - http://blog.csdn.net/coding_or_coded/article/details/6603549 
    - http://soft.chinabyte.com/database/149/12485149.shtml
    
<br>

---

#### ArrayList、LinkedList、Vector的区别 

- `ArrayList`: 元素单个，效率高，多用于查询
- `Vector`: 元素单个，线程安全，多用于查询
- `LinkedList`:元素单个，多用于插入和删除 
 
1. `List` 是有序的 `Collection`，使用此接口能够精确的控制每个元素插入的位置。用户能够使用索引（元素在List中的位置，类似于数组下标）来访问List中的元素，这类似于Java的数组。
 
2. `Vector`： 
基于数组（`Array`）的 `List`，其实就是封装了数组所不具备的一些功能方便我们使用，所以它难易避免数组的限制，同时性能也不可能超越数组。所以，在可能的情况下，我们要多运用数组。另外很重要的一点就是 `Vector` 是线程同步的(sychronized)的，这也是 `Vector` 和 `ArrayList` 的一个的重要区别

3. `ArrayList`： 
同 `Vector` 一样是一个基于数组上的链表，但是不同的是 `ArrayList` 不是同步的。所以在性能上要比 `Vector` 好一些，但是当运行到多线程环境中时，可需要自己在管理线程的同步问题。

4. `LinkedList`： 
LinkedList不同于前面两种 `List` ，它不是基于数组的，所以不受数组性能的限制。
它每一个节点（Node）都包含两方面的内容 

    1.节点本身的数据（data）
    2.下一个节点的信息（nextNode）

所以当对 `LinkedList` 做添加，删除动作的时候就不用像基于数组的 `ArrayList` 一样，必须进行大量的数据移动。只要更改 `nextNode` 的相关信息就可以实现了，这是 `LinkedList` 的优势。
 
List总结： 
所有的List中只能容纳单个不同类型的对象组成的表，而不是Key－Value键值对。例如：[ tom,1,c ] 
所有的List中可以有相同的元素，例如Vector中可以有 [ tom,koo,too,koo ] 
所有的List中可以有null元素，例如[ tom,null,1 ] 
基于Array的List（Vector，ArrayList）适合查询，而LinkedList 适合添加，删除操作

<br>

---

#### `String`、`StringBuffer` 与 `StringBuilder` 的区别 

- `String` 类中使用字符数组保存字符串，如下就是，因为有“final”修饰符，所以可以知道string对象是不可变的。 
- `StringBuilder` 与 `StringBuffer` 都继承自 `AbstractStringBuilder` 类，在 `AbstractStringBuilder` 中也是使用字符数组保存字符串，可知这两种对象都是可变的。 
- `String` 中的对象是不可变的，也就可以理解为常量，显然 `线程安全`。 
- `StringBuffer` 对方法加了同步锁或者对调用的方法加了`同步锁`，所以是 `线程安全` 的。 
 
参考链接： 
http://www.cnblogs.com/xudong-bupt/p/3961159.html


<br>

---

#### `try catch finally` ，`try` 里有 `return` ，`finally` 还执行么 ?

A: `finally{}`在 `return` 中间执行。 `try{}` 中的 `return` 执行后在没有返回数据时先去执行 `finally{}` 中的代码，然后再返回。 

若 `try` 语句中有 `system.exit()` ，则不执行 `finally` 语句直接退出。




<br>

---

#### Collection包结构，与Collections的区别

- List： 
    - ArrayList 
    - LinkedList 
    - Vector 
- Stack（public class Stack<E> extends Vector<E>） 
- Set ： 
    - HashSet 
    - TreeSet 
- Queue: 
    - LinkedList 

Map 
    - HashMap 
    - HashTable 
    - TreeMap 

Collections是个java.util下的类，它包含有各种有关集合操作的静态方法。 
Collection是个java.util下的接口，它是各种集合结构的父接口。







<br>

---

#### `Map` 、`Set`、 `List`、 `Queue`、 `Stack` 的特点与用法 

1. `Map` 接口 

    请注意，`Map` 没有继承 `Collection` 接口，`Map` 提供key到value的映射。一个 `Map` 中不能包含相同的key，每个key只能映射一个 value。 `Map` 接口提供3种集合的视图， `Map` 的内容可以被当作一组key集合，一组value集合，或者一组key-value映射。 

2. `Set` 接口　　

    Set是一种不包含重复的元素的 `Collection`，即任意的两个元素 `e1` 和 `e2` 都有 `e1.equals(e2)=false`， `Set` 最多有一个 `null` 元素。 

3. `List` 接口 

    List是有序的 `Collection`，使用此接口能够精确的控制每个元素插入的位置。用户能够使用索引（元素在 `List` 中的位置，类似于数组下标）来访问 `List` 中的元素，这类似于 `Java` 的数组。 

4. `Stack` 类 

    `Stack` 继承自 `Vector`，实现一个后进先出的堆栈。 `Stack` 提供5个额外的方法使得 `Vector` 得以被当作堆栈使用。基本的 `push` 和 `pop` 方法，还有 `peek` 方法得到栈顶的元素， `empty` 方法测试堆栈是否为空，`search` 方法检测一个元素在堆栈中的位置。`Stack` 刚创建后是空栈。

参考链接： 
http://blog.csdn.net/zxfc88/article/details/8720854 




<br>

---

#### HashMap、HashTable、ConcurrentHashMap、TreeMap、LinkedHashMap 

`HashMap` 和 `HashTable` 的区别： 

1. 历史原因: `Hashtable` 是基于陈旧的 `Dictionary` 类的，`HashMap` 是 `Java 1.2` 引进的 `Map` 接口的一个实现 
2. 同步性: `Hashtable` 是线程安全的，也就是说是 `同步` 的，而 `HashMap` 是线程序不安全的，不是同步的 
3. 值：只有 `HashMap` 可以让你将 `null` 值作为一个表的条目的key或value 
 
`HashMap` 和 `ConcurrentHashMap` 的区别： 

- `HashMap` 非线程安全；
- `ConcurrentHashMap` 线程安全。 
 
`TreeMap`、 `HashMap`、 `LinkedHashMap` 的区别： 

HashMap:http://liujiacai.net/blog/2015/09/03/java-hashmap/ 

    public class HashMap<K,V> 
        extends AbstractMap<K,V> 
        implements Map<K,V>, Cloneable, Serializable 

    public abstract class AbstractMap<K,V> implements Map<K,V> 

    TreeMap:http://liujiacai.net/blog/2015/09/04/java-treemap/ 

    public class TreeMap<K,V> 
        extends AbstractMap<K,V> 
        implements NavigableMap<K,V>, Cloneable, java.io.Serializable 

    public interface NavigableMap<K,V> extends SortedMap<K,V> 
    public interface SortedMap<K,V> extends Map<K,V> 

    LinkedHashMap:http://liujiacai.net/blog/2015/09/12/java-linkedhashmap/ 
    
    public class LinkedHashMap<K,V> 
        extends HashMap<K,V> 
        implements Map<K,V> 






<br>

---

#### `final` 和 `static`

`final` —修饰符（关键字）

- 如果一个类被声明为final，意味着它不能再派生出新的子类，不能作为父类被继承。因此一个类不能既被声明为 abstract的，又被声明为final的。 
- 将变量或方法声明为final，可以保证它们在使用中不被改变。被声明为final的变量必须在声明时给定初值，而在以后的引用中只能读取，不可修改。被声明为final的方法也同样只能使用，不能重载。 

`static` —修饰符（关键字） 

- 被static修饰的成员变量和成员方法独立于该类的任何对象。也就是说，它不依赖类特定的实例，被类的所有实例共享。只要这个类被加载，Java虚拟机就能根据类名在运行时数据区的方法区内定找到他们。因此，static对象可以在它的任何对象创建之前访问，无需引用任何对象。 



`static` 变量与 `非staitc` 变量的区别： 

- 对于静态变量在内存中只有一个拷贝（节省内存），JVM只为静态分配一次内存，在加载类的过程中完成静态变量的内存分配，可用类名直接访问（方便），当然也可以通过对象来访问（但是这是不推荐的）。  
- 对于实例变量，每创建一个实例，就会为实例变量分配一次内存，实例变量可以在内存中有多个拷贝，互不影响（灵活）。 
- 静态方法：静态方法可以直接通过类名调用，任何的实例也都可以调用，因此静态方法中不能用this和super关键字，不能直接访问所属类的实例变量和实例方法(就是不带static的成员变量和成员成员方法)，只能访问所属类的静态成员变量和成员方法。






<br>

---

#### `Exception` 与 `Error` 包结构

    - Throwable
        - Exeception
            - RuntimeException
            - 非运行时异常
        - Error

在这里，RuntimeException和Error都属于Unchecked exception。 
参考链接：http://www.cnblogs.com/dolphin0520/p/3769804.html





<br>

---

#### `Java` 面向对象的三个特征与含义

- 封装(`encapsulation`)：对象的属性（私有要用get，set），方法声明，方法实现 
- 继承(`Inheritance`)：单继承，接口，访问权限，构造方法 
- 多态(`polymorphism`)：子类的对象放在父类的引用中 
 
参考链接： 
http://blog.sina.com.cn/s/blog_5f79a56a0100c6ig.html





<br>

---

#### `Override` 与 `Overload` 的含义与区别？

- override（重写，覆盖）

    1. 方法名、参数、返回值相同。
    2. 子类方法不能缩小父类方法的访问权限。
    3. 子类方法不能抛出比父类方法更多的异常(但子类方法可以不抛出异常)。
    4. 存在于父类和子类之间。
    5. 方法被定义为final不能被重写。

- overload（重载，过载）
    
    1. 参数类型、个数、顺序至少有一个不相同。
    2. 不能重载只有返回值不同的方法名。
    3. 存在于父类和子类、同类中。



<br>

---

#### `Interface` 与 `abstract` 类的区别？

1. `Java接口` 和 `Java抽象类` 最大的一个区别，就在于 `Java抽象类` 可以提供某些方法的部分实现，而 `Java接口` 不可以； 
2. 接口是公开的，里面不能有私有的方法或变量，是用于让别人使用的，而抽象类是可以有私有方法或私有变量的； 
3. 另外，实现接口的一定要实现接口里定义的所有方法，而实现抽象类可以有选择地重写需要用到的方法，一般的应用里，最顶级的是接口，然后是抽象类实现接口，最后才到具体类实现。



<br>

---

#### `Static class` 与 `non static class` 的区别

- Q: `Java` 中的类可以是 `static` 吗？

A: 答案是可以。在Java中我们可以有静态实例变量、静态方法、静态块。类也可以是静态的。 

- Java允许我们在一个类里面定义静态类。
    
    比如内部类（nested class）。把nested class封闭起来的类叫外部类。在java中，我们不能用static修饰顶级类（top level class）。只有内部类可以为static。 

- `静态内部类` 和 `非静态内部类` 之间到底有什么不同呢？下面是两者间主要的不同。 

    1. 内部静态类不需要有指向外部类的引用。但非静态内部类需要持有对外部类的引用。 
    2. 非静态内部类能够访问外部类的静态和非静态成员。静态类不能访问外部类的非静态成员。他只能访问外部类的静态成员。 
    3. 一个非静态内部类不能脱离外部类实体被创建，一个非静态内部类可以访问外部类的数据和方法，因为他就在外部类里面。





<br>

---

#### 实现多线程的两种方法: `Thread` 与 `Runnable`

在程序开发中只要是多线程肯定永远以实现Runnable接口为主，因为实现Runnable接口相比继承Thread类有如下好处： 

- 避免点继承的局限，一个类可以继承多个接口。 
- 适合于资源的共享 
- `Runnable接口` 和 `Thread` 之间的联系： `public class Thread extends Object implements Runnable`, 发现Thread类也是Runnable接口的子类。 
 
参考链接： 
http://developer.51cto.com/art/201203/321042.htm




<br>

---

#### 线程同步的方法：`synchronized`、`lock`、`reentrantLock` 等 

1. `Synchronized` 关键词：有 `synchronized` 关键字修饰的变量、方法，以及其修饰的代码块。 

2. 使用特殊域变量(`volatile` )实现线程同步： 

Java 语言提供了一种稍弱的同步机制,即 `volatile` 变量。 用来确保将变量的更新操作通知到其他线程,保证了新值能立即同步到主内存,以及每次使用前立即从主内存刷新. 当把变量声明为 `volatile类型` 后,编译器与运行时都会注意到这个变量是共享的。但是 `volatile变量` 并不是完全线程安全的。 

3. 使用`重入锁`实现线程同步 :

在 `JavaSE5.0` 中新增了一个 `java.util.concurrent` 包来支持同步。 `ReentrantLock类` 是可重入、互斥、实现了 `Lock接口` 的锁。 
需要注意的是，用 `sychronized` 修饰的方法或者语句块在代码执行完之后锁自动释放，而是用 `Lock` 需要我们手动释放锁，所以为了保证锁最终被释放(发生异常情况)，要把互斥区放在 `try` 内，释放锁放在 `finally` 内！！ 

`Lock` 的优势：`ReadWriteLock`，`读写锁`，`读共享`，`写互斥`。 
 
参考链接： 
http://blog.csdn.net/vking_wang/article/details/9952063 


















<br>

---

#### 锁的等级: `方法锁`、`对象锁`、`类锁`

假设我有一个类 `ClassA` ，其中有一个方法 `synchronized methodA()`，那么当这个方法被调用的时候你获得就是对象锁，但是要注意，如果这个类有两个实例，比如：

    ClassA a = new ClassA();
    ClassA b = new ClassA();

那么如果你在 `a` 这对象上调用了 `methodA()`，不会影响 `b` 这个对象，也就是说对于 `b` 这个对象，他也可以调用 `methodA`，因为这是两对象，所以说对象锁是针对对象的。 

而类锁，其实没有所谓的类锁，因为类锁实际上就是这个类的对象的对象锁，还是举例，我有一个类 `ClassA` ，其中有一个方法 `synchronized static methodA()` ，注意这个方法是静态的了，那就是说这个类的所有的对象都公用一个这个方法了，那如果你在这个类的某个对象上调用了这个方法，那么其他的对象如果想要用这个方法就得等着锁被释放，所以感觉就好像这个类被锁住了一样。














<br>

---

#### Concurrent包里的其他东西：ArrayBlockingQueue等 

1. `CountDownLatch`： 

- CountDownLatch类是一个同步计数器，构造时传入int参数,该参数就是计数器的初始值。 
- 每调用一次countDown()方法，计数器减1,计数器大于0 时，await()方法会阻塞程序继续执行 
- CountDownLatch如其所写，是一个倒计数的锁存器，当计数减至0时触发特定的事件。 

2. `LinkedBlockingQueue`： 

`LinkedBlockingQueue` 是一个链表实现的阻塞队列，在链表一头加入元素，如果队列满，就会阻塞，另一头取出元素，如果队列为空，就会阻塞。 

3. `ArrayBlockingQueue`： 

同 `LinkedBlockingQueue` ，其采用循环数组实现。 




<br>

---

#### `wait()` 与 `sleep()` 的区别

- `sleep()` 指线程被调用时，占着CPU不工作，形象地说明为“占着CPU睡觉”，此时，系统的CPU部分资源被占用，其他线程无法进入，会增加时间限制。 

- `wait()` 指线程处于进入等待状态，形象地说明为“等待使用CPU”，此时线程不占用任何资源，不增加时间限制。 
所以 

Examples:

    sleep（100L）意思为：占用CPU，线程休眠100毫秒 
    wait（100L）意思为：不占用CPU，线程等待100毫秒 





<br>

---

#### `ThreadLocal` 的设计理念与作用 

1. `ThreadLocal` 为解决多线程程序的并发问题提供了一种新的思路:
    
    当使用 `ThreadLocal` 维护变量时，`ThreadLocal` 为每个使用该变量的线程提供独立的变量副本，所以每一个线程都可以独立地改变自己的副本，而不会影响其它线程所对应的副本。 

2. `ThreadLocal` 和 `线程同步机制` 相比有什么优势呢？

    - `ThreadLocal` 和 `线程同步机制` 都是为了解决多线程中相同变量的访问冲突问题。 
    
    - 在同步机制中，通过 `对象的锁机制`保证同一时间只有一个线程访问变量。这时该变量是多个线程共享的，使用`同步机制` 要求程序慎密地分析什么时候对变量进行读写，什么时候需要锁定某个对象，什么时候释放对象锁等繁杂的问题，程序设计和编写难度相对较大。 

    - 而 `ThreadLocal` 则从另一个角度来解决多线程的并发访问。 `ThreadLocal` 会为每一个线程提供一个独立的变量副本，从而隔离了多个线程对数据的访问冲突。因为每一个线程都拥有自己的变量副本，从而也就没有必要对该变量进行同步了。`ThreadLocal` 提供了线程安全的共享对象，在编写多线程代码时，可以把不安全的变量封装进 `ThreadLocal`。 
 
参考链接： 
http://blog.csdn.net/lufeng20/article/details/24314381 








<br>

---

#### `ThreadPool` 用法与优势

- 如果并发的线程数量很多，并且每个线程都是执行一个时间很短的任务就结束了，这样频繁创建线程就会大大降低系统的效率，因为频繁创建线程和销毁线程需要时间。
- 那么有没有一种办法使得线程可以复用，就是执行完一个任务，并不被销毁，而是可以继续执行其他的任务？在Java中可以通过线程池来达到这样的效果。 
- Java中的实现：`ThreadPoolExecutor` 

源码解析：http://www.importnew.com/16797.html 
在java doc中，并不提倡我们直接使用ThreadPoolExecutor，而是使用Executors类中提供的几个静态方法来创建线程池。

参考链接：http://www.cnblogs.com/dolphin0520/p/3932921.html 






<br>

---

#### `foreach` 与 正常 `for` 循环效率对比

- 使用for，更高效率。
- 使用foreach，更安全。

- 那么如何选择呢？我的建议是，在一些全局的，多线程可以访问的数据结构对象，使用foreach。而对本地变量，则使用for，效率和安全兼顾！ 
 
参考链接： 
http://flyvszhb.iteye.com/blog/2163569





<br>

---

#### 反射的作用与原理

1. 概念： 

    `JAVA反射机制` 是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种`动态获取的信息`以及`动态调用对象的方法`的功能称为Java语言的反射机制。 

2. 作用： 

    - 它使类和数据结构能按名称动态检索相关信息，并允许在运行着的程序中操作这些信息。 
    - 增加程序的灵活性。如struts中。请求的派发控制。当请求来到时。struts通过查询配置文件。找到该请求对应的action。然后通过反射实例化action。并调用响应method。如果不适用反射，那么你就只能写死到代码里了。 
 
参考链接： 
http://blog.csdn.net/cnham/article/details/3086038






<br>

---

#### 泛型常用特点，List<String>能否转为List<Object> 

`Java` 用 `type erasure` 实现泛型，在编译时，只会生成 `List.class`，不带类型，只有在使用时，才会做类型的转换。 
`covariant contravariant`，`Java` 中除了 `Array` 是 `covariant` 的，其他都是 `invariant`，所以 `List<String>` 不能转为 `List<Object>`。





<br>

---

#### `Java IO` 与 `NIO`

- `面向流` 与 `面向缓冲`

    最大的区别是 `IO` ssssssssss是面向流与 `NIO` 是面向缓冲的；

- `阻塞IO` 与 `非阻塞IO`

    Java IO的各种流是阻塞的。这意味着，当一个线程调用 `read()` 或 `write()` 时，该线程被阻塞，直到有一些数据被读取，或数据完全写入。该线程在此期间不能再干任何事情了。Java `NIO的非阻塞模式`，使一个线程从某通道发送请求读取数据，但是它仅能得到目前可用的数据，如果目前没有数据可用时，就什么都不会获取。而不是保持线程阻塞，所以直至数据变的可以读取之前，该线程可以继续做其他的事情。 
    
- 选择器（Selectors） 

    Java NIO的选择器允许一个单独的线程来监视多个输入通道，你可以注册多个通道使用一个选择器，然后使用一个单独的线程来“选择”通道：这些通道里已经有可以处理的输入，或者选择已准备写入的通道。这种选择机制，使得一个单独的线程很容易来管理多个通道。 
 
参考链接： 
http://www.jb51.net/article/50621.htm






<br>

---

#### `JNI` 的使用

`Java` 通过 `JNI` 调用 `本地方法`，而本地方法是以库文件的形式存放的（在Windows平台下是DLL文件形式，在UNIX机器上是SO文件形式）。通过调用本地的库文件的内部方法，使Java可以实现和本地机器的紧密联系，调用系统级的各接口方法 
 
参考链接： 
http://blog.csdn.net/kai_wei_zhang/article/details/8118842






<br>

---

#### 设计模式： 单例、工厂、适配器、责任链、观察者等等

单例：只能有一个实例，构造函数为private，类提供一个方法 








<br>

---

#### 黑盒测试、白盒测试、单元测试

- 黑盒测试

    黑盒测试也称 `功能测试` 或 `数据驱动测试`，它是在已知产品所应具有的功能，通过测试来检测每个功能是否都能正常使用，在测试时，把程序看作一个不能打开的黑盆子，在完全不考虑程序内部结构和内部特性的情况下，测试者在程序接口进行测试，它只检查程序功能是否按照需求规格说明书的规定正常使用，程序是否能适当地接收输入数锯而产生正确的输出信息，并且保持外部信息（如数据库或文件）的完整性。 
 
    黑盒测试方法主要有 `等价类划分`、`边值分析`、`因—果图`、`错误推测` 等，主要用于软件确认测试。
    
    “黑盒”法着眼于程序外部结构、不考虑内部逻辑结构、针对软件界面和软件功能进行测试。“黑盒”法是穷举输入测试，只有把所有可能的输入都作为测试情况使用，才能以这种方法查出程序中所有的错误。实际上测试情况有无穷多个，人们不仅要测试所有合法的输入，而且还要对那些不合法但是可能的输入进行测试。 
 
- 白盒测试

    `白盒测试` 也称 `结构测试` 或 `逻辑驱动测试`，它是知道产品内部工作过程，可通过测试来检测产品内部动作是否按照规格说明书的规定正常进行，按照程序内部的结构测试程序，检验程序中的每条通路是否都有能按预定要求正确工作，而不顾它的功能，白盒测试的主要方法有`逻辑驱动`、`基路测试`等，主要用于软件验证。 
 
 
参考链接： 
http://blog.csdn.net/success0123/article/details/1603837 
 
单元测试（unit testing），是指对软件中的最小可测试单元进行检查和验证。对于单元测试中单元的含义，一般来说，要根据实际情况去判定其具体含义，如C语言中单元指一个函数，Java里单元指一个类，图形化的软件中可以指一个窗口或一个菜单等。总的来说，单元就是人为规定的最小的被测功能模块。单元测试是在软件开发过程中要进行的最低级别的测试活动，软件的独立单元将在与程序的其他部分相隔离的情况下进行测试。 














<br>

---

#### `Java` 内部类

- Java内部类分为： 

    - 成员内部类
    - 静态嵌套类
    - 方法内部类
    - 匿名内部类 
 
- 为什么使用内部类： 

    内部类可以随意使用外部类的成员变量（包括私有）而不用生成外部类的对象。 
每个内部类都能独立地继承自一个（接口的）实现，所以无论外围类是否已经继承了某个（接口的）实现，对于内部类都没有影响。如果没有内部类提供的可以继承多个具体的或抽象的类的能力，一些设计与编程问题就很难解决。从这个角度看，内部类使得多重继承的解决方案变得完整。接口解决了部分问题，而内部类有效地实现了“多重继承”。














<br>

---

#### `Java` 序列化

- 什么是序列化： 

    - Java平台允许我们在内存中创建可复用的Java对象，但一般情况下，只有当 `JVM` 处于运行时，这些对象才可能存在，即，这些对象的生命周期不会比 `JVM` 的生命周期更长。
    - 但在现实应用中，就可能要求在 `JVM` 停止运行之后能够保存(持久化)指定的对象，并在将来重新读取被保存的对象。
    - Java对象序列化就能够帮助我们实现该功能。
    - 使用Java对象序列化，在保存对象时，会把其状态保存为一组字节，在未来，再将这些字节组装成对象。
    - 必须注意地是，对象序列化保存的是对象的"状态"，即它的成员变量。
    - 由此可知，对象序列化不会关注类中的静态变量。 
    - 除了在持久化对象时会用到对象序列化之外，当使用RMI(远程方法调用)，或在网络中传递对象时，都会用到对象序列化。     - Java序列化API为处理对象序列化提供了一个标准机制，该API简单易用，在本文的后续章节中将会陆续讲到。 
    - 只要一个类实现了java.io.Serializable接口，那么它就可以被序列化 
 
参考文献： 
http://developer.51cto.com/art/201202/317181.htm
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

