在位于不同地理位置的网络中的两个主机系统之间提供连接和路径选择。Internet的发展使得从世界各站点访问信息的用户数大大增加，而网络层正是管理这种连接的层。

# 面经知识点整合

## JAVA基础知识

### 1、面向对象的特性

**类**：一组相关属性和行为的集合。可以看成是一类事物的模板，使用事物的属性特征和行为特征来描述该类事物。

**对象**：一类事物的具体体现。

类是对一类事物的描述，是抽象的。
对象是一类事物的实例，是具体的。
类是对象的模板，对象是类的实体。 

- **继承**：从已有类得到继承信息并创建新类的过程，继承是封装程序中可变因素的重要手段，提高代码的复用性，是多态的前提。

- **封装**：将数据与操作数据的方法绑定起来，对数据的访问只能通过已定义的接口，使用private将属性隐藏起来，若需要访问某个属性，提供公共方法对其访问。

- **多态**： 多态是同一个行为具有多个不同表现形式或形态的能力，同一个接口，使用不同的实例而执行不同操作。引用类型转换：1、向上类型转换（隐式）2、向下类型转换（强制类型转换）,instanceof运算符，来解决引用对象的类型，避免类型转换的安全性问题。

  成员变量，编译看左边（基类），运行看左边（基类）；无论如何都是访问基类的成员变量。

  成员方法，编译看左边（基类），运行看右边（派生类），动态绑定。

  Static方法,编译看左边（基类），运行看左边（基类）。

  只有非静态的成员方法,编译看左边,运行看右边。

  这样，我们也可以得出多态的局限：不能使用派生类特有的成员属性和派生类特有的成员方法。

  多态存在的三个必要条件:继承、重写、父类引用指向子类对象。

- **抽象**：将一类对象的共同特征总结出来构造类的过程，包括数据抽象和行为抽象，抽象只关注有哪些共同的属性和行为，不关注该行为的具体实现。

**重载和重写**:方法的重载和重写都是实现多态的方式，区别在于前者实现的是编译时的多态性，而后者实现的是运行时的多态性。重载发生在一个类中，同名的方法如果有不同的参数列表（参数类型不同、参数个数不同或者二者都不同）则视为重载；重写发生在子类与父类之间，重写要求子类被重写方法与父类被重写方法有相同的返回类型，比父类被重写方法更好访问，不能比父类被重写方法声明更多的异常（里氏代换原则）。重载对返回类型没有特殊的要求。 

#### 面向对象的"六原则一法则"

\- 单一职责原则：一个类只做它该做的事情。

\- 开闭原则：软件实体应当对扩展开放，对修改关闭。

\- 依赖倒转原则：面向接口编程。（该原则说得直白和具体一些就是声明方法的参数类型、方法的返回类型、变量的引用类型时，尽可能使用抽象类型而不用具体类型，因为抽象类型可以被它的任何一个子类型所替代，请参考下面的里氏替换原则。）

\- 接口隔离原则：接口要小而专，绝不能大而全。

\- 里氏替换原则：任何时候都可以用子类型替换掉父类型。

\- 合成聚合复用原则：优先使用聚合或合成关系复用代码。

\- 迪米特法则：迪米特法则又叫最少知识原则，一个对象应当对其他对象有尽可能少的了解。

### 2、接口与抽象类的联系与区别

**抽象类**：
（1）一个类中有抽象方法，这个类就变成了抽象类。
（2）抽象类中class的前面必须有abstract修饰符。
（3）抽象类中可以有普通方法，也可以有抽象方法，而抽象方法的个数可以是0个，也可以是多个。
（4）子类继承父类，必须重写全部的抽象方法，除非这个类也变成了抽象类。

**接口**：
（1）表面上看，接口是一种特殊的抽象类，但是类是类，接口是接口，是并列的关系。
（2）接口中所有方法都必须是抽象的。
（3）接口中方法定义默认为public abstract类型，成员变量默认为public static final 类型。（如果省略，系统会默认补全）。

##### 为什么接口不能有变量

> 1. 首先接口由于少了方法的实现，所以不能实例化，这个与抽象类一致，
> 2. 由于不能实例化，所以对于成员变量只能是static
> 3. 由于是static所以所有实现了接口的类共享一份
> 4. 由于所有人共享一份，同时接口的定义是“所有实现该接口的人都共同拥有这些属性/功能”
> 5. 由于所有的实现类都共同拥有，若是变量则实现类A的改变会导致实现类B的改变
> 6. 会由于实现类的操作而改变的东西违反了接口的定义
> 7. 所以为了确保每个实现的接口都共同遵守这个“属性”，属性必须是final
> 8. 由于接口本身的定义是public
> 9. 最后就是 public static final xxx
> 10. 而抽象类属于类，只能单继承不会存在上述问题

**区别主要体现在**：

抽象类中可以含有成员变量、构造函数、静态方法、普通函数，而接口中不能出现，在访问权限方面抽象类可以为public、protect而接口只能是public。抽象类由extends实现，接口由implements实现。

Java提供和支持创建抽象类和接口。它们的实现有共同点，不同点在于：
接口中所有的方法隐含的都是抽象的。而抽象类则可以同时包含抽象和非抽象的方法。
类可以实现很多个接口，但是只能继承一个抽象类
类可以不实现抽象类和接口声明的所有方法，当然，在这种情况下，类也必须得声明成是抽象的。
抽象类可以在不提供接口方法实现的情况下实现接口。
Java接口中声明的变量默认都是final的。抽象类可以包含非final的变量。
Java接口中的成员函数默认是public的。抽象类的成员函数可以是private，protected或者是public。
接口是绝对抽象的，不可以被实例化。抽象类也不可以被实例化，但是，如果它包含main方法的话是可以被调用的。

### 3、关键字

**final:** 修饰的变量不可修改(基本类型值不能修改，引用类型引用不可修改)，final修饰的方法，不可重写、不可继承 。

**static:**修饰的变量被所有类实例共享，静态变量在其所在类被加载时进行初始化，静态方法中不能引用非静态变量或函数。

**native:**修饰的方法是一个原生态方法，方法对应的实现不是在当前文件，而是在用其他语言（如C和C++）实现的文件中。Java不是完美的，Java的不足除了体现在运行速度上要比传统的C++慢许多之外，Java语言本身不能对操作系统底层进行访问和操作（如系统硬件等)，因此Java使用native方法来扩展Java程序的功能，通过JNI接口调用其他语言来实现对底层的访问。

**volatile:** 修饰的成员变量在每次被线程访问时，都从主内存中重新读取该成员变量的值。而且，当成员变量发生变化时，强迫线程将变化值回写到主内存 。在指令优化时，禁止指令重排 。

**synchronized:** 用于代码同步，用于控制多线程同步访问同一变量或方法 。

**类锁**： 当 synchronized 修饰静态方法或 synchronized 修饰代码块时传入某个class对象（synchronized (XXXX.class)）时被称为类锁。某个线程得到了一个类锁之后，其他所有被该类锁加锁方法或代码块是锁定的， 其他线程是无法访问的，但是其他线程还是可以访问没有被该类锁加锁的任何代码。

**对象锁**： 当 synchronized 修饰非静态方法或 synchronized 修饰代码块时传入非class对象（synchronized this)）时被称为对象锁。某个线程得到了对象锁之后，该对象的其他被 synchronized修饰的方法（同步方法）是锁定的，其他线程是无法访问的。但是其他线程还是可以访问没有进行同步的方法或者代码；当获取到与对象关联的内置锁时，并不能阻止其他线程访问该对象，当某个线程获得对象的锁 之后，只能阻止其他线程获得同一个锁。

**类锁和对象锁的关系**： 如同每个类只有一个class对象而类的实例可以有很多个一样，每个类只有一个类锁，每个实例都有自己的对象锁，所以不同对象实例的对象锁是互不干扰的。但是有一点必须注意的是，其实类锁只是一个概念上的东西，并不是真实存在的，它只是用来帮助我们理解锁定实例方法和静态方法的区别的。类锁和对象锁是不一样的锁，是互相独立的，两者不存在竞争关系，线程获得对象锁的同时，也可以获得该类锁，即同时获得两个锁，这是允许的。

 **其他特性**： 因为被 synchronized 修饰的代码在同一时刻只有一个线程执行，所以也就保证了操作的 原子性和内存可见性。

### 4、泛型

“泛型” 意味着编写的代码可以被不同类型的对象所重用。泛型的提出是为了编写重用性更好的代码。泛型的本质是参数化类型，也就是说所操作的数据类型被指定为一个参数。 

### 5、String特性

**不可变**对象是指一个对象的状态在对象被创建之后就不再变化。不可改变的意思就是说：不能改变对象内的成员变量，包括基本数据类型的值不能改变，引用类型的变量不能指向其他的对象，引用类型指向的对象的状态也不能改变。

String 不可变是因为在 JDK 中 String 类被声明为一个 final 类，且类内部的 value 字节数组也是 final 的，只有当字符串是不可变时字符串池才有可能实现，字符串池的实现可以在运行时节约很多 heap 空间，因为不同的字符串变量都指向池中的同一个字符串；如果字符串是可变的则会引起很严重的安全问题，譬如数据库的用户名密码都是以字符串的形式传入来获得数据库的连接，或者在 socket 编程中主机名和端口都是以字符串的形式传入，因为字符串是不可变的，所以它的值是不可改变的，否则黑客们可以钻到空子改变字符串指向的对象的值造成安全漏洞；因为字符串是不可变的，所以是多线程安全的，同一个字符串实例可以被多个线程共享，这样便不用因为线程安全问题而使用同步，字符串自己便是线程安全的；因为字符串是不可变的所以在它创建的时候 hashcode 就被缓存了，不变性也保证了 hash 码的唯一性，不需要重新计算，这就使得字符串很适合作为 Map 的键，字符串的处理速度要快过其它的键对象，这就是 HashMap 中的键往往都使用字符串的原因。

### 6、列举你所知道的Object类的方法并简要说明

Object()默认构造方法。

clone() 创建并返回此对象的一个副本。

equals(Object obj) 指示某个其他对象是否与此对象“相等”。

finalize()当垃圾回收器确定不存在对该对象的更多引用时，由对象的垃圾回收器调用此方法。

getClass()返回一个对象的运行时类。

hashCode()返回该对象的哈希码值。 

notify()唤醒在此对象监视器上等待的单个线程。 

notifyAll()唤醒在此对象监视器上等待的所有线程。

toString()返回该对象的字符串表示。

wait()导致当前的线程等待，直到其他线程调用此对象的 notify() 方法或 notifyAll() 方法。wait(long timeout)导致当前的线程等待，直到其他线程调用此对象的 notify() 方法或 notifyAll() 方法，或者超过指定的时间量。

wait(long timeout, int nanos) 导致当前的线程等待，直到其他线程调用此对象的 notify() 方法或 notifyAll() 方法，或者其他某个线程中断当前线程，或者已超过某个实际时间量。 

### 7、重写不能比父类被重写方法声明更多的异常

举例说明：有一份工作交由父类完成，因为父类可能出现异常，所以在该工作中，声明捕获该异常。现在子类继承父类，子类对象当然可以从事父类的工作，而如果子类能够出现比父类更多的异常的话，该工作无法捕获，出现问题。

### 8、父类静态方法不可以被子类继承和重写（覆盖）

Java里不管是static方法还是final方法不是不能被覆盖的，那为什么在子类写一个和父类同名的静态方法不会报错，而写一个同名的final方法分分钟报错给你看？其实final修饰的不管是普通方法还是静态方法，子类中都不允许由同名的方法，这是规定。那子类里的为什么可以有重名的静态方法，可以把它理解为重新定义，，静态方法是在类加载时就和类绑定在一起，是静态绑定，子类有同名的静态方法，就是在加载子类的同名静态方法时重新分配一块空间，和父类的静态方法没有任何关系！[ADDR][1]

[1]: https://blog.csdn.net/qq_34826261/article/details/101039492

### Map的遍历

```java
for(Map.Entry<String, String> entry : map.entrySet()){
    String mapKey = entry.getKey();
    String mapValue = entry.getValue();
    ......
}
```

```java
//key
for(String key : map.keySet()){
    ......
}
//value
for(String value : map.values()){
    ......
}
```

```java
Iterator<Entry<String, String>> entries = map.entrySet().iterator();
while(entries.hasNext()){
    ......
}
```

Hashmap基于数组实现的，通过对key的hashcode & 数组的长度得到在数组中位置，如当前数组有元素，则数组当前元素next指向要插入的元素，这样来解决hash冲突的，形成了拉链式的结构。put时在多线程情况下，会形成环从而导致死循环。数组长度一般是2n，从0开始编号，所以hashcode & （2n-1），（2n-1）每一位都是1，这样会让散列均匀。需要注意的是，HashMap在JDK1.8的版本中引入了红黑树结构做优化，当链表元素个数大于等于8时，链表转换成树结构；若桶中链表元素个数小于等于6时，树结构还原成链表。因为红黑树的平均查找长度是log(n)，长度为8的时候，平均查找长度为3，如果继续使用链表，平均查找长度为8/2=4，这才有转换为树的必要。链表长度如果是小于等于6，6/2=3，虽然速度也很快的，但是转化为树结构和生成树的时间并不会太短。还有选择6和8，中间有个差值7可以有效防止链表和树频繁转换。假设一下，如果设计成链表个数超过8则链表转换成树结构，链表个数小于8则树结构转换成链表，如果一个HashMap不停的插入、删除元素，链表个数在8左右徘徊，就会频繁的发生树转链表、链表转树，效率会很低。 

### 集合

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200405150206772.png" alt="image-20200405150206772" style="zoom:50%;" />

- LinkedList源码分析总结

  > LinkedList 是一个继承于AbstractSequentialList的双向链表。它也可以被当作堆栈、队列或双端队列进行操作。有关索引的操作可能从链表头开始遍历到链表尾部，也可能从尾部遍历到链表头部，这取决于看索引更靠近哪一端。
  > LinkedList 实现 List 接口，能对它进行队列操作。
  > LinkedList 实现 Deque 接口，即能将LinkedList当作双端队列使用。
  > LinkedList 实现了Cloneable接口，即覆盖了函数clone()，能克隆。
  > LinkedList 实现java.io.Serializable接口，这意味着LinkedList支持序列化，能通过序列化去传输。
  > LinkedList 是非同步的。
  >
  > LinkedList的clone方法为浅拷贝，将first、last赋值为null，使用被拷贝的List的元素进行复制，即first、last为独立的，其他元素共享，若为引用，则改变一方、另一方也会被改变。

- ArrayList源码分析总结

  > ArrayList的扩容机制：判断添加一个元素是否会导致数组溢出 ，若溢出则进入扩容步骤，正常情况下型数组大小为旧数组的1.5倍，若容量oldcapacity*1.5 -  MAX_ARRAY_SIZE > 0  (MAX_ARRAY_SIZE = Integer.MAX_VALUE - 8)，进入数组最大容量判断：
  >
  > ```java
  > private static int hugeCapacity(int minCapacity) {
  >         if (minCapacity < 0) // overflow
  >             throw new OutOfMemoryError();
  >         return (minCapacity > MAX_ARRAY_SIZE) ? Integer.MAX_VALUE : MAX_ARRAY_SIZE;
  > }
  > ```
  >
  > MAX_ARRAY_SIZE的定义是因为：一些虚拟机在数组中保留一些标题字。

对于随机访问get和set，ArrayList觉得优于LinkedList，因为LinkedList要移动指针；对于新增和删除操作add和remove，LinedList比较占优势，因为ArrayList要移动数据。 

### 并发

#### 1、并发编程三要素（线程的安全性问题体现在）：

原子性：原子，即一个不可再被分割的颗粒。原子性指的是一个或多个操作要么全部执行成功要么全部执行失败。

可见性：一个线程对共享变量的修改,另一个线程能够立刻看到。（synchronized,volatile）

有序性：程序执行的顺序按照代码的先后顺序执行。（处理器可能会对指令进行重排序）                                                     

#### 2、创建线程的四种方式：*

继承Thread类、实现Runnable接口、实现Callable接口、使用Executors工具类创建线程池。

为什么我们调用 start() 方法时会执行 run() 方法，不能直接调用 run() 方法:
new 一个 Thread，线程进入了新建状态。调用 start() 方法，会启动一个线程并使线程进入了就绪状态，当分配到时间片后就可以开始运行了。 start() 会执行线程的相应准备工作，然后自动执行 run() 方法的内容，这是真正的多线程工作。而直接执行 run() 方法，会把 run 方法当成一个 main 线程下的普通方法去执行，并不会在某个线程中执行它，所以这并不是多线程工作。

#### 3、synchronized 和 Lock 有什么区别？

- synchronized是Java内置关键字，在JVM层面；Lock是一个类。
- synchronized可以给类、方法、代码块加锁；Lock只能给代码块加锁。
- 在发生异常情况时，syschronized不需要手动的获取或释放锁，不会发生死锁；Lock需要手动处理异常情况，释放锁，以此来避免死锁。
- synchronized无法知道有没有获得锁；通过Lock可以知道有没有成功获得锁。

#### 4、synchronized 和 ReentrantLock 区别是什么？

synchronized 是和 if、else、for、while 一样的关键字，ReentrantLock 是类，这是二者的本质区别。既然 ReentrantLock 是类，那么它就提供了比synchronized 更多更灵活的特性，可以被继承、可以有方法、可以有各种各样的类变量。

两者都是可重入锁。“可重入锁”概念是：自己可以再次获取自己的内部锁。比如一个线程获得了某个对象的锁，此时这个对象锁还没有释放，当其再次想要获取这个对象的锁的时候还是可以获取的，如果不可锁重入的话，就会造成死锁。同一个线程每次获取锁，锁的计数器都自增1，所以要等到锁的计数器下降为0时才能释放锁。

主要区别如下：

ReentrantLock 使用起来比较灵活，但是必须有释放锁的配合动作；
ReentrantLock 必须手动获取与释放锁，而 synchronized 不需要手动释放和开启锁；
ReentrantLock 只适用于代码块锁，而 synchronized 可以修饰类、方法、变量等。
二者的锁机制其实也是不一样的。ReentrantLock 底层调用的是 Unsafe 的park 方法加锁，synchronized 操作的应该是对象头中 mark word
Java中每一个对象都可以作为锁，这是synchronized实现同步的基础：

普通同步方法，锁是当前实例对象；静态同步方法，锁是当前类的class对象；同步方法块，锁是括号里面的对象。

#### 5、synchronized 和 volatile 的区别是什么？

synchronized 表示只有一个线程可以获取作用对象的锁，执行代码，阻塞其他线程。

volatile 表示变量在 CPU 的寄存器中是不确定的，必须从主存中读取。保证多线程环境下变量的可见性；禁止指令重排序。

区别：

volatile 是变量修饰符；synchronized 可以修饰类、方法、变量。

volatile 仅能实现变量的修改可见性，不能保证原子性；而 synchronized 则可以保证变量的修改可见性和原子性。

volatile 不会造成线程的阻塞；synchronized 可能会造成线程的阻塞。

volatile标记的变量不会被编译器优化；synchronized标记的变量可以被编译器优化。

volatile关键字是线程同步的轻量级实现，所以volatile性能肯定比synchronized关键字要好。但是volatile关键字只能用于变量而synchronized关键字可以修饰方法以及代码块。

锁共有4种状态，级别从低到高依次为：无状态锁，偏向锁，轻量级锁和重量级锁状态。

#### 6、自旋锁、互斥锁

自旋锁的定义：当一个线程尝试去获取某一把锁的时候，如果这个锁此时已经被别人获取(占用)，那么此线程就无法获取到这把锁，该线程将会等待，间隔一段时间后会再次尝试获取。这种采用循环加锁 -> 等待的机制被称为自旋锁。 

原理：自旋锁的原理比较简单，如果持有锁的线程能在短时间内释放锁资源，那么那些等待竞争锁的线程就不需要做内核态和用户态之间的切换进入阻塞状态，它们只需要等一等(自旋)，等到持有锁的线程释放锁之后即可获取，这样就避免了用户进程和内核切换的消耗。因为自旋锁避免了操作系统进程调度和线程切换，所以自旋锁通常适用在时间比较短的情况下。由于这个原因，操作系统的内核经常使用自旋锁。但是，如果长时间上锁的话，自旋锁会非常耗费性能，它阻止了其他线程的运行和调度。线程持有锁的时间越长，则持有该锁的线程将被 `OS(Operating System)` 调度程序中断的风险越大。如果发生中断情况，那么其他线程将保持旋转状态(反复尝试获取锁)，而持有该锁的线程并不打算释放锁，这样导致的是结果是无限期推迟，直到持有锁的线程可以完成并释放它为止。

自旋锁的优缺点：自旋锁尽可能的减少线程的阻塞，这对于锁的竞争不激烈，且占用锁时间非常短的代码块来说性能能大幅度的提升，因为自旋的消耗会小于线程阻塞挂起再唤醒的操作的消耗，这些操作会导致线程发生两次上下文切换！但是如果锁的竞争激烈，或者持有锁的线程需要长时间占用锁执行同步块，这时候就不适合使用自旋锁了，因为自旋锁在获取锁前一直都是占用 cpu 做无用功，占着 XX 不 XX，同时有大量线程在竞争一个锁，会导致获取锁的时间很长，线程自旋的消耗大于线程阻塞挂起操作的消耗，其它需要 cpu 的线程又不能获取到 cpu，造成 cpu 的浪费。所以这种情况下我们要关闭自旋锁。

互斥锁：保证在同一时刻只能有一个线程访问对象，同一线程多次加锁会造成死锁。

#### 7、线程池

线程池就是提前创建若干个线程，如果有任务需要处理，线程池里的线程就会处理任务，处理完之后线程并不会被销毁，而是等待下一个任务。由于创建和销毁线程都是消耗系统资源的，所以当你想要频繁的创建和销毁线程的时候就可以考虑使用线程池来提升系统的性能。 

- 线程池的优势

  (1)降低系统资源消耗，通过重用已存在的线程，降低线程创建和销毁造成的消耗；

  (2)提高系统响应速度，当有任务到达时，通过复用已存在的线程，无需等待新线程的创建便能立即执行；

  (3)方便线程并发数的管控。因为线程若是无限制的创建，可能会导致内存占用过多而产生OOM，并且会造成cpu过度切换（cpu切换线程是有时间成本的（需要保持当前执行线程的现场，并恢复要执行线程的现场））。

  (4)提供更强大的功能，延时定时线程池。

- 线程池的种类 

  <img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200415184639533.png" alt="image-20200415184639533" style="zoom:67%;" />

  1、newCachedThreadPool：用来创建一个可以无限扩大的线程池，适用于负载较轻的场景，执行短期异步任务。（可以使得任务快速得到执行，因为任务时间执行短，可以很快结束，也不会造成cpu过度切换）

  2、newFixedThreadPool：创建一个固定大小的线程池，因为采用无界的阻塞队列，所以实际线程数量永远不会变化，适用于负载较重的场景，对当前线程数量进行限制。（保证线程数可控，不会造成线程过多，导致系统负载更为严重）

  3、newSingleThreadExecutor：创建一个单线程的线程池，适用于需要保证顺序执行各个任务。

  4、newScheduledThreadPool：适用于执行延时或者周期性任务。

#### 8、CountDownLatch和CyclicBarrier的理解和区别*

从字面上理解，CountDown表示减法计数，Latch表示门闩的意思，计数为0的时候就可以打开门闩了。Cyclic Barrier表示循环的障碍物。两个类都含有这一个意思：对应的线程都完成工作之后再进行下一步动作，也就是大家都准备好之后再进行下一步。然而两者最大的区别是，进行下一步动作的动作实施者是不一样的。这里的“动作实施者”有两种，一种是主线程（即执行main函数），另一种是执行任务的其他线程，后面叫这种线程为“其他线程”，区分于主线程。对于CountDownLatch，当计数为0的时候，下一步的动作实施者是main函数；对于CyclicBarrier，下一步动作实施者是“其他线程”。

### 异常

#### 1、Error 和 Exception 区别是什么？
Error 类型的错误通常为虚拟机相关错误，如系统崩溃，内存不足，堆栈溢出等，编译器不会对这类错误进行检测，JAVA 应用程序也不应对这类错误进行捕获，一旦这类错误发生，通常应用程序会被终止，仅靠应用程序本身无法恢复。

Exception 类的错误是可以在应用程序中进行捕获并处理的，通常遇到这种错误，应对其进行处理，使应用程序可以继续正常运行。

即使 catch 中包含了 return 语句，finally 子句依然会执行；若 finally 中也包含 return 语句，finally 中的 return 会覆盖前面的 return.。

#### 2、JVM 是如何处理异常的？
在一个方法中如果发生异常，这个方法会创建一个异常对象，并转交给 JVM，该异常对象包含异常名称，异常描述以及异常发生时应用程序的状态。创建异常对象并转交给 JVM 的过程称为抛出异常。可能有一系列的方法调用，最终才进入抛出异常的方法，这一系列方法调用的有序列表叫做调用栈。

JVM 会顺着调用栈去查找看是否有可以处理异常的代码，如果有，则调用异常处理代码。当 JVM 发现可以处理异常的代码时，会把发生的异常传递给它。如果 JVM 没有找到可以处理该异常的代码块，JVM 就会将该异常转交给默认的异常处理器（默认处理器为 JVM 的一部分），默认异常处理器打印出异常信息并终止应用程序。

### 反射

#### 通过反射机制获取类的私有变量、方法

```java
public class ListNode {
    private int a = 100;
    ListNode() {
    }

    private ListNode(int x) {
        a = x;
    }
    
    private void out_put(String str){
        System.out.println(str);
    }
}

public class try_test {
    public static void main(String[] args) throws NoSuchFieldException, IllegalAccessException {
        Class<?> clazz = Class.forName("test.ListNode");
        //Class<?> clazz = ListNode.class;
        Object object = clazz.newInstance();//newInstance只能调用无参构造函数
        //getDeclaredConstructor可以获取私有含参构造函数\getConstructor只能获取共有构造函数
        Constructor constructor = clazz.getDeclaredConstructor(int.class);
        constructor.setAccessible(true);
        Object object2 = constructor.newInstance(1);
        Field field = clazz.getDeclaredField("a");
        field.setAccessible(true);
        System.out.println(field.get(object));//100  //1
        field.set(object/object2,200);
        System.out.println(field.get(object));//200  //200
        
        Method method = clazz.getDeclaredMethod("out_put", String.class);
        method.setAccessible(true);
        method.invoke(object, "反射调用！");//反射调用！
    }
}
```

```java
Method getDeclaredMethod(String name, Class… parameterTypes)
//返回一个 Method 对象，该对象反映此 Class 对象所表示的类或接口的指定已声明方法。 
Method[] getDeclaredMethods() 
//返回 Method 对象的一个数组，这些对象反映此 Class 对象表示的类或接口声明的所有方法，包括公共、保护、默认（包）访问和私有方法，但不包括继承的方法。 
Method getMethod(String name, Class… parameterTypes) 
//返回一个 Method 对象，它反映此 Class 对象所表示的类或接口的指定公共成员方法。 
Method[] getMethods() 
//返回一个包含某些 Method 对象的数组，这些对象反映此 Class 对象所表示的类或接口（包括那些由该类或接口声明的以及从超类和超接口继承的那些的类或接口）的公共 member 方法。 
getDeclaredField(String name) 
//返回一个 Field 对象，该对象反映此 Class 对象所表示的类或接口的指定已声明字段。 
Field[] getDeclaredFields() 
//返回 Field 对象的一个数组，这些对象反映此 Class 对象所表示的类或接口所声明的所有字段，包括公共、保护、默认（包）访问和私有字段，但不包括继承的字段。 
```

## JVM虚拟机

### jvm是如何实现线程的？

线程是比进程更轻量级的调度执行单位。线程可以把一个进程的资源分配和执行调度分开。一个进程里可以启动多条线程，各个线程可共享该进程的资源(内存地址，文件IO等)，又可以独立调度。线程是CPU调度的基本单位。

主流OS都提供线程实现。Java语言提供对线程操作的同一API，每个已经执行start()，且还未结束的java.lang.Thread类的实例，代表了一个线程。

Thread类的关键方法，都声明为Native。这意味着这个方法无法或没有使用平台无关的手段来实现，也可能是为了执行效率。

实现线程的方式A.使用内核线程实现内核线程(Kernel-Level Thread, KLT)就是直接由操作系统内核支持的线程。内核来完成线程切换内核通过调度器Scheduler调度线程，并将线程的任务映射到各个CPU上程序使用内核线程的高级接口，轻量级进程(Light Weight Process,LWP)，用户态和内核态切换消耗内核资源使用用户线程实现系统内核不能感知线程存在的实现用户线程的建立、同步、销毁和调度完全在用户态中完成所有线程操作需要用户程序自己处理，复杂度高，用户线程加轻量级进程混合实现轻量级进程作为用户线程和内核线程之间的桥梁。

### 类的加载

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200416185106628.png" alt="image-20200416185106628" style="zoom:67%;" />

加载、验证、准备、初始化和卸载这 5 个阶段的顺序是确定的，类的加载过程必须按照这种顺序按部就班地开始（注意是“开始”，而不是“进行”或“完成”），而解析阶段则不一定：它在某些情况下可以在初始化后再开始，这是为了支持 Java 语言的运行时绑定。

- 加载

- 验证

- 准备

- 解析

- 初始化开始的时机

  Java 虚拟机规范没有强制约束类加载过程的第一阶段（即：加载）什么时候开始，但对于“初始化”阶段，有着严格的规定。有且仅有 5 种情况必须立即对类进行“初始化”：

  - 在遇到 new、putstatic、getstatic、invokestatic 字节码指令时，如果类尚未初始化，则需要先触发其初始化。
  - 对类进行反射调用时，如果类还没有初始化，则需要先触发其初始化。
  - 初始化一个类时，如果其父类还没有初始化，则需要先初始化父类。
  - 虚拟机启动时，用于需要指定一个包含 main() 方法的主类，虚拟机会先初始化这个主类。
  - 当使用 JDK 1.7 的动态语言支持时，如果一个 java.lang.invoke.MethodHandle 实例最后的解析结果为 REF_getStatic、REF_putStatic、REF_invokeStatic 的方法句柄，并且这个方法句柄所对应的类还没初始化，则需要先触发其初始化。

  这 5 种场景中的行为称为对一个类进行**主动引用**，除此之外，其它所有引用类的方式都不会触发初始化，称为**被动引用**。

  被动引用例：

  对于静态字段，只有直接定义这个字段的类才会被初始化，因此通过其子类来引用父类中定义的静态字段，只会触发父类的初始化而不会触发子类的初始化。

   通过数组定义来引用类，不会触发此类的初始化。

  常量在编译阶段会存入调用类的常量池中，本质上并没有直接引用到定义常量的类，因此不会触发定义常量的类的初始化。

  **接口加载过程与类加载过程稍有不同：**

  当一个类在初始化时，要求其父类全部都已经初始化过了，但是一个接口在初始化时，并不要求其父接口全部都完成了初始化，当真正用到父接口的时候才会初始化。

- 使用

- 卸载

### 堆和栈

数据结构：

堆：一种常用的树形结构，是一种特殊的完全二叉树，其满足对任意节点而言大于或小于其父节点的值。

栈：先进后出。

JVM：

堆：Java堆是被所有线程共享的一块内存区域，在虚拟机启动时创建，用于存放对象实例，几乎所有的对象实例都在这里分配内存，也是垃圾收集器管理的主要区域

栈：Java虚拟机栈是描述方法的运行过程的内存模型，Java虚拟机栈会为每一个即将执行的方法开辟一个栈帧，用于存放方法运行中的一些信息：局部变量表、操作数栈、动态链接、方法出口信息...

区别：

可见性：堆对所有线程共享，栈对应于线程。

存放对象：堆存放对象实例，栈存放 局部变量，操作数栈，返回结果。

物理地址：堆不连续、栈连续。

内存：堆大小不确定；栈在编译器就确认大小，固定。

### 对象的访问

- 句柄访问方式

堆中需要有一块叫做“句柄池”的内存空间，句柄中包含了对象实例数据与类型数据各自的具体地址信息。

引用类型的变量存放的是该对象的句柄地址（reference）。访问对象时，首先需要通过引用类型的变量找到该对象的句柄，然后根据句柄中对象的地址找到对象。

优势：引用中存储的是稳定的句柄地址，在对象被移动（垃圾收集时移动对象是非常普遍的行为）时只会改变句柄中的实例数据指针，而引用本身不需要修改。 

- 直接指针访问方式

引用类型的变量直接存放对象的地址，从而不需要句柄池，通过引用能够直接访问对象。但对象所在的内存空间需要额外的策略存储对象所属的类信息的地址。 

优势：速度更快，节省了一次指针定位的时间开销。由于对象的访问在`Java`中非常频繁，因此这类开销积少成多后也是非常可观的执行成本。HotSpot 中采用的就是这种方式。 

### 内存泄露

 指不再被使用的对象或者变量一直被占据在内存中 。

例：长生命周期的对象持有短生命周期对象的引用，导致短生命周期的对象不会被回收，引起内存泄露。

### Java引用类型

强引用：发生 gc 的时候不会被回收。
软引用：有用但不是必须的对象，在发生内存溢出之前会被回收。
弱引用：有用但不是必须的对象，在下一次GC时会被回收。
虚引用（幽灵引用/幻影引用）：无法通过虚引用获得对象，用 PhantomReference 实现虚引用，虚引用的用途是在 gc 时返回一个通知。

### [各垃圾回收收集器特性][ https://www.cnblogs.com/cxxjohnson/p/8625713.html ]

新生代收集器：Serial、ParNew、Parallel Scavenge；

老年代收集器：Serial Old、Parallel Old、CMS；

整堆收集器：G1；

#### Serial

> Serial（串行）垃圾收集器是最基本、发展历史最悠久的收集器； 
>
> 作用于新生代，采用复制算法，单线程收集，在 进行垃圾收集时，必须暂停所有工作线程，直到完成；
>
> 优点： 
>
> 简单高效（与其他收集器的单线程相比）；
>
> 对于限定单个CPU的环境来说，Serial收集器没有线程交互（切换）开销，可以获得最高的单线程收集效率；
>
> 在用户的桌面应用场景中，可用内存一般不大（几十M至一两百M），可以在较短时间内完成垃圾收集（几十MS至一百多MS）,只要不频繁发生，这是可以接受的

#### ParNew

>  ParNew垃圾收集器是Serial收集器的多线程版本。
>
>  除了多线程外，其余的行为、特点和Serial收集器一样；同样需要在收集时暂停所有用户线程；
>
> 在Server模式下，ParNew收集器是一个非常重要的收集器，因为除Serial外，目前只有它能与CMS收集器配合工作；
>
> 但在单个CPU环境中，不会比Serail收集器有更好的效果，因为存在线程交互开销。
>
> **为什么只有ParNew能与CMS收集器配合**：
>
> CMS是HotSpot在JDK1.5推出的第一款真正意义上的并发（Concurrent）收集器，第一次实现了让垃圾收集线程与用户线程（基本上）同时工作；CMS作为老年代收集器，但却无法与JDK1.4已经存在的新生代收集器Parallel Scavenge配合工作； 因为Parallel Scavenge（以及G1）都没有使用传统的GC收集器代码框架，而另外独立实现；而其余几种收集器则共用了部分的框架代码

#### Parallel Scavenge

> 新生代收集器；采用复制算法；多线程收集；
>
> 特点：
>
> 它的关注点与其他收集器不同；CMS等收集器的关注点是尽可能地缩短垃圾收集时用户线程的停顿时间；而Parallel Scavenge收集器的目标则是达一个可控制的吞吐量（Throughput）；
>
> 主要应用场景：
>
> 高吞吐量为目标，即减少垃圾收集时间，让用户代码获得更长的运行时间；当应用程序运行在具有多个CPU上，对暂停时间没有特别高的要求时，即程序主要在后台进行计算，而不需要与用户进行太多交互；例如，那些执行批量处理、订单处理、工资支付、科学计算的应用程序；

#### Serial Old

> 针对老年代；采用"标记-整理"算法（还有压缩，Mark-Sweep-Compact）；单线程收集；

#### Parallel Old

> 针对老年代；采用"标记-整理"算法；多线程收集；

#### CMS

>   并发标记清理（Concurrent Mark Sweep，CMS）收集器也称为并发低停顿收集器（Concurrent Low Pause Collector）或低延迟（low-latency）垃圾收集器；
>
> 针对老年代；基于"标记-清除"算法(不进行压缩操作，产生内存碎片)；      以获取最短回收停顿时间为目标；并发收集、低停顿；需要更多的内存；
>
> 应用场景：
>
> 与用户交互较多的场景；希望系统停顿时间最短，注重服务的响应速度；以给用户带来较好的体验；如常见WEB、B/S系统的服务器上的应用；
>
>  **CMS收集器运作过程** 
>
> （A）、初始标记（CMS initial mark）
>
> 仅标记一下GC Roots能直接关联到的对象；速度很快；但需要"Stop The World"；
>
> （B）、并发标记（CMS concurrent mark）
>
> 进行GC Roots Tracing的过程；刚才产生的集合中标记出存活对象；应用程序也在运行；并不能保证可以标记出所有的存活对象；
>
> （C）、重新标记（CMS remark）
>
> 为了修正并发标记期间因用户程序继续运作而导致标记变动的那一部分对象的标记记录；需要"Stop The World"，且停顿时间比初始标记稍长，但远比并发标记短；采用多线程并行执行来提升效率；
>
> （D）、并发清除（CMS concurrent sweep）
>
> 回收所有的垃圾对象；
>
> 缺点：
>
> （A）、对CPU资源非常敏感 
>
> 并发收集虽然不会暂停用户线程，但因为占用一部分CPU资源，还是会导致应用程序变慢，总吞吐量降低。
>
> CMS的默认收集线程数量是=(CPU数量+3)/4；
>
> 当CPU数量多于4个，收集线程占用的CPU资源多于25%，对用户程序影响可能较大；不足4个时，影响更大，可能无法接受。
>
> （B）、无法处理浮动垃圾,可能出现"Concurrent Mode Failure"失败 
>
> 浮动垃圾（Floating Garbage）：在并发清除时，用户线程新产生的垃圾，称为浮动垃圾；这使得并发清除时需要预留一定的内存空间，不能像其他收集器在老年代几乎填满再进行收集；也要可以认为CMS所需要的空间比其他垃圾收集器大；
>
> 如果CMS预留内存空间无法满足程序需要，就会出现一次"Concurrent Mode Failure"失败；这时JVM启用后备预案：临时启用Serail Old收集器，而导致另一次Full GC的产生；这样的代价是很大的。
>
> （C）、产生大量内存碎片 
>
> 由于CMS基于"标记-清除"算法，清除后不进行压缩操作； 
>
> 产生大量不连续的内存碎片会导致分配大内存对象时，无法找到足够的连续内存，从而需要提前触发另一次Full GC动作。 
>
> 由于空间不再连续，CMS需要使用可用"空闲列表"内存分配方式，这比简单实用"碰撞指针"分配内存消耗大 ；

#### G1

> 能充分利用多CPU、多核环境下的硬件优势；也可以并发让垃圾收集与用户程序同时进行；
>
> 虽然保留分代概念，但Java堆的内存布局有很大差别；将整个堆划分为多个大小相等的独立区域（Region）；新生代和老年代不再是物理隔离，它们都是一部分Region（不需要连续）的集合；
>
> 从整体看，是基于标记-整理算法； 可以明确指定M毫秒时间片内，垃圾收集消耗的时间不超过N毫秒； 
>
>  在下面的情况时，使用G1可能比CMS好：
>
> >    （1）、超过50％的Java堆被活动数据占用；
> >
> >    （2）、对象分配频率或年代提升频率变化很大；
> >
> >    （3）、GC停顿时间过长（长于0.5至1秒）。
>
> **G1收集器运作过程** 
>
> （A）、初始标记（Initial Marking）
>
> 仅标记一下GC Roots能直接关联到的对象；且修改TAMS（Next Top at Mark Start）,让下一阶段并发运行时，用户程序能在正确可用的Region中创建新对象；需要"Stop The World"，但速度很快；
>
> （B）、并发标记（Concurrent Marking）
>
> 进行GC Roots Tracing的过程；刚才产生的集合中标记出存活对象；耗时较长，但应用程序也在运行；并不能保证可以标记出所有的存活对象；
>
> （C）、最终标记（Final Marking）
>
> 为了修正并发标记期间因用户程序继续运作而导致标记变动的那一部分对象的标记记录；上一阶段对象的变化记录在线程的Remembered Set Log；这里把Remembered Set Log合并到Remembered Set中；需要"Stop The World"，且停顿时间比初始标记稍长，但远比并发标记短；采用多线程并行执行来提升效率；
>
> （D）、筛选回收（Live Data Counting and Evacuation）
>
> 首先排序各个Region的回收价值和成本；然后根据用户期望的GC停顿时间来制定回收计划；最后按计划回收一些价值高的Region中垃圾对象；回收时采用"复制"算法，从一个或多个Region复制存活对象到堆上的另一个空的Region，并且在此过程中压缩和释放内存；可以并发进行，降低停顿时间，并增加吞吐量；

### 怎么判断对象是否可以被回收

- 引用计数器法：为每个对象创建一个引用计数，有对象引用时计数器 +1，引用被释放时计数 -1，当计数器为 0 时就可以被回收。它有一个缺点不能解决循环引用的问题；

- 可达性分析算法：从 GC Roots 开始向下搜索，搜索所走过的路径称为引用链。当一个对象到 GC Roots 没有任何引用链相连时，则证明此对象是可以被回收的。

- GCRoot的种类

  1.虚拟机栈：栈帧中的本地变量表引用的对象

  2.native方法引用的对象

  3.方法区中的静态变量和常量引用的对象

## 设计模式

### 单例模式

#### Ⅰ 懒汉式-线程不安全

```java
public class Singleton {

    private static Singleton uniqueInstance;

    private Singleton() {
    }

    public static Singleton getUniqueInstance() {
        if (uniqueInstance == null) {
            uniqueInstance = new Singleton();
        }
        return uniqueInstance;
    }
}
```

#### Ⅱ 饿汉式-线程安全

```java
private static Singleton uniqueInstance = new Singleton();
```

#### Ⅲ 懒汉式-线程安全

```java
public static synchronized Singleton getUniqueInstance() {
    if (uniqueInstance == null) {
        uniqueInstance = new Singleton();
    }
    return uniqueInstance;
}
```

#### Ⅳ 双重校验锁-线程安全

```java
public class Singleton {

    private volatile static Singleton uniqueInstance;

    private Singleton() {
    }

    public static Singleton getUniqueInstance() {
        if (uniqueInstance == null) {
            synchronized (Singleton.class) {
                if (uniqueInstance == null) {
                    uniqueInstance = new Singleton();
                }
            }
        }
        return uniqueInstance;
    }
}
```

 考虑下面的实现，也就是只使用了一个 if 语句。在 uniqueInstance == null 的情况下，如果两个线程都执行了 if 语句，那么两个线程都会进入 if 语句块内。虽然在 if 语句块内有加锁操作，但是两个线程都会执行 `uniqueInstance = new Singleton();` 这条语句，只是先后的问题，那么就会进行两次实例化。因此必须使用双重校验锁，也就是需要使用两个 if 语句：第一个 if 语句用来避免 uniqueInstance 已经被实例化之后的加锁操作，而第二个 if 语句进行了加锁，所以只能有一个线程进入，就不会出现 uniqueInstance == null 时两个线程同时进行实例化操作。 

uniqueInstance 采用 volatile 关键字修饰也是很有必要的， `uniqueInstance = new Singleton();` 这段代码其实是分为三步执行：

1. 为 uniqueInstance 分配内存空间
2. 初始化 uniqueInstance
3. 将 uniqueInstance 指向分配的内存地址

但是由于 JVM 具有指令重排的特性，执行顺序有可能变成 1>3>2。指令重排在单线程环境下不会出现问题，但是在多线程环境下会导致一个线程获得还没有初始化的实例。例如，线程 T1 执行了 1 和 3，此时 T2 调用 getUniqueInstance() 后发现 uniqueInstance 不为空，因此返回 uniqueInstance，但此时 uniqueInstance 还未被初始化。

使用 volatile 可以禁止 JVM 的指令重排，保证在多线程环境下也能正常运行。

#### Ⅴ 静态内部类实现

```java
public class Singleton {

    private Singleton() {
    }

    private static class SingletonHolder {
        private static final Singleton INSTANCE = new Singleton();
    }

    public static Singleton getUniqueInstance() {
        return SingletonHolder.INSTANCE;
    }
}
```

#### Ⅵ 枚举实现

```java
public enum Singleton {

    INSTANCE;

    private String objName;

    public String getObjName() {
        return objName;
    }

    public void setObjName(String objName) {
        this.objName = objName;
    }

    public static void main(String[] args) {
        // 单例测试
        Singleton firstSingleton = Singleton.INSTANCE;
        firstSingleton.setObjName("firstName");
        System.out.println(firstSingleton.getObjName());
        Singleton secondSingleton = Singleton.INSTANCE;
        secondSingleton.setObjName("secondName");
        System.out.println(firstSingleton.getObjName());
        System.out.println(secondSingleton.getObjName());

        // 反射获取实例测试
        try {
            Singleton[] enumConstants = Singleton.class.getEnumConstants();
            for (Singleton enumConstant : enumConstants) {
                System.out.println(enumConstant.getObjName());
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### 简单工厂模式

把实例化的操作放入一个类（工厂）中，由工厂来决定应该实例化哪个类，具体的实现不向客户暴露。

```java
public interface Product {
}
public class ConcreteProduct implements Product {
}
public class ConcreteProduct1 implements Product {
}
public class ConcreteProduct2 implements Product {
}
public class SimpleFactory {
    public Product createProduct(int type) {
        if (type == 1) {
            return new ConcreteProduct1();
        } else if (type == 2) {
            return new ConcreteProduct2();
        }
        return new ConcreteProduct();
    }
}
```

### 工厂方法

在工厂方法中，使用子类来创建对象。

```java
public abstract class Factory {
    abstract public Product factoryMethod();
    public void doSomething() {
        Product product = factoryMethod();
        // do something with the product
    }
}
public class ConcreteFactory extends Factory {
    public Product factoryMethod() {
        return new ConcreteProduct();
    }
}
public class ConcreteFactory1 extends Factory {
    public Product factoryMethod() {
        return new ConcreteProduct1();
    }
}
public class ConcreteFactory2 extends Factory {
    public Product factoryMethod() {
        return new ConcreteProduct2();
    }
}
```



### 抽象工厂

 抽象工厂模式创建的是对象家族，也就是很多对象而不是一个对象，并且这些对象是相关的，也就是说必须一起创建出来。而工厂方法模式只是用于创建一个对象，这和抽象工厂模式有很大不同。 

```java
public class AbstractProductA {
}
public class AbstractProductB {
}
public class ProductA1 extends AbstractProductA {
}
public class ProductA2 extends AbstractProductA {
}
public class ProductB1 extends AbstractProductB {
}
public class ProductB2 extends AbstractProductB {
}
public abstract class AbstractFactory {
    abstract AbstractProductA createProductA();
    abstract AbstractProductB createProductB();
}
public class ConcreteFactory1 extends AbstractFactory {
    AbstractProductA createProductA() {
        return new ProductA1();
    }

    AbstractProductB createProductB() {
        return new ProductB1();
    }
}
public class ConcreteFactory2 extends AbstractFactory {
    AbstractProductA createProductA() {
        return new ProductA2();
    }

    AbstractProductB createProductB() {
        return new ProductB2();
    }
}
public class Client {
    public static void main(String[] args) {
        AbstractFactory abstractFactory = new ConcreteFactory1();
        AbstractProductA productA = abstractFactory.createProductA();
        AbstractProductB productB = abstractFactory.createProductB();
        // do something with productA and productB
    }
}
```

### 生成器

将一个对象分解为各个组件，将对象组件的构造封装起来，可以控制整个对象的生成过程，对不同类型的对象需要实现不同的具体构造器的类，这可能会大大增加类的数量。

```
public class Computer {
    public String master;
    public String screen;
    public String keyboard;
    public String mouse;
    public String audio;
    public void setMaster(String master) {
        this.master = master;
    }
    public void setScreen(String screen) {
        this.screen = screen;
    }
    public void setKeyboard(String keyboard) {
        this.keyboard = keyboard;
    }
    public void setMouse(String mouse) {
        this.mouse = mouse;
    }
    public void setAudio(String audio) {
        this.audio = audio;
    }
}

public abstract class ComputerBuilder {
    
    protected Computer computer;
    
    public Computer getComputer() {
        return computer;
    }
    
    public void buildComputer() {
        computer = new Computer();
        System.out.println("生成了一台电脑！！！");
    }

    public abstract void buildMaster();
    public abstract void buildScreen();
    public abstract void buildKeyboard();
    public abstract void buildMouse();
    public abstract void buildAudio();
}

public class HPComputerBuilder extends ComputerBuilder {

    @Override
    public void buildMaster() {
        // TODO Auto-generated method stub
        computer.setMaster("i7,16g,512SSD,1060");
        System.out.println("(i7,16g,512SSD,1060)的惠普主机");
    }

    @Override
    public void buildScreen() {
        // TODO Auto-generated method stub
        computer.setScreen("1080p");
        System.out.println("(1080p)的惠普显示屏");
    }

    @Override
    public void buildKeyboard() {
        // TODO Auto-generated method stub
        computer.setKeyboard("cherry 青轴机械键盘");
        System.out.println("(cherry 青轴机械键盘)的键盘");
    }

    @Override
    public void buildMouse() {
        // TODO Auto-generated method stub
        computer.setMouse("MI 鼠标");
        System.out.println("(MI 鼠标)的鼠标");
    }

    @Override
    public void buildAudio() {
        // TODO Auto-generated method stub
        computer.setAudio("飞利浦 音响");
        System.out.println("(飞利浦 音响)的音响");
    }
}

public class DELLComputerBuilder extends ComputerBuilder {
    
    @Override
    public void buildMaster() {
        // TODO Auto-generated method stub
        computer.setMaster("i7,32g,1TSSD,1060");
        System.out.println("(i7,32g,1TSSD,1060)的戴尔主机");
    }

    @Override
    public void buildScreen() {
        // TODO Auto-generated method stub
        computer.setScreen("4k");
        System.out.println("(4k)的dell显示屏");
    }

    @Override
    public void buildKeyboard() {
        // TODO Auto-generated method stub
        computer.setKeyboard("cherry 黑轴机械键盘");
        System.out.println("(cherry 黑轴机械键盘)的键盘");
    }

    @Override
    public void buildMouse() {
        // TODO Auto-generated method stub
        computer.setMouse("MI 鼠标");
        System.out.println("(MI 鼠标)的鼠标");
    }

    @Override
    public void buildAudio() {
        // TODO Auto-generated method stub
        computer.setAudio("飞利浦 音响");
        System.out.println("(飞利浦 音响)的音响");
    }
}

public class Director { 
    private ComputerBuilder computerBuilder;

    public void setComputerBuilder(ComputerBuilder computerBuilder) {
        this.computerBuilder = computerBuilder;
    }
    
    public Computer getComputer() {
        return computerBuilder.getComputer();
    }
    
    public void constructComputer() {
        computerBuilder.buildComputer();
        computerBuilder.buildMaster();
        computerBuilder.buildScreen();
        computerBuilder.buildKeyboard();
        computerBuilder.buildMouse();
        computerBuilder.buildAudio();
    }
}

public class ComputerCustomer {
    public static void main(String[] args) {
        // TODO Auto-generated method stub
        Director director = new Director();
        
        ComputerBuilder hp = new HPComputerBuilder();
        
        director.setComputerBuilder(hp);
        
        director.constructComputer();
        //get the pc
        Computer pc = director.getComputer();
    }
}
```

### 原型模式

 使用原型实例指定要创建对象的类型，通过复制这个原型来创建新对象。 

## 操作系统

### 1、进程、线程、协程

进程：是操作系统资源分配的最小单位，拥有代码、打开的文件资源、数据资源和独立的内存空间，一个进程可以拥有多个线程。

线程：是操作系统执行的最小单位；拥有自己的栈空间，五种状态： 初始化、可运行、运行中、阻塞、销毁 。

协程：比线程更轻量级的存在，一个线程可以拥有多个协程，协程不由操作系统内核管理，完全由程序所控制。

区别与联系：

- 协程既不是进程也不是线程，协程仅仅是一个特殊的函数，协程和进程不是一个维度的。
- 一个进程可以包含多个线程，一个线程可以包含多个协程。
- 一个线程内的多个协程虽然可以切换，但是多个协程是串行执行的，只能在一个线程内运行，没法利用CPU多核能力。
- 协程与进程一样，切换是存在上下文切换问题的。

上下文切换：

- 进程的切换者是操作系统，切换时机是根据操作系统自己的切换策略，用户是无感知的。进程的切换内容包括页全局目录、内核栈、硬件上下文，切换内容保存在内存中。进程切换过程是由“用户态到内核态到用户态”的方式，切换效率低。
- 线程的切换者是操作系统，切换时机是根据操作系统自己的切换策略，用户无感知。线程的切换内容包括内核栈和硬件上下文。线程切换内容保存在内核栈中。线程切换过程是由“用户态到内核态到用户态”， 切换效率中等。
- 协程的切换者是用户（编程者或应用程序），切换时机是用户自己的程序所决定的。协程的切换内容是硬件上下文，切换内存保存在用户自己的变量（用户栈或堆）中。协程的切换过程只有用户态，即没有陷入内核态，因此切换效率高。

### 2、电梯调度算法

### 3、进程调度算法

- 批处理系统
- 交互式系统
- 实时系统

### 4、死锁

 死锁是指两个或两个以上的进程（线程）在执行过程中，由于竞争资源或者由于彼此通信而造成的一种阻塞的现象，若无外力作用，它们都将无法推进下去。此时称系统处于死锁状态或系统产生了死锁，这些永远在互相等待的进程（线程）称为死锁进程（线程）。 

形成死锁的四个必要条件：

**互斥条件**：线程(进程)对于所分配到的资源具有排它性，即一个资源只能被一个线程(进程)占用，直到被该线程(进程)释放。

**请求与保持条件**：一个线程(进程)因请求被占用资源而发生阻塞时，对已获得的资源保持不放。

**不剥夺条件**：线程(进程)已获得的资源在末使用完之前不能被其他线程强行剥夺，只有自己使用完毕后才释放资源。

**循环等待条件**：当发生死锁时，所等待的线程(进程)必定会形成一个环路（类似于死循环），造成永久阻塞。

破坏死锁：

**破坏互斥条件**：这个条件我们没有办法破坏，因为我们用锁本来就是想让他们互斥的（临界资源需要互斥访问）。

**破坏请求与保持条件**：一次性申请所有的资源。

**破坏不剥夺条件**：占用部分资源的线程进一步申请其他资源时，如果申请不到，可以主动释放它占有的资源。

**破坏循环等待条件**：靠按序申请资源来预防。按某一顺序申请资源，释放资源则反序释放。破坏循环等待条件。

### 5、段式存储、页式存储、段页式存储

- **段式存储**

  段号	+	段内位移量

  将用户程序地址空间分成若干个大小不等的段，每段可以定义一组相对完整的逻辑信息。存储分配时，以段为单位，段与段在内存中可以不相邻接。

- **页式存储**

  页号	+	页内位移

  将一个进程的逻辑地址空间划分成若干大小相等的部分，每一部分称为页或页面（页面的大小通常是2的次幂，大约在512B~4MB之间）；同样，将内存空间也划分为与页面大小相同的若干个存储块，即物理块或页框。可将用户的任一页放在内存的任一块中，实现离散分配。 

  *快表的地址转换*：页表存放在内存中，使CPU每要存取一个数据，都要两次访问（访问页表，寻找物理块号；访问内存，读写数据）；这使计算机的处理速度降低1/2。为提高地址变换速度，可在地址转换机构中增设一个具有并行查寻能力的特殊高速缓冲存储器，又称快表（TLB），用以存放当前访问最频繁的那些少量页表项。

  *纯分页系统*：所谓纯分页系统是指在调度一个作业时，必须把它的所有页一次装入到内存的物理块中，如果当时物理块不足，则该作业必须等待，直到有足够的物理块为止，这时系统可再调度另外的作业，纯分页系统同样有地址转换和快表，和基础分页系统求地址过程差不多

  *请求式分页系统*：是目前常用的一种实现虚拟存储器的方式；基本思想是，作业在运行之前，只把当前需要的一部分页面装入内存，当需要其他页面是，才自动选择一些页交换到辅存，同时调入所需的页到内存中

- **段页式存储**

  段号	+	页号	+	页内位移量

  分页系统能有效地提高内存的利用率，而分段系统能反映程序的逻辑结构，便于段的共享与保护，将分页与分段两种存储方式结合起来，就形成了段页式存储管理方式。

  在段页式存储管理系统中，作业的地址空间首先被分成若干个逻辑分段，每段都有自己的段号，然后再将每段分成若干个大小相等的页。对于主存空间也分成大小相等的页，主存的分配以页为单位。

  段页式系统中，作业的地址结构包含三部分的内容：段号   页号    页内位移量。

  程序员按照分段系统的地址结构将地址分为段号与段内位移量，地址变换机构将段内位移量分解为页号和页内位移量。

  为实现段页式存储管理，系统应为每个进程设置一个段表，包括每段的段号，该段的页表始址和页表长度。每个段有自己的页表，记录段中的每一页的页号和存放在主存中的物理块号。

- **段式存储与页式存储的区别**

  页是信息的物理单位。分页的目的是为了实现离散分离，提高内存利用率。分页仅仅是系统管理上的需要，对用户不可见。

  段是信息的逻辑单位。分段的目的是为了更好的满足用户的需求。一个段通常包含一组属于一个逻辑模块的信息，分段是对用户可见的，用户编程需要显示给出段名。

  页的大小固定由系统决定，段的大小不固定，取决于用户编写的程序。

  分段比分页更容易实现信息的共享和保护。

  分页的用户进程地址空间是一维的，只需给出一个记忆符即可表示一个地址；分段的用户进程地址空间是二维的，在标识一个地址时，需要给出段名，也要给出段内地址。

  分段：段内地址字段溢出将产生越界中断；分页：段内地址字段溢出将自动加入页号中。

### 6、软链接、硬链接

硬链接:文件A是文件B的硬链接，则A的目录项中的inode节点号与B节点的inode节点号相同，既一个inode节点对应两个不同的文件名，两个文件名指向一个同一个文件,A和B对于文件系统其实是完全相同的. 如果删除了其中一个，对另外一个没有影响. 每增加一个文件名，inode节点上的链接数增加一，每删除一个对应的文件名，inode节点上的链接数减一，直到为0，inode节点和对应数据块被回收. 对应上图你就可以理解硬链接的过程。

特点：不能对目录创建硬链接，原因有几种，最重要的是：文件系统不能存在链接环，存在环的后果会导致例如文件遍历等操作的混乱；不能对不同的文件系统创建硬链接，既两个文件名要在相同的文件系统下；不能对不存在的文件创建硬链接，由原理即可知真相。

软链接: A是B的软链接，A的目录项中的inode节点号与B的目录项中的inode节点号不同，A和B指向的是两个不同的inode，继而指向两块不同的数据块，但是A的数据块存放的知识B的路径名. A和B之间 "主从"关系，如果B被删除了，A仍然存在,但指向的是一个无效的链接。

特点可以对目录创建软链接，便利操作会忽略目录的软链接；可以跨越文件系统；可以对不存在的文件创建软链接，因为放的只是一个字符串，至于这个字符串是不是对于一个实际的文件，就是另外一回事了。

### 7、线程从创建到死亡

1. 新建( new )：新创建了一个线程对象。

2. 可运行( runnable )：线程对象创建后，其他线程(比如 main 线程）调用了该对象 的 start ()方法。该状态的线程位于可运行线程池中，等待被线程调度选中，获 取 cpu 的使用权 。

3. 运行( running )：可运行状态( runnable )的线程获得了CPU时间片 ，执行程序代码。

4. 阻塞( block )：阻塞状态是指线程因为某种原因放弃了CPU使用权，也即让出了CPU时间片 ，暂时停止运行。直到线程进入可运行( runnable )状态，才有 机会再次获得CPU时间片 转到运行( running )状态。阻塞的情况分三种：
   (一). 等待阻塞：运行( running )的线程执行 o . wait ()方法， JVM 会把该线程放 入等待队列中。
   (二). 同步阻塞：运行( running )的线程在获取对象的同步锁时，若该同步锁 被别的线程占用，则 JVM 会把该线程放入锁池( lock pool )中。
   (三). 其他阻塞: 运行( running )的线程执行 Thread . sleep ( long ms )或 t . join ()方法，或者发出了 I / O 请求时， JVM 会把该线程置为阻塞状态。 当 sleep ()状态超时、 join ()等待线程终止或者超时、或者 I / O 处理完毕时，线程重新转入可运行( runnable )状态。
5. 死亡( dead )：线程 run ()、 main () 方法执行结束，或者因异常退出了 run ()方法，则该线程结束生命周期。死亡的线程不可再次复生。 

### Linux常用命令



## 计算机网络

### 1. OSI七层模型/TCP.IP四层模型/五层协议体系

- OSI七层模型

  应用层、表示层、会话层、传输层、网络层、数据链路层、物理层

- TCP/IP四层模型

  应用层、运输层、网际层、网络接口层

- 五层协议体系

  应用层、传输层、网络层、链路层、物理层

#### 三种物理模型关系

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200726155439642.png" alt="image-20200726155439642" style="zoom: 67%;" />

#### 各层关键网络协议

| OSI七层网络模型 | TCP/IP四层概念模型 | 五层协议体系模型 | 对应网络协议                         |
| --------------- | ------------------ | ---------------- | ------------------------------------ |
| 应用层          | 应用层             | 应用层           | HTTP、FTP、NFS、WAIS、SMTP           |
| 表示层          | 应用层             | 应用层           | Telnet、Rlogin、SNMP                 |
| 会话层          | 应用层             | 应用层           | SMTP、DNS                            |
| 传输层          | 传输层             | 传输层           | TCP、UDP                             |
| 网络层          | 网络层             | 网络层           | IP、ICMP、ARP、RARP、AKP、UUCP       |
| 数据链路层      | 网络接口层         | 数据链路层       | FDDI、PND、SLIP、PPP                 |
| 物理层          | 网络接口层         | 物理层           | IEEE 802.1A、IEEE 802.2到IEEE 802.11 |

#### 各层的作用

1. 物理层

   主要定义物理设备标准，如网线的接口类型、光纤的接口类型、各种传输介质的传输速率等。它的主要作用是传输比特流（就是由1、0转化为电流强弱来进行传输,到达目的地后在转化为1、0，也就是我们常说的数模转换与模数转换）。这一层的数据叫做比特。

2. 数据链路层

   定义了如何让格式化数据以进行传输，以及如何让控制对物理介质的访问。这一层通常还提供错误检测和纠正，以确保数据的可靠传输。 

3. 网络层

   在位于不同地理位置的网络中的两个主机系统之间提供连接和路径选择。Internet的发展使得从世界各站点访问信息的用户数大大增加，而网络层正是管理这种连接的层。

4. 运输层

   定义了一些传输数据的协议和端口号（WWW端口80等），如： 
   TCP（transmission control protocol –传输控制协议，传输效率低，可靠性强，用于传输可靠性要求高，数据量大的数据） 
   UDP（user datagram protocol–用户数据报协议，与TCP特性恰恰相反，用于传输可靠性要求不高，数据量小的数据，如QQ聊天数据就是通过这种方式传输的）。 主要是将从下层接收的数据进行分段和传输，到达目的地址后再进行重组。常常把这一层数据叫做段。 　

5. 会话层

   通过运输层（端口号：传输端口与接收端口）建立数据传输的通路。主要在你的系统之间发起会话或者接受会话请求（设备之间需要互相认识可以是IP也可以是MAC或者是主机名）

6. 表示层

   可确保一个系统的应用层所发送的信息可以被另一个系统的应用层读取。例如，PC程序与另一台计算机进行通信，其中一台计算机使用扩展二一十进制交换码（EBCDIC），而另一台则使用美国信息交换标准码（ASCII）来表示相同的字符。如有必要，表示层会通过使用一种通格式来实现多种数据格式之间的转换。 

7. 应用层

   是最靠近用户的OSI层。这一层为用户的应用程序（例如电子邮件、文件传输和终端仿真）提供网络服务。

### 2. TCP/IP协议的概念及作用

- 概念

  TCP/IP 是因特网的通信协bai议，Transmission Control Protocol/Internet Protocol的简写，中译du名为传输控制协议/因特网互联协议，又名网络通讯协议，是Internet最基本的协议、Internet国际互联网络的基础，由网络层的IP协议和传输层的TCP协议组成。

  tcp/ip协议家族的两个核心协议：TCP（传输控制协议）和IP（网际协议）。

  - TCP协议全称：传输控制协议，英文：Transmission Control Protocol，是基于节字流的传输层通信协议，它完成传输层所指定的功能。

    TCP层是位于网络层（IP层）之上，应用层之下的中间层。不同主机的应用层之间经常需要可靠的、像管道一样的连接，但是IP层完成不了。那么TCP是工作过程如下：

    1、首先应用层向TCP层发送用于网间传输的数据流；

    2、然后TCP把数据流分区成适当长度的报文段；

    3、最后TCP把结果包传给IP层，由IP层来通过网络将包传送给接收端实体的TCP层。

    为了不发生丢包，TCP会给每一个包一个序号，一方面按序号传输，同时在TCP实体成功收到包之后还会给一个“回执”。这样提高了传输的可靠性。

  - IP协议，全称：网际协议或者互联网协议，英文：Internet Protocol。IP是在TCP/IP协议族中网络层的主要协议（TCP协议是完成传输层的功能），任务是仅仅根据源主机和目的主机的地址传送数据。

    为此目的，IP定义了寻址方法和数据报的封装结构。经常听到的，IPv4，IPv6就是常见的IP协议。 IP协议只关心如何使得数据能够跨越本地网络边界的问题，而不关心使用传输媒体的类型和数据传输的方式。

- 作用

  TCP/IP协议，是一个网络通信模型，以及一整个网络传输协议家族，为互联网的基础通信架构。协议的作用就是，相互通信的计算机之间需要遵循的约定。

  TCP/IP提供点对点的链接机制，将数据应该如何封装、定址、传输、路由以及在目的地如何接收，都加以标准化。简单的说，TCP/IP定义了全世界的计算机之间通信，传输数据的规则。TCP/IP通信模型分为4层，应用层，传输层，网络互联层，网络接口层。

### 3. TCP、UDP

#### 报文结构

- TCP报文结构

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200726161135825.png" alt="image-20200726161135825" style="zoom:67%;" />

- UDP报文结构

  <img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200726161258278.png" alt="image-20200726161258278" style="zoom:67%;" />

#### TCP/UDP优缺点以及区别

TCP的优点： 可靠，稳定 TCP的可靠体现在TCP在传递数据之前，会有三次握手来建立连接，而且在数据传递时，有确认、窗口、重传、拥塞控制机制，在数据传完后，还会断开连接用来节约系统资源。 TCP的缺点： 慢，效率低，占用系统资源高，易被攻击 TCP在传递数据之前，要先建连接，这会消耗时间，而且在数据传递时，确认机制、重传机制、拥塞控制机制等都会消耗大量的时间，而且要在每台设备上维护所有的传输连接，事实上，每个连接都会占用系统的CPU、内存等硬件资源。 而且，因为TCP有确认机制、三次握手机制，这些也导致TCP容易被人利用，实现DOS、DDOS、CC等攻击。

UDP的优点： 快，比TCP稍安全 UDP没有TCP的握手、确认、窗口、重传、拥塞控制等机制，UDP是一个无状态的传输协议，所以它在传递数据时非常快。没有TCP的这些机制，UDP较TCP被攻击者利用的漏洞就要少一些。但UDP也是无法避免攻击的，比如：UDP Flood攻击…… UDP的缺点： 不可靠，不稳定 因为UDP没有TCP那些可靠的机制，在数据传递时，如果网络质量不好，就会很容易丢包。 基于上面的优缺点，那么： 什么时候应该使用TCP： 当对网络通讯质量有要求的时候，比如：整个数据要准确无误的传递给对方，这往往用于一些要求可靠的应用，比如HTTP、HTTPS、FTP等传输文件的协议，POP、SMTP等邮件传输的协议。 在日常生活中，常见使用TCP协议的应用如下： 浏览器，用的HTTP FlashFXP，用的FTP Outlook，用的POP、SMTP Putty，用的Telnet、SSH QQ文件传输 ………… 什么时候应该使用UDP： 当对网络通讯质量要求不高的时候，要求网络通讯速度能尽量的快，这时就可以使用UDP。 比如，日常生活中，常见使用UDP协议的应用如下： QQ语音 QQ视频 TFTP ……

区别：

1. 基于连接与无连接；
2. 对系统资源的要求（TCP较多，UDP少）；
3. UDP程序结构较简单；4.流模式与数据报模式 ；TCP保证数据正确性，
4. UDP可能丢包，TCP保证数据顺序，UDP不保证。

#### TCP三次握手、四次挥手

- 三次握手的连接过程

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200726152951084.png" alt="image-20200726152951084" style="zoom: 67%;" />

第一次握手：客户端向服务器端发送请求连接报文，请求连接报文中的SYN标志位置为1，随机选取一个序列号作为初始序列号与服务器端进行同步，发送完毕后，客户端状态变为SYN_SEND(同步已发送状态)。

第二次握手：服务端收到客户端的连接请求报文，如果统一建立连接，则发送确认报文。确认报文的首部中标志位SYN、ACK都置为一，等同于确认报文+连接报文，其确认号为客户端发送的序列号+1，自身也携带一个服务端的初始序列号，发送完毕后，服务器端装态变为SYN_RCVD(同步收到状态)。

第三次握手：客户端接收到服务端的确认报文后，会向服务器端发送确认报文，并准备建立连接，发送完该报文后，客户端进入ESTABLISHED（已建立连接状态），可以向服务器端发送请求。而服务器端需要在收到客户端发来的确认报文后，才会进入ESTABLISHED（已建立连接状态）。

**三次握手**：实质上就是客户端连接服务器指定端口，建立TCP连接，并同步序列号与确认号，交换TCP窗口大小信息。刚开始客户端处于closed状态、服务端处于listen状态。

第一次握手：客户端给服务端发送一个SYN报文，并指明客户端的初始化序列号，客户端处于SYN_SENT状态，同步号SYN = 1，初始序号seq = x，SYN = 1 的报文段不能携带数据。

第二次握手：服务端监听到SYN报文后，用自己的SYN报文应答指定自己的初始化序列号， 同时会把客户端的 ISN + 1 作为ACK 的值，表示自己已经收到了客户端的 SYN，此时服务器处于SYN_RCVD 的状态。 

第三次握手：客户端收到 SYN 报文之后，会发送一个 ACK 报文，当然，也是一样把服务器的 ISN + 1 作为 ACK 的值，表示已经收到了服务端的 SYN 报文，此时客户端处于 ESTABLISHED状态。服务器收到 ACK 报文之后，也处于 ESTABLISHED 状态，此时，双方已建立起了连接，第三次握手可以携带数据。

**四次挥手**：刚开始双方都处于 ESTABLISHED 状态，假如是客户端先发起关闭请求。

- 第一次挥手：客户端发送一个 FIN 报文，报文中会指定一个序列号。此时客户端处于 `FIN_WAIT1` 状态。
  即发出**连接释放报文段**（FIN=1，序号seq=u），并停止再发送数据，主动关闭TCP连接，进入FIN_WAIT1（终止等待1）状态，等待服务端的确认。
- 第二次挥手：服务端收到 FIN 之后，会发送 ACK 报文，且把客户端的序列号值 +1 作为 ACK 报文的序列号值，表明已经收到客户端的报文了，此时服务端处于 `CLOSE_WAIT` 状态。
  即服务端收到连接释放报文段后即发出**确认报文段**（ACK=1，确认号ack=u+1，序号seq=v），服务端进入CLOSE_WAIT（关闭等待）状态，此时的TCP处于半关闭状态，客户端到服务端的连接释放。客户端收到服务端的确认后，进入FIN_WAIT2（终止等待2）状态，等待服务端发出的连接释放报文段。
- 第三次挥手：如果服务端也想断开连接了，和客户端的第一次挥手一样，发给 FIN 报文，且指定一个序列号。此时服务端处于 `LAST_ACK` 的状态。
  即服务端没有要向客户端发出的数据，服务端发出**连接释放报文段**（FIN=1，ACK=1，序号seq=w，确认号ack=u+1），服务端进入LAST_ACK（最后确认）状态，等待客户端的确认。
- 第四次挥手：客户端收到 FIN 之后，一样发送一个 ACK 报文作为应答，且把服务端的序列号值 +1 作为自己 ACK 报文的序列号值，此时客户端处于 `TIME_WAIT` 状态。需要过一阵子以确保服务端收到自己的 ACK 报文之后才会进入 CLOSED 状态，服务端收到 ACK 报文之后，就处于关闭连接了，处于 `CLOSED` 状态。
  即客户端收到服务端的连接释放报文段后，对此发出**确认报文段**（ACK=1，seq=u+1，ack=w+1），客户端进入TIME_WAIT（时间等待）状态。此时TCP未释放掉，需要经过时间等待计时器设置的时间2MSL后，客户端才进入CLOSED状态。

1. 请画出三次握手和四次挥手的示意图

   <img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200402145406300.png" alt="image-20200402145406300" style="zoom:50%;" />

2. 为什么连接的时候是三次握手？

   确认客户端与服务端的接收与发送能力是否正常。

   第一次握手->服务端可知客户端的发送能力与服务端的接收能力。

   第二次握手->客户端可知客户端的发送能力，服务端的发送与接收能力。

   第三次握手->服务端可知双方接收、发送能力都正常。

   避免二次握手带来的问题。

3. 什么是半连接队列？

   服务器第一次收到客户端的 SYN 之后，就会处于 SYN_RCVD 状态，此时双方还没有完全建立其连接，服务器会把此种状态下请求连接放在一个**队列**里，我们把这种队列称之为**半连接队列**。

   当然还有一个**全连接队列**，就是已经完成三次握手，建立起连接的就会放在全连接队列中。如果队列满了就有可能会出现丢包现象。

   关于**SYN-ACK 重传次数**的问题：
   服务器发送完SYN-ACK包，如果未收到客户确认包，服务器进行首次重传，等待一段时间仍未收到客户确认包，进行第二次重传。如果重传次数超过系统规定的最大重传次数，系统将该连接信息从半连接队列中删除。
   注意，每次重传等待的时间不一定相同，一般会是指数增长，例如间隔时间为 1s，2s，4s，8s......

4. ISN(Initial Sequence Number)是固定的吗？

   三次握手的其中一个重要功能是客户端和服务端交换 ISN(Initial Sequence Number)，以便让对方知道接下来接收数据的时候如何按序列号组装数据。如果 ISN 是固定的，攻击者很容易猜出后续的确认号，因此 ISN 是动态生成的。ISN一般每4ms加一。

5. 三次握手过程中可以携带数据吗？

   第三次发送报文后，对于客户端来说已经建立起连接，可以在报文中携带数据，若在第一次握手报文中携带数据，增加服务端接收报文的压力，使得攻击者能够在第一次报文中添加大量数据，反复发送来攻击服务端。

6. 如果第三次握手丢失了，客户端服务端会如何处理？

   **服务端**：
   该TCP连接的状态为SYN_RECV,并且会根据TCP的超时重传机制，会等待3秒、6秒、12秒后重新发送SYN+ACK包，以便Client重新发送ACK包。而Server重发SYN+ACK包的次数，可以通过设置/proc/sys/net/ipv4/tcp_synack_retries修改，默认值为5。如果重发指定次数之后，仍然未收到客户端的ACK应答，那么一段时间后，服务端自动关闭这个连接。
   **客户端**：
   客户端在接收到SYN+ACK包，它的TCP连接状态就为ESTABLISHED（已连接），表示该连接已经建立。那么如果第三次握手中的ACK包丢失的情况下，客户端向服务端发送数据，服务端将以RST包(reset重置)响应，才能感知到服务端的错误。

7. SYN攻击是什么？

   服务器端的资源分配是在二次握手时分配的，而客户端的资源是在完成三次握手时分配的，所以服务器容易受到SYN洪泛攻击。SYN攻击就是Client在短时间内伪造大量不存在的IP地址，并向Server不断地发送SYN包，Server则回复确认包，并等待Client确认，由于源地址不存在，因此Server需要不断重发直至超时，这些伪造的SYN包将长时间占用未连接队列，导致正常的SYN请求因为队列满而被丢弃，从而引起网络拥塞甚至系统瘫痪。SYN 攻击是一种典型的 DoS/DDoS 攻击。

   常见的防御 SYN 攻击的方法：

   - 缩短超时（SYN Timeout）时间
   - 增加最大半连接数
   - 过滤网关防护
   - SYN cookies技术

8. 挥手为什么需要四次？

    因为当服务端收到客户端的SYN连接请求报文后，可以直接发送SYN+ACK报文。其中ACK报文是用来应答的，SYN报文是用来同步的。但是关闭连接时，当服务端收到FIN报文时，很可能并不会立即关闭SOCKET，所以只能先回复一个ACK报文，告诉客户端，"你发的FIN报文我收到了"。只有等到我服务端所有的报文都发送完了，我才能发送FIN报文，因此不能一起发送。故需要四次挥手。 

9. 四次挥手释放连接时，等待2MSL的意义?

    一个是保证客户端发送ACK确认报文能到达服务器端；另一个则是保证本次连接中产生的报文全部从网络中消失。

10. 为什么不能用两次握手进行连接？

    答：3次握手完成两个重要的功能，既要双方做好发送数据的准备工作(双方都知道彼此已准备好)，也要允许双方就初始序列号进行协商，这个序列号在握手过程中被发送和确认。

    - 两次握手，客户端收到服务端的应答后进入ESTABLISHED（已建立连接状态），而服务端在收到客户端的连接请求之后就进入了ESTABLISHED状态。如果出现网络拥塞，客户端发送的连接请求报文A过了很久没有到达服务端，会超时重发请求报文B，服务端正确接受并确认应答，连接建立并开始通信传输数据，等通信结束之后释放连接。此时，如果之前失效的连接请求A到达服务端，由于两次握手就能成功建立连接，服务端收到请求A之后进入ESTABLISHED已建立连接状态，等待发送数据或者主动发送数据，此时，客户端已经进入CLISED断开连接状态，服务器会一直等下去，浪费服务器连接资源。

    - 现在把三次握手改成仅需要两次握手，死锁是可能发生的。作为例子，考虑计算机S和C之间的通信，假定C给S发送一个连接请求分组，S收到了这个分组，并发送了确认应答分组。按照两次握手的协定，S认为连接已经成功地建立了，可以开始发送数据分组。可是，C在S的应答分组在传输中被丢失的情况下，将不知道S 是否已准备好，不知道S建立什么样的序列号，C甚至怀疑S是否收到自己的连接请求分组。在这种情况下，C认为连接还未建立成功，将忽略S发来的任何数据分组，只等待连接确认应答分组。而S在发出的分组超时后，重复发送同样的分组。这样就形成了死锁。

####  TCP流量控制、拥塞控制、TCP/UDP 

### 4、[HTTP/HTTPS]( https://www.jianshu.com/p/6c46ef63c407 )

 HTTP+加密+认证+完整性保护 = HTTPS 

**散列函数 Hash**：

**对称加密：**

**非对称加密** :

### 7、访问网页的全过程

当Bob使用电脑访问网页时：首先要获取自身的IP地址，使用DHCP，生成DHCP请求报文，将报文放置在具有目的端口67（DHCP服务器）和源端口68（DHCP客户）的UDP报文段中，该UDP报文被放在广播IP目的地址（255.255.255.255）和源IP地址0.0.0.0 的IP数据报中；

1. 获取自身IP
2. 解析URL的IP地址
3. 建立TCP连接，进行通信

## 数据库

### 基本操作

### 1、索引为什么用B+树

在B树的基础上，每个节点存储的关键字更多，树的层级更少查询速度更快，所有关键词指针都在叶子节点上，所以每次查询的次数都相同，查询速度更稳定。

# 程序员小灰漫画

## 小结

### B-树

### B+树

### 一致性哈希

### Bitmap算法

### 布隆算法

### AES算法

### SHA系列算法

### MD5算法

### 破解MD5算法

### Base64算法

#  面经问题

![image-20200404175951148](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200404175951148.png)

## 海康威视JAVA开发面经

1.  OOM都有哪些，说出几种？

   - 堆溢出
   - 虚拟机栈和本地方法栈溢出
   - 运行时常量池溢出

   - 方法区溢出

2.  volatile关键字的作用，底层实现？讲一下你对JMM的理解。

   JMM（Java Memory Model）八大同步规范
   （1）lock(锁定)：作用于 主内存的变量，把一个变量标记为一条线程独占状态
   （2）unlock(解锁)：作用于 主内存的变量，把一个处于锁定状态的变量释放出来，释放后的变量才可以被其他线程锁定
   （3）read(读取)：作用于 主内存的变量，把一个变量值从主内存传输到线程的 工作内存中，以便随后的load动作使用
   （4）load(载入)：作用于 工作内存的变量，它把read操作从主内存中得到的变量值放入工作内存的变量副本中
   （5）use(使用)：作用于 工作内存的变量，把工作内存中的一个变量值传递给执行引擎
   （6）assign(赋值)：作用于 工作内存的变量，它把一个从执行引擎接收到的值赋给工作内存的变量
   （7）store(存储)：作用于 工作内存的变量，把工作内存中的一个变量的值传送到 主内存中，以便随后的write的操作
   （8）write(写入)：作用于 工作内存的变量，它把store操作从工作内存中的一个变量的值传送到 主内存的变量中

3. 线程的生命周期？

   线程的生命周期包含5个阶段，包括：新建、就绪、运行、阻塞、销毁。

   - 新建：就是刚使用new方法，new出来的线程；
   - 就绪：就是调用的线程的start()方法后，这时候线程处于等待CPU分配资源阶段，谁先抢的CPU资源，谁开始执行;
   - 运行：当就绪的线程被调度并获得CPU资源时，便进入运行状态，run方法定义了线程的操作和功能;
   - 阻塞：在运行状态的时候，可能因为某些原因导致运行状态的线程变成了阻塞状态，比如sleep()、wait()之后线程就处于了阻塞状态，这个时候需要其他机制将处于阻塞状态的线程唤醒，比如调用notify或者notifyAll()方法。唤醒的线程不会立刻执行run方法，它们要再次等待CPU分配资源进入运行状态;
   - 销毁：如果线程正常执行完毕后或线程被提前强制性的终止或出现异常导致结束，那么线程就要被销毁，释放资源;

4. ArrayList的初始长度是多少？扩容机制？

   

5. 谈谈你对JVM虚拟机的了解？垃圾回收过程？你用的哪个版本的JDK，使用的垃圾回收器是什么？垃圾回收算法是什么？介绍一下双亲委派模型

   

6. 序列化的原理和作用聊聊你对集合的认识

   

7. springMVC的内部流程 

   

8. java中的集合类都使用过哪些？CopyonWriteList的原理及使用场景

   

9. IO模型都有哪些？阻塞与非阻塞IO的区别？同步和异步IO的区别？ 

   

10. 线程池用过么？谈谈你对ThreadLocal的理解？

    

11. 单一的、固定数的和可变的三种创建线程池的方法，你用哪个多？

    

12. 线程池的拒绝策略都有哪些？如何合理的配置线程池？（考虑CPU密集型和IO密集型）

     

13. 有没有使用过redis？redis的基本类型有哪些？redis和memche有什么区别？

    

14. 说一下redis的使用场景吧？你再项目中哪里使用过redis？redis的持久化机制？ 

    

15. CAS知道么？底层实现？ 会引发什么问题？如何解决ABA问题？ 

    

16. 一条sql语句执行时间过长，应该如何优化？从哪些方面进行优化？

    

17. 在做分布式集群时候一般会产生什么问题？（分布式幂等性问题，session共享问题，分布式全局生成Id问题）

    