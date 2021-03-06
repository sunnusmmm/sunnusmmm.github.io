

<center><font face="宋体" size=6 color=blue>Welcome to NHY'S Blog</font></center>

# 面经知识点整合

## JAVA基础知识

### JDK、JRE、JVM三者间的联系与区别

- JDK

JDK(Java SE Development Kit)，Java标准开发包，它提供了编译、运行Java程序所需的各种工具和资源，包括Java编译器、Java运行时环境，以及常用的Java类库等。

- JRE

JRE( Java Runtime Environment) 、Java运行环境，用于解释执行Java的字节码文件。普通用户而只需要安装 JRE（Java Runtime Environment）来运行 Java 程序。而程序开发者必须安装JDK来编译、调试程序。

- JVM

JVM(Java Virtual Mechinal)，Java虚拟机，是JRE的一部分。它是整个java实现跨平台的最核心的部分，负责解释执行字节码文件，是可运行java字节码文件的虚拟计算机。所有平台的上的JVM向编译器提供相同的接口，而编译器只需要面向虚拟机，生成虚拟机能识别的代码，然后由虚拟机来解释执行。

当使用Java编译器编译Java程序时，生成的是与平台无关的字节码，这些字节码只面向JVM。不同平台的JVM都是不同的，但它们都提供了相同的接口。JVM是Java程序跨平台的关键部分，只要为不同平台实现了相应的虚拟机，编译后的Java字节码就可以在该平台上运行。

- **区别与联系**
  1. JDK 用于开发，JRE 用于运行java程序 ；如果只是运行Java程序，可以只安装JRE，无序安装JDK。
  2. JDk包含JRE，JDK 和 JRE 中都包含 JVM。
  3. JVM 是 java 编程语言的核心并且具有平台独立性。

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

  1. 子类和父类含有相同的成员变量的时候，访问的是父类的成员变量

  2. 子类和父类含有相同的成员方法是，访问的是子类的成员方法

  3. 子类和父类含有相同的静态函数和静态方法时，访问的是父类的。

  4. 父类不能访问子类特有成员和方法（强制类型转换除外）

  这样，我们也可以得出多态的局限：不能使用派生类特有的成员属性和派生类特有的成员方法。

  多态存在的三个必要条件:继承、重写、父类引用指向子类对象。

- **抽象**：将一类对象的共同特征总结出来构造类的过程，包括数据抽象和行为抽象，抽象只关注有哪些共同的属性和行为，不关注该行为的具体实现。

**重载和重写**:方法的重载和重写都是实现多态的方式，区别在于前者实现的是编译时的多态性，而后者实现的是运行时的多态性。重载发生在一个类中，同名的方法如果有不同的参数列表（参数类型不同、参数个数不同或者二者都不同）则视为重载；重写发生在子类与父类之间，重写要求子类被重写方法与父类被重写方法有相同的返回类型，比父类被重写方法更好访问，不能比父类被重写方法声明更多的异常（里氏代换原则）。重载对返回类型没有特殊的要求。 

#### 面向对象的"六原则一法则"(死记硬背)

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

泛型，即“参数化类型”。就是将类型由原来的具体的类型参数化，类似于方法中的变量参数，此时类型也定义成参数形式（可以称之为类型形参），然后在使用/调用时传入具体的类型（类型实参）。

#### 泛型存在的意义

1. 适用于多种数据类型执行相同的代码（代码复用）
2. 泛型中的类型在使用时指定，不需要强制类型转换（类型安全，编译器会检查类型）

####  泛型使用的约束和局限性

1. 不能实例化泛型类
2. 静态变量或方法不能引用泛型类型变量，但是静态泛型方法是可以的
3. 基本类型无法作为泛型类型
4. 无法使用instanceof关键字或==判断泛型类的类型
5. 泛型类的原生类型与所传递的泛型无关，无论传递什么类型，原生类是一样的
6. 泛型数组可以声明但无法实例化
7. 泛型类不能继承Exception或者Throwable
8. 不能捕获泛型类型限定的异常但可以将泛型限定的异常抛出

####  泛型类型的继承规则

1. 对于泛型参数是继承关系的泛型类之间是没有继承关系的

2. 泛型类可以继承其它泛型类，例如: public class ArrayList<E> extends AbstractList<E>

3. 泛型类的继承关系在使用中同样会受到泛型类型的影响

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

### 内部类与静态内部类

### throw和throws的区别

- throw用于主动抛出java.lang.Throwable 类的一个实例化对象，即通过关键字 throw 抛出一个 Error 或者 一个Exception；
- throws 的作用是作为方法声明和签名的一部分；

### error和exception的区别

- Error类和Exception类的父类都是throwable类
- Error类一般是指与虚拟机相关的问题，如系统崩溃，虚拟机错误，内存空间不足，方法调用栈溢等。直接终止程序即可；
- Exception类表示程序可以处理的异常，可以捕获和有可能恢复。需要程序员手动处理；

### 常见的五种运行时异常

- ClassCastException（类转换异常）
- IndexOutOfBoundsException（数组越界）
- NullPointerException（空指针异常）
- ArrayStoreException（数据存储异常，操作数组是类型不一致）
- BuﬀerOverﬂowException（缓存溢出异常）

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

#### HashMap详解（JDK1.8）（待完成）

##### HashMap的构造方法



##### HashMap的PutVal



##### HashMap的Resize



##### 为什么容量为2的幂

##### HashMap JDK1.7与JDK1.8的区别

- **HashMap JDK1.7扩容时采用头插法，JDK1.8采用尾插法**，使用头插法在多线程并发下会出现死循环的问题，原因如下图所示。

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200806202657795.png" alt="image-20200806202657795" style="zoom:50%;" />

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200806202731728.png" alt="image-20200806202731728" style="zoom:50%;" />

- **扩容后数据存储位置的计算方式不同**

- 在JDK1.7的时候是直接用hash值和需要扩容的二进制数进行&（这里就是为什么扩容的时候为啥一定必须是2的多少次幂的原因所在，因为如果只有2的n次幂的情况时最后一位二进制数才一定是1，这样能最大程度减少hash碰撞）（hash值 & length-1）
  
- 而在JDK1.8的时候直接用了JDK1.7的时候计算的规律，也就是扩容前的原始位置+扩容的大小值=JDK1.8的计算方式，而不再是JDK1.7的那种异或的方法。但是这种方式就相当于只需要判断Hash值的新增参与运算的位是0还是1就直接迅速计算出了扩容后的储存方式。
  
- J**DK1.7的时候使用的是数组+ 单链表的数据结构；但是在JDK1.8及之后时，使用的是数组+链表+红黑树的数据结构（转换阈值）。**

  主要是为了提高查询效率，单链表查询时，需要逐个遍历桶中元素，时间复杂度大致为O（n），而使用红黑树的结构能够将时间复杂度提高到O（nlogn）。

  当链表长度小于等于**6**时转变为链表，当链表长度大于等于**8**时转变为红黑树，采用这两个数为转换点的主要原因是，红黑树的平均查找长度是log(n)，如果长度为8，平均查找长度为log(8)=3，链表的平均查找长度为n/2，当长度为8时，平均查找长度为8/2=4，这才有转换成树的必要；链表长度如果是小于等于6，6/2=3，而log(6)=2.6，虽然速度也很快的，但是转化为树结构和生成树的时间并不会太短。提高效率的同时也避免了频繁的转换。

  还有一点重要的就是由于treenodes的大小大约是常规节点的两倍，因此我们仅在容器包含足够的节点以保证使用时才使用它们，当它们变得太小（由于移除或调整大小）时，它们会被转换回普通的node节点，容器中节点分布在hash桶中的频率遵循泊松分布，桶的长度超过8的概率非常非常小。

- **为什么使用红黑树而不是其他平衡二叉树**

  红黑树牺牲了一些查找性能 但其本身并不是完全平衡的二叉树。因此插入删除操作效率略高于AVL树
  AVL树用于自平衡的计算牺牲了插入删除性能，但是因为最多只有一层的高度差，查询效率会高一些。
  
  - 红黑树：
  
  ```
  红黑树是一种二叉查找树，但在每个节点增加一个存储位表示节点的颜色，可以是红或黑（非红即黑）。
  通过对任何一条从根到叶子的路径上各个节点着色的方式的限制，红黑树确保没有一条路径会比其它路
  径长出两倍，因此，红黑树是一种弱平衡二叉树，相对于要求严格的AVL树来说，它的旋转次数少，所
  以对于搜索，插入，删除操作较多的情况下，通常使用红黑树。
  ```
  
  性质：
  
  ```
  1. 每个节点非红即黑
  2. 根节点是黑的;
  3. 每个叶节点（叶节点即树尾端NULL指针或NULL节点）都是黑的;
  4. 如果一个节点是红色的，则它的子节点必须是黑色的。
  5. 对于任意节点而言，其到叶子点树NULL指针的每条路径都包含相同数目的黑节点;
  ```
  
  - 平衡二叉树（AVL树）：
  
  ```
  红黑树是在AVL树的基础上提出来的。
  平衡二叉树又称为AVL树，是一种特殊的二叉排序树。其左右子树都是平衡二叉树，且左右子树高度之差的绝对值不超过1。
  AVL树中所有结点为根的树的左右子树高度之差的绝对值不超过1。
  将二叉树上结点的左子树深度减去右子树深度的值称为平衡因子BF，那么平衡二叉树上的所有结点的平衡因子只可能是
  -1、0和1。只要二叉树上有一个结点的平衡因子的绝对值大于1，则该二叉树就是不平衡的。
  ```
  
  - 红黑树较AVL树的优点：
  
  ```
  AVL 树是高度平衡的，频繁的插入和删除，会引起频繁的rebalance，导致效率下降；红黑树不是高度平衡的，算是一种
  折中，插入最多两次旋转，删除最多三次旋转。
  ```
  
  所以红黑树在查找，插入删除的性能都是O(logn)，且性能稳定，所以STL里面很多结构包括map底层实现都是使用的红黑树。
  
- **在JDK1.7的时候是先进行扩容后进行插入，而在JDK1.8的时候则是先插入后进行扩容**

  在JDK1.7中的话，是先进行扩容后进行插入的，就是当你发现你插入的桶是不是为空，如果不为空说明存在值就发生了hash冲突，那么就必须得扩容，但是如果不发生Hash冲突的话，说明当前桶是空的（后面并没有挂有链表），那就等到下一次发生Hash冲突的时候在进行扩容，但是当如果以后都没有发生hash冲突产生，那么就不会进行扩容了，减少了一次无用扩容，也减少了内存的使用

### 并发

#### 并发编程三要素（线程的安全性问题体现在）：

原子性：原子，即一个不可再被分割的颗粒。原子性指的是一个或多个操作要么全部执行成功要么全部执行失败。

可见性：一个线程对共享变量的修改,另一个线程能够立刻看到。（synchronized,volatile）

有序性：程序执行的顺序按照代码的先后顺序执行。（处理器可能会对指令进行重排序）                                                     

#### 创建线程的四种方式：*

继承Thread类、实现Runnable接口、实现Callable接口、使用Executors工具类创建线程池。

为什么我们调用 start() 方法时会执行 run() 方法，不能直接调用 run() 方法:
new 一个 Thread，线程进入了新建状态。调用 start() 方法，会启动一个线程并使线程进入了就绪状态，当分配到时间片后就可以开始运行了。 start() 会执行线程的相应准备工作，然后自动执行 run() 方法的内容，这是真正的多线程工作。而直接执行 run() 方法，会把 run 方法当成一个 main 线程下的普通方法去执行，并不会在某个线程中执行它，所以这并不是多线程工作。

#### synchronized 和 Lock 有什么区别？

- synchronized是Java内置关键字，在JVM层面；Lock是一个类。
- synchronized可以给类、方法、代码块加锁；Lock只能给代码块加锁。
- 在发生异常情况时，syschronized不需要手动的获取或释放锁，不会发生死锁；Lock需要手动处理异常情况，释放锁，以此来避免死锁。
- synchronized无法知道有没有获得锁；通过Lock可以知道有没有成功获得锁。

#### synchronized 和 ReentrantLock 区别是什么？

synchronized 是和 if、else、for、while 一样的关键字，ReentrantLock 是类，这是二者的本质区别。既然 ReentrantLock 是类，那么它就提供了比synchronized 更多更灵活的特性，可以被继承、可以有方法、可以有各种各样的类变量。

两者都是可重入锁。“可重入锁”概念是：自己可以再次获取自己的内部锁。比如一个线程获得了某个对象的锁，此时这个对象锁还没有释放，当其再次想要获取这个对象的锁的时候还是可以获取的，如果不可锁重入的话，就会造成死锁。同一个线程每次获取锁，锁的计数器都自增1，所以要等到锁的计数器下降为0时才能释放锁。

主要区别如下：

ReentrantLock 使用起来比较灵活，但是必须有释放锁的配合动作；
ReentrantLock 必须手动获取与释放锁，而 synchronized 不需要手动释放和开启锁；
ReentrantLock 只适用于代码块锁，而 synchronized 可以修饰类、方法、变量等。
二者的锁机制其实也是不一样的。ReentrantLock 底层调用的是 Unsafe 的park 方法加锁，synchronized 操作的应该是对象头中 mark word
Java中每一个对象都可以作为锁，这是synchronized实现同步的基础：

普通同步方法，锁是当前实例对象；静态同步方法，锁是当前类的class对象；同步方法块，锁是括号里面的对象。

#### synchronized 和 volatile 的区别是什么？

synchronized 表示只有一个线程可以获取作用对象的锁，执行代码，阻塞其他线程。

volatile 表示变量在 CPU 的寄存器中是不确定的，必须从主存中读取。保证多线程环境下变量的可见性；禁止指令重排序。

区别：

volatile 是变量修饰符；synchronized 可以修饰类、方法、变量。

volatile 仅能实现变量的修改可见性，不能保证原子性；而 synchronized 则可以保证变量的修改可见性和原子性。

volatile 不会造成线程的阻塞；synchronized 可能会造成线程的阻塞。

volatile标记的变量不会被编译器优化；synchronized标记的变量可以被编译器优化。

volatile关键字是线程同步的轻量级实现，所以volatile性能肯定比synchronized关键字要好。但是volatile关键字只能用于变量而synchronized关键字可以修饰方法以及代码块。

锁共有4种状态，级别从低到高依次为：无状态锁，偏向锁，轻量级锁和重量级锁状态。

#### 自旋锁、互斥锁

自旋锁的定义：当一个线程尝试去获取某一把锁的时候，如果这个锁此时已经被别人获取(占用)，那么此线程就无法获取到这把锁，该线程将会等待，间隔一段时间后会再次尝试获取。这种采用循环加锁 -> 等待的机制被称为自旋锁。 

原理：自旋锁的原理比较简单，如果持有锁的线程能在短时间内释放锁资源，那么那些等待竞争锁的线程就不需要做内核态和用户态之间的切换进入阻塞状态，它们只需要等一等(自旋)，等到持有锁的线程释放锁之后即可获取，这样就避免了用户进程和内核切换的消耗。因为自旋锁避免了操作系统进程调度和线程切换，所以自旋锁通常适用在时间比较短的情况下。由于这个原因，操作系统的内核经常使用自旋锁。但是，如果长时间上锁的话，自旋锁会非常耗费性能，它阻止了其他线程的运行和调度。线程持有锁的时间越长，则持有该锁的线程将被 `OS(Operating System)` 调度程序中断的风险越大。如果发生中断情况，那么其他线程将保持旋转状态(反复尝试获取锁)，而持有该锁的线程并不打算释放锁，这样导致的是结果是无限期推迟，直到持有锁的线程可以完成并释放它为止。

自旋锁的优缺点：自旋锁尽可能的减少线程的阻塞，这对于锁的竞争不激烈，且占用锁时间非常短的代码块来说性能能大幅度的提升，因为自旋的消耗会小于线程阻塞挂起再唤醒的操作的消耗，这些操作会导致线程发生两次上下文切换！但是如果锁的竞争激烈，或者持有锁的线程需要长时间占用锁执行同步块，这时候就不适合使用自旋锁了，因为自旋锁在获取锁前一直都是占用 cpu 做无用功，占着 XX 不 XX，同时有大量线程在竞争一个锁，会导致获取锁的时间很长，线程自旋的消耗大于线程阻塞挂起操作的消耗，其它需要 cpu 的线程又不能获取到 cpu，造成 cpu 的浪费。所以这种情况下我们要关闭自旋锁。

互斥锁：保证在同一时刻只能有一个线程访问对象，同一线程多次加锁会造成死锁。

#### 线程池

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

#### CountDownLatch和CyclicBarrier的理解和区别*

从字面上理解，CountDown表示减法计数，Latch表示门闩的意思，计数为0的时候就可以打开门闩了。Cyclic Barrier表示循环的障碍物。两个类都含有这一个意思：对应的线程都完成工作之后再进行下一步动作，也就是大家都准备好之后再进行下一步。然而两者最大的区别是，进行下一步动作的动作实施者是不一样的。这里的“动作实施者”有两种，一种是主线程（即执行main函数），另一种是执行任务的其他线程，后面叫这种线程为“其他线程”，区分于主线程。对于CountDownLatch，当计数为0的时候，下一步的动作实施者是main函数；对于CyclicBarrier，下一步动作实施者是“其他线程”。

#### AQS（待完成）

#### CAS（Conmpare And Swap）（待完成）

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

### IO流（待完成）



## JVM虚拟机

### 什么是JVM以及平台无关性

Java虚拟机是一个可以执行Java字节码的虚拟机进程。Java源文件被编译成能被Java虚拟机执行的字节码文件。 Java被设计成允许应用程序可以运行在任意的平台，而不需要程序员为每一个平台单独重写或者是重新编译。Java虚拟机让这个变为可能，因为它知道底层硬件平台的指令长度和其他特性。

### jvm如何实现线程

线程是比进程更轻量级的调度执行单位。线程可以把一个进程的资源分配和执行调度分开。一个进程里可以启动多条线程，各个线程可共享该进程的资源(内存地址，文件IO等)，又可以独立调度。线程是CPU调度的基本单位。

主流OS都提供线程实现。Java语言提供对线程操作的同一API，每个已经执行start()，且还未结束的java.lang.Thread类的实例，代表了一个线程。

Thread类的关键方法，都声明为Native。这意味着这个方法无法或没有使用平台无关的手段来实现，也可能是为了执行效率。

实现线程的方式A.使用内核线程实现内核线程(Kernel-Level Thread, KLT)就是直接由操作系统内核支持的线程。内核来完成线程切换内核通过调度器Scheduler调度线程，并将线程的任务映射到各个CPU上程序使用内核线程的高级接口，轻量级进程(Light Weight Process,LWP)，用户态和内核态切换消耗内核资源使用用户线程实现系统内核不能感知线程存在的实现用户线程的建立、同步、销毁和调度完全在用户态中完成所有线程操作需要用户程序自己处理，复杂度高，用户线程加轻量级进程混合实现轻量级进程作为用户线程和内核线程之间的桥梁。

### 类的加载

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200416185106628.png" alt="image-20200416185106628" style="zoom:67%;" />

加载、验证、准备、初始化和卸载这 5 个阶段的顺序是确定的，类的加载过程必须按照这种顺序按部就班地开始（注意是“开始”，而不是“进行”或“完成”），而解析阶段则不一定：它在某些情况下可以在初始化后再开始，这是为了支持 Java 语言的运行时绑定。

- 加载：根据查找路径找到相应的 class 文件然后导入；

- 验证：检查加载的 class 文件的正确性；

- 准备：给类中的静态变量分配内存空间；

- 解析：虚拟机将常量池中的符号引用替换成直接引用的过程。符号引用就理解为一个标示，而在直接引用直接指向内存中的地址；

- 初始化：对静态变量和静态代码块执行初始化工作。

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

-  注意以下几种情况不会执行类初始化：

（1）通过子类引用父类的静态字段，只会触发父类的初始化，而不会触发子类的初始化。

（2）定义对象数组，不会触发该类的初始化。

（3）常量在编译期间会存入调用类的常量池中，本质上并没有直接引用定义常量的类，不会触发定义常量所在的类。

（4）通过类名获取 Class 对象，不会触发类的初始化。

（5）通过 Class.forName 加载指定类时，如果指定参数 initialize 为 false 时，也不会触发类初始化，其实这个参数是告诉虚拟机，是否要对类进行初始化。

（6）通过 ClassLoader 默认的 loadClass 方法，也不会触发初始化动作。

### 双亲委派模型

在介绍双亲委派模型之前先说下类加载器。对于任意一个类，都需要由加载它的类加载器和这个类本身一同确立在 JVM 中的唯一性，每一个类加载器，都有一个独立的类名称空间。类加载器就是根据指定全限定名称将 class 文件加载到 JVM 内存，然后再转化为 class 对象。

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200730214141999.png" alt="image-20200730214141999" style="zoom:50%;" />

类加载器分类：

- 启动类加载器（Bootstrap ClassLoader），是虚拟机自身的一部分，用来加载Java_HOME/lib/目录中的，或者被 -Xbootclasspath 参数所指定的路径中并且被虚拟机识别的类库；
- 扩展类加载器（Extension ClassLoader）：负责加载\lib\ext目录或Java. ext. dirs系统变量指定的路径中的所有类库；
- 应用程序类加载器（Application ClassLoader）。负责加载用户类路径（classpath）上的指定类库，我们可以直接使用这个类加载器。一般情况，如果我们没有自定义类加载器默认就是用这个加载器。
- 用户自定义类加载器

双亲委派模型：如果一个类加载器收到了类加载的请求，它首先不会自己去加载这个类，而是把这个请求委派给父类加载器去完成，每一层的类加载器都是如此，这样所有的加载请求都会被传送到顶层的启动类加载器中，只有当父加载无法完成加载请求（它的搜索范围中没找到所需的类）时，子加载器才会尝试去加载类。

当一个类收到了类加载请求时，不会自己先去加载这个类，而是将其委派给父类，由父类去加载，如果此时父类不能加载，反馈给子类，由子类去完成类的加载。

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

### 对象的创建过程

（1）JVM遇到一条新建对象的指令时首先去检查这个指令的参数是否能在常量池中定义到一个类的符号引用。然后加载这个类（类加载过程在后边讲）

（2）为对象分配内存。一种办法“指针碰撞”、一种办法“空闲列表”，最终常用的办法“本地线程缓冲分配(TLAB)”

（3）将除对象头外的对象内存空间初始化为0

（4）对对象头进行必要设置

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200823181706691.png" alt="image-20200823181706691" style="zoom: 50%;" />

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200731145955947.png" alt="image-20200731145955947" style="zoom:50%;" />

### 对象的结构

Java对象由三个部分组成：对象头、实例数据、对齐填充。

对象头由两部分组成，第一部分存储对象自身的运行时数据：哈希码、GC分代年龄、锁标识状态、线程持有的锁、偏向线程ID（一般占32/64 bit）。第二部分是指针类型，指向对象的类元数据类型（即对象代表哪个类）。如果是数组对象，则对象头中还有一部分用来记录数组长度。

实例数据用来存储对象真正的有效信息（包括父类继承下来的和自己定义的）

对齐填充：JVM要求对象起始地址必须是8字节的整数倍（8字节对齐 )

### 对象的访问

- 句柄访问方式

堆中需要有一块叫做“句柄池”的内存空间，句柄中包含了对象实例数据与类型数据各自的具体地址信息。

引用类型的变量存放的是该对象的句柄地址（reference）。访问对象时，首先需要通过引用类型的变量找到该对象的句柄，然后根据句柄中对象的地址找到对象。

优势：引用中存储的是稳定的句柄地址，在对象被移动（垃圾收集时移动对象是非常普遍的行为）时只会改变句柄中的实例数据指针，而引用本身不需要修改。 

- 直接指针访问方式

引用类型的变量直接存放对象的地址，从而不需要句柄池，通过引用能够直接访问对象。但对象所在的内存空间需要额外的策略存储对象所属的类信息的地址。 

优势：速度更快，节省了一次指针定位的时间开销。由于对象的访问在`Java`中非常频繁，因此这类开销积少成多后也是非常可观的执行成本。HotSpot 中采用的就是这种方式。 

### 对象的分配

（1）对象优先分配在Eden区，如果Eden区没有足够的空间时，虚拟机执行一次Minor GC。

（2）大对象直接进入老年代（大对象是指需要大量连续内存空间的对象）。这样做的目的是避免在Eden区和两个Survivor区之间发生大量的内存拷贝（新生代采用复制算法收集内存）。

（3）长期存活的对象进入老年代。虚拟机为每个对象定义了一个年龄计数器，如果对象经过了1次Minor GC那么对象会进入Survivor区，之后每经过一次Minor GC那么对象的年龄加1，知道达到阀值对象进入老年区。

（4） 动态判断对象的年龄。如果Survivor区中相同年龄的所有对象大小的总和大于Survivor空间的一半，年龄大于或等于该年龄的对象可以直接进入老年代。

（5） 空间分配担保。每次进行Minor GC时，JVM会计算Survivor区移至老年区的对象的平均大小，如果这个值大于老年区的剩余值大小则进行一次Full GC，如果小于检查HandlePromotionFailure设置，如果true则只进行Monitor GC,如果false则进行Full GC

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

### 那些可以作为GC ROOT

1、栈中的引用对象。

2、方法区中类静态属性引用的对象。

3、方法区中常量引用的对象。

4、栈中JNI（Java Native Interface）java本地接口中引用的对象。

### 什么情况会触发FULL GC

1. 旧生代空间不足
旧生代空间只有在新生代对象转入及创建为大对象、大数组时才会出现不足的现象，当执行Full GC后空间仍然不足，则抛出如下错误：java.lang.OutOfMemoryError: Java heap space 
为避免以上两种状况引起的FullGC，调优时应尽量做到让对象在Minor GC阶段被回收、让对象在新生代多存活一段时间及不要创建过大的对象及数组。

2. Permanet Generation（永久代）空间满
PermanetGeneration中存放的为一些class的信息等，当系统中要加载的类、反射的类和调用的方法较多时，Permanet Generation可能会被占满，在未配置为采用CMS GC的情况下会执行Full GC。如果经过Full GC仍然回收不了，那么JVM会抛出如下错误信息：
java.lang.OutOfMemoryError: PermGen space 
为避免Perm Gen占满造成Full GC现象，可采用的方法为增大Perm Gen空间或转为使用CMS GC。
3. CMS GC时出现promotion failed（担保：s1s2--old）和concurrent mode failure
对于采用CMS进行旧生代GC的程序而言，尤其要注意GC日志中是否有promotion failed和concurrent mode failure两种状况，当这两种状况出现时可能会触发Full GC。
promotionfailed是在进行Minor GC时，survivor space放不下、对象只能放入旧生代，而此时旧生代也放不下造成的；concurrent mode failure是在执行CMS GC的过程中同时有对象要放入旧生代，而此时旧生代空间不足造成的。
应对措施为：增大survivorspace、旧生代空间或调低触发并发GC的比率，但在JDK 5.0+、6.0+的版本中有可能会由于JDK的bug29导致CMS在remark完毕后很久才触发sweeping动作。对于这种状况，可通过设置-XX:CMSMaxAbortablePrecleanTime=5（单位为ms）来避免。
4. 统计得到的Minor GC晋升到旧生代的平均大小大于旧生代的剩余空间
这是一个较为复杂的触发情况，Hotspot为了避免由于新生代对象晋升到旧生代导致旧生代空间不足的现象，在进行Minor GC时，做了一个判断，如果之前统计所得到的Minor GC晋升到旧生代的平均大小大于旧生代的剩余空间，那么就直接触发Full GC。
例如程序第一次触发MinorGC后，有6MB的对象晋升到旧生代，那么当下一次Minor GC发生时，首先检查旧生代的剩余空间是否大于6MB，如果小于6MB，则执行Full GC。
当新生代采用PSGC时，方式稍有不同，PS GC是在Minor GC后也会检查，例如上面的例子中第一次Minor GC后，PS GC会检查此时旧生代的剩余空间是否大于6MB，如小于，则触发对旧生代的回收。
除了以上4种状况外，对于使用RMI来进行RPC或管理的Sun JDK应用而言，默认情况下会一小时执行一次Full GC。可通过在启动时通过- java-Dsun.rmi.dgc.client.gcInterval=3600000来设置Full GC执行的间隔时间或通过-XX:+ DisableExplicitGC来禁止RMI调用System.gc。

## 设计模式

### 创建型模式

#### 单例模式

##### Ⅰ 懒汉式-线程不安全

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

##### Ⅱ 饿汉式-线程安全

```java
private static Singleton uniqueInstance = new Singleton();
```

##### Ⅲ 懒汉式-线程安全

```java
public static synchronized Singleton getUniqueInstance() {
    if (uniqueInstance == null) {
        uniqueInstance = new Singleton();
    }
    return uniqueInstance;
}
```

##### Ⅳ 双重校验锁-线程安全

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

##### Ⅴ 静态内部类实现

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

##### Ⅵ 枚举实现

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

#### 简单工厂模式

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

#### 工厂方法

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



#### 抽象工厂

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

#### 生成器

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

#### 原型模式

 使用原型实例指定要创建对象的类型，通过复制这个原型来创建新对象。 

### 结构型模式

#### 代理模式

#### 适配器模式

#### 桥接模式

#### 装饰模式

#### 外观模式

#### 享元模式

#### 组合模式

### 行为型模式

#### 模板方法模

#### 策略模式

#### 命令模式

#### 责任链模式

#### 状态模式

#### 观察者模式

#### 中介者模式

#### 迭代器模

#### 访问者模

#### 备忘录模式

#### 解释器模式

## 操作系统

### 进程、线程、协程

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

**进程与线程的选择取决以下几点**：

1. 需要频繁创建销毁的优先使用线程；因为对进程来说创建和销毁一个进程代价是很大的。
2. 线程的切换速度快，所以在需要大量计算，切换频繁时用线程，还有耗时的操作使用线程可提高应用程序的响应
3. 因为对CPU系统的效率使用上线程更占优，所以可能要发展到多机分布的用进程，多核分布用线程；
4. 并行操作时使用线程，如C/S架构的服务器端并发线程响应用户的请求；
5. 需要更稳定安全时，适合选择进程；需要速度时，选择线程更好。

#### 守护进程（待完成）

**守护进程**是运行在后台的一种特殊进程，它是独立于控制终端的，并周期性地执行某些任务。

#### 进程通信方式

**管道**

- 管道是半双工的，数据只能向一个方向流动；如果需要双方通信时，需要建立起两个管道。 
- 管道只能用于父子进程或者兄弟进程之间或者说具有亲缘关系的进程； 
- 管道对于管道两端的进程而言，就是一个文件，但它不是普通的文件，它不属于某种文件系统，只存在与内存中。 
- 管道的实质是一个内核缓冲区，进程以先进先出的方式从缓冲区存取数据，管道一端的进程顺序的将数据写入缓冲区，另一端的进程则顺序的读出数据。该缓冲区可以看做是一个循环队列，读和写的位置都是自动增长的，不能随意改变，一个数据只能被读一次，读出来以后在缓冲区就不复存在了。当缓冲区读空或者写满时，有一定的规则控制相应的读进程或者写进程进入等待队列，当空的缓冲区有新数据写入或者满的缓冲区有数据读出来时，就唤醒等待队列中的进程继续读写。 
- 管道的主要局限性正体现在它的特点上，比如只支持单向数据流，只能用于具有亲缘关系的进程之间，没有名字，管道的缓冲区是有限的等等。 

**命名管道**

这种管道也叫`FIFO`。命名管道不同于管道的地方，在于它提供了一个路径名与之关联，以命名管道的文件形式存在于文件系统中，这样，即使与命名管道的创建进程不存在亲缘关系的进程，只要可以访问文件系统中的这个路径，就能够彼此通过命名管道相互通信。命名管道严格遵循先进先出原则的，不支持诸如数据随机定位。命名管道的名字存在于文件系统中，但内容存放在内存中。

**消息队列**

消息队列是消息的链表，具有特定的格式，它是存放在内存里面的，并且每个消息队列都有唯一的标识。消息队列允许一个或多个进程向它写入与读取消息，所以，利用消息队列，一个进程可以将一个数据块发送到另一个进程，每个数据块都有一个类型，接收进程可以独立地接收含有不同类型的数据结构，这个过程是异步的，我们可以通过发送消息来避免命名管道的同步和阻塞问题。但消息队列的数据块有一个最大长度的大小限制。

**共享内存**

- 共享内存是针对其他通信机制运行效率较低而设计的，它可以让多个进程可以可以直接读写同一块内存空间，是最快的`IPC`形式。 
- 为了在多个进程间交换信息，内核专门留出了一块内存区，可以由需要访问的进程将其映射到自己的私有地址空间。进程就可以直接读写这一块内存而不需要进行数据的拷贝，从而大大提高效率。 
- 由于多个进程共享一段内存，因此需要依靠某种同步机制来达到进程间的同步和互斥。 

**信号量**

信号量是一个计数器，可以用来控制多个进程对共享资源的访问。它是一种类似于锁的机制，就是防止某进程正在访问共享资源时，其他进程也访问该资源。

**Socket**

- `Socket`就是套接字，套接字也是一种通信机制，凭借这种机制，可以让不在同一台主机上的两个进程，通过网络进行通信，一般可以用在客户端和服务器之间的通信。 
- 实际上，`Socket` 是在应用层和传输层之间的一个抽象层，它把 `TCP`/IP 协议的传输层里面复杂的操作，抽象为几个简单的接口，供应用层调用实现进程在网络中的通信。

**五种通讯方式总结**

1. 管道：速度慢，容量有限，只有父子进程能通讯   
2. FIFO：任何进程间都能通讯，但速度慢   
3. 消息队列：容量受到系统限制，且要注意第一次读的时候，要考虑上一次没有读完数据的问题   
4. 信号量：不能传递复杂消息，只能用来同步   
5. 共享内存区：能够很容易控制容量，速度快，但要保持同步，比如一个进程在写的时候，另一个进程要注意读写的问题，相当于线程中的线程安全，当然，共享内存区同样可以用作线程间通讯，不过没这个必要，线程间本来就已经共享了同一进程内的一块内存
6. socket（待完成）

#### 进程同步(P|V操作)

同步和异步关注的是**消息通信机制** (synchronous communication/ asynchronous communication)。

同步，就是调用某个东西是，调用方得等待这个调用返回结果才能继续往后执行。

异步，和同步相反 调用方不会理解得到结果，而是在调用发出后调用者可用继续执行后续操作，被调用者通过状体来通知调用者，或者通过回掉函数来处理这个调用

- 临界区

  临界区是一段代码，在临界区内进程将访问临界资源。任何时候最多只有一个进程可以进入临界区，也就是说，临界区具有排他性。所以，为了互斥访问临界资源，每个进程在进入临界区之前，需要先进行检查。

- 互斥量

  就是使用一个互斥的变量来直接制约多个进程，每个进程只有拥有这个变量才具有访问公共资源的权限，因为互斥量只有一个，所以能保证资源的正确访问。

- 信号量

  信号量（`Semaphore`）是一个整型变量，可以对其执行自增和自减操作，自减操作通常也叫做`P`操作，自增操作也称为`V`操作。这两个操作需要被设计成原语，是不可分割，通常的做法是在执行这些操作的时候屏蔽中断。进程使用这两个操作进行同步。

  对于`P`操作，如果执行操作后信号量小于 `0`，那么执行该操作的进程就会阻塞，否则继续执行； 

  对于`V`操作，如果操作之后的信号量小于等于`0`，那么就会从阻塞队列唤醒一个进程。 

- 管程

  管程使用的是面向对象思想，将表示共享资源的数据结构还有相关的操作，包括同步机制，都集中并封装到一起。所有进程都只能通过管程间接访问临界资源，而管程只允许一个进程进入并执行操作，从而实现进程互斥。管程中设置了多个条件变量，表示多个进程被阻塞或挂起的条件。对条件变量执行 `wait()` 操作会导致调用进程阻塞，把管程让出来给另一个进程持有。`signal()` 操作用于唤醒被阻塞的进程。管程有一个重要特性，就是在一个时刻只能有一个进程使用管程。进程在无法继续执行的时候不能一直占用管程，否则其它进程永远不能使用管程。

- 同步机制应遵循的规则
  - **空闲让进**：当临界资源处于空闲状态，应允许一个请求进入临界区的进程立即进入临界区。
  - **忙则等待**：进程正在访问某临界资源则不允许其它的进程再进入到临界区去访问这个临界资源，而是让它等待。
  - **有限等待**：进程在等待进入临界区访问临界资源时，应该限制这个等待的时间。
  - **让权等待**：权是指处理机的使用权。

#### 线程同步

 **线程同步方式：** 

> 为什么需要线程同步：线程有时候会和其他线程共享一些资源，比如内存、数据库等。当多个线程同时读写同一份共享资源的时候，可能会发生冲突。因此需要线程的同步，多个线程按顺序访问资源。

- **互斥量** Mutex：互斥量是内核对象，只有拥有互斥对象的线程才有访问互斥资源的权限。因为互斥对象只有一个，所以可以保证互斥资源不会被多个线程同时访问；当前拥有互斥对象的线程处理完任务后必须将互斥对象交出，以便其他线程访问该资源；
- **信号量** Semaphore：信号量是内核对象，它允许同一时刻多个线程访问同一资源，但是需要控制同一时刻访问此资源的最大线程数量。信号量对象保存了**最大资源计数**和**当前可用资源计数**，每增加一个线程对共享资源的访问，当前可用资源计数就减1，只要当前可用资源计数大于0，就可以发出信号量信号，如果为0，则将线程放入一个队列中等待。线程处理完共享资源后，应在离开的同时通过`ReleaseSemaphore`函数将当前可用资源数加1。如果信号量的取值只能为0或1，那么信号量就成为了互斥量；
- **事件** Event：允许一个线程在处理完一个任务后，主动唤醒另外一个线程执行任务。事件分为手动重置事件和自动重置事件。手动重置事件被设置为激发状态后，会唤醒所有等待的线程，而且一直保持为激发状态，直到程序重新把它设置为未激发状态。自动重置事件被设置为激发状态后，会唤醒**一个**等待中的线程，然后自动恢复为未激发状态。
- **临界区** Critical Section：任意时刻只允许一个线程对临界资源进行访问。拥有临界区对象的线程可以访问该临界资源，其它试图访问该资源的线程将被挂起，直到临界区对象被释放。

#### 进程调度算法

- 先来先去服务
- 时间片轮转法
- 多级反馈队列算法
- 最短进程优先
- 最短剩余时间优先
- 最高响应比优先
- 多级反馈队列调度算法

### 系统调用和库函数（待完成）

### IO多路复用（待完成）



### 什么是用户态和内核态？

为了限制不同程序的访问能力，防止一些程序访问其它程序的内存数据，CPU划分了用户态和内核态两个权限等级。

- 用户态只能受限地访问内存，且不允许访问外围设备，没有占用CPU的能力，CPU资源可以被其它程序获取；
- 内核态可以访问内存所有数据以及外围设备，也可以进行程序的切换。

所有用户程序都运行在用户态，但有时需要进行一些内核态的操作，比如从硬盘或者键盘读数据，这时就需要进行系统调用，使用**陷阱指令**，CPU切换到内核态，执行相应的服务，再切换为用户态并返回系统调用的结果。

##### 为什么要分用户态和内核态？

<details open="" style="box-sizing: border-box; display: block; margin-top: 0px; margin-bottom: 16px;"><summary style="box-sizing: border-box; display: list-item; cursor: pointer;">展开</summary><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 16px;">（我自己的见解：）</p><ul style="box-sizing: border-box; padding-left: 2em; margin-top: 0px; margin-bottom: 16px;"><li style="box-sizing: border-box;">安全性：防止用户程序恶意或者不小心破坏系统/内存/硬件资源；</li><li style="box-sizing: border-box; margin-top: 0.25em;">封装性：用户程序不需要实现更加底层的代码；</li><li style="box-sizing: border-box; margin-top: 0.25em;">利于调度：如果多个用户程序都在等待键盘输入，这时就需要进行调度；统一交给操作系统调度更加方便。</li></ul></details>

##### 如何从用户态切换到内核态？

<details open="" style="box-sizing: border-box; display: block; margin-top: 0px; margin-bottom: 16px;"><summary style="box-sizing: border-box; display: list-item; cursor: pointer;">展开</summary><ul style="box-sizing: border-box; padding-left: 2em; margin-top: 0px; margin-bottom: 16px;"><li style="box-sizing: border-box;">系统调用：比如读取命令行输入。本质上还是通过中断实现</li><li style="box-sizing: border-box; margin-top: 0.25em;">用户程序发生异常时：比如缺页异常</li><li style="box-sizing: border-box; margin-top: 0.25em;">外围设备的中断：外围设备完成用户请求的操作之后，会向CPU发出中断信号，这时CPU会转去处理对应的中断处理程序</li></ul></details>

### 分页和分段有什么区别？

- 页式存储：用户空间划分为大小相等的部分称为页（page），内存空间划分为同样大小的区域称为页框，分配时以页为单位，按进程需要的页数分配，逻辑上相邻的页物理上不一定相邻；
- 段式存储：用户进程地址空间按照自身逻辑关系划分为若干个段（segment）（如代码段，数据段，堆栈段），内存空间被动态划分为长度不同的区域，分配时以段为单位，每段在内存中占据连续空间，各段可以不相邻；
- 段页式存储：用户进程先按段划分，段内再按页划分，内存划分和分配按页。

区别：

- 目的不同：分页的目的是管理内存，用于虚拟内存以获得更大的地址空间；分段的目的是满足用户的需要，使程序和数据可以被划分为逻辑上独立的地址空间；
- 大小不同：段的大小不固定，由其所完成的功能决定；页的大小固定，由系统决定；
- 地址空间维度不同：分段是二维地址空间（段号+段内偏移），分页是一维地址空间（每个进程一个页表/多级页表，通过一个逻辑地址就能找到对应的物理地址）；
- 分段便于信息的保护和共享；分页的共享收到限制；
- 碎片：分段没有内碎片，但会产生外碎片；分页没有外碎片，但会产生内碎片（一个页填不满）

### 什么是虚拟内存？

每个程序都拥有自己的地址空间，这个地址空间被分成大小相等的页，这些页被映射到物理内存；但不需要所有的页都在物理内存中，当程序引用到不在物理内存中的页时，由操作系统将缺失的部分装入物理内存。这样，对于程序来说，逻辑上似乎有很大的内存空间，只是实际上有一部分是存储在磁盘上，因此叫做虚拟内存。

虚拟内存的优点是让程序可以获得更多的可用内存。

##### 如何进行地址空间到物理内存的映射？

<details open="" style="box-sizing: border-box; display: block; margin-top: 0px; margin-bottom: 16px;"><summary style="box-sizing: border-box; display: list-item; cursor: pointer;">展开</summary><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 16px;"><strong style="box-sizing: border-box; font-weight: 600;">内存管理单元</strong>（MMU）管理着逻辑地址和物理地址的转换，其中的页表（Page table）存储着页（逻辑地址）和页框（物理内存空间）的映射表，页表中还包含包含有效位（是在内存还是磁盘）、访问位（是否被访问过）、修改位（内存中是否被修改过）、保护位（只读还是可读写）。逻辑地址：页号+页内地址（偏移）；每个进程一个页表，放在内存，页表起始地址在PCB/寄存器中。</p></details>

### 死锁

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

#### **死锁检测和恢复**

可以允许系统进入死锁状态，但会维护一个系统的资源分配图，定期调用死锁检测算法来检测途中是否存在死锁，检测到死锁发生后，采取死锁恢复算法进行恢复。

死锁检测方法如下：

- 在资源分配图中，找到不会阻塞又不独立的进程结点，使该进程获得其所需资源并运行，运行完毕后，再释放其所占有的全部资源。也就是消去该进程结点的请求边和分配边。 
- 使用上面的算法进行一系列简化，若能消去所有边，则表示不会出现死锁，否则会出现死锁。 

检测到死锁后，就需要解决死锁。目前操作系统中主要采用如下几种方法：

- 取消所有死锁相关线程，简单粗暴，但也确实是最常用的 
- 把每个死锁线程回滚到某些检查点，然后重启 
- 连续取消死锁线程直到死锁解除，顺序基于特定最小代价原则 
- 连续抢占资源直到死锁解除

#### 死锁有哪些处理方法？

<details open="" style="box-sizing: border-box; display: block; margin-top: 0px; margin-bottom: 16px;"><summary style="box-sizing: border-box; display: list-item; cursor: pointer;">鸵鸟策略</summary><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 16px;">直接忽略死锁。因为解决死锁问题的代价很高，因此鸵鸟策略这种不采取任务措施的方案会获得更高的性能。当发生死锁时不会对用户造成多大影响，或发生死锁的概率很低，可以采用鸵鸟策略。</p></details>

<details open="" style="box-sizing: border-box; display: block; margin-top: 0px; margin-bottom: 16px;"><summary style="box-sizing: border-box; display: list-item; cursor: pointer;">死锁预防</summary><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 16px;">基本思想是破坏形成死锁的四个必要条件：</p><ul style="box-sizing: border-box; padding-left: 2em; margin-top: 0px; margin-bottom: 16px;"><li style="box-sizing: border-box;">破坏互斥条件：允许某些资源同时被多个进程访问。但是有些资源本身并不具有这种属性，因此这种方案实用性有限；</li><li style="box-sizing: border-box; margin-top: 0.25em;">破坏占有并等待条件：<ul style="box-sizing: border-box; padding-left: 2em; margin-top: 0px; margin-bottom: 0px;"><li style="box-sizing: border-box;">实行资源预先分配策略（当一个进程开始运行之前，必须一次性向系统申请它所需要的全部资源，否则不运行）；</li><li style="box-sizing: border-box; margin-top: 0.25em;">或者只允许进程在没有占用资源的时候才能申请资源（申请资源前先释放占有的资源）；</li><li style="box-sizing: border-box; margin-top: 0.25em;">缺点：很多时候无法预知一个进程所需的全部资源；同时，会降低资源利用率，降低系统的并发性；</li></ul></li><li style="box-sizing: border-box; margin-top: 0.25em;">破坏非抢占条件：允许进程强行抢占被其它进程占有的资源。会降低系统性能；</li><li style="box-sizing: border-box; margin-top: 0.25em;">破坏循环等待条件：对所有资源统一编号，所有进程对资源的请求必须按照序号递增的顺序提出，即只有占有了编号较小的资源才能申请编号较大的资源。这样避免了占有大号资源的进程去申请小号资源。</li></ul></details>

<details open="" style="box-sizing: border-box; display: block; margin-top: 0px; margin-bottom: 16px;"><summary style="box-sizing: border-box; display: list-item; cursor: pointer;">死锁避免</summary><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 16px;">动态地检测资源分配状态，以确保系统处于安全状态，只有处于安全状态时才会进行资源的分配。所谓安全状态是指：即使所有进程突然请求需要的所有资源，也能存在某种对进程的资源分配顺序，使得每一个进程运行完毕。</p><blockquote style="box-sizing: border-box; margin: 0px 0px 16px; padding: 0px 1em; color: rgb(106, 115, 125); border-left: 0.25em solid rgb(223, 226, 229);"><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 0px;">银行家算法</p></blockquote></details>

<details open="" style="box-sizing: border-box; display: block; margin-top: 0px; margin-bottom: 16px;"><summary style="box-sizing: border-box; display: list-item; cursor: pointer;">死锁解除</summary><blockquote style="box-sizing: border-box; margin: 0px 0px 16px; padding: 0px 1em; color: rgb(106, 115, 125); border-left: 0.25em solid rgb(223, 226, 229);"><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 0px;">如何检测死锁：检测有向图是否存在环；或者使用类似死锁避免的检测算法。</p></blockquote><p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 16px;">死锁解除的方法：</p><ul style="box-sizing: border-box; padding-left: 2em; margin-top: 0px; margin-bottom: 16px;"><li style="box-sizing: border-box;">利用抢占：挂起某些进程，并抢占它的资源。但应防止某些进程被长时间挂起而处于饥饿状态；</li><li style="box-sizing: border-box; margin-top: 0.25em;">利用回滚：让某些进程回退到足以解除死锁的地步，进程回退时自愿释放资源。要求系统保持进程的历史信息，设置还原点；</li><li style="box-sizing: border-box; margin-top: 0.25em;">利用杀死进程：强制杀死某些进程直到死锁解除为止，可以按照优先级进行。</li></ul></details>

### 磁盘调度算法（待完成）



### 虚拟内存

虚拟内存就是说，让物理内存扩充成更大的逻辑内存，从而让程序获得更多的可用内存。虚拟内存使用部分加载的技术，让一个进程或者资源的某些页面加载进内存，从而能够加载更多的进程，甚至能加载比内存大的进程，这样看起来好像内存变大了，这部分内存其实包含了磁盘或者硬盘，并且就叫做虚拟内存。

### 段式存储、页式存储、段页式存储

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

- **页面替换算法（待完成）**

  

### Linux文件系统（待完成）

### 软链接、硬链接

硬链接:文件A是文件B的硬链接，则A的目录项中的inode节点号与B节点的inode节点号相同，既一个inode节点对应两个不同的文件名，两个文件名指向一个同一个文件,A和B对于文件系统其实是完全相同的. 如果删除了其中一个，对另外一个没有影响. 每增加一个文件名，inode节点上的链接数增加一，每删除一个对应的文件名，inode节点上的链接数减一，直到为0，inode节点和对应数据块被回收. 对应上图你就可以理解硬链接的过程。

特点：不能对目录创建硬链接，原因有几种，最重要的是：文件系统不能存在链接环，存在环的后果会导致例如文件遍历等操作的混乱；不能对不同的文件系统创建硬链接，既两个文件名要在相同的文件系统下；不能对不存在的文件创建硬链接，由原理即可知真相。

软链接: A是B的软链接，A的目录项中的inode节点号与B的目录项中的inode节点号不同，A和B指向的是两个不同的inode，继而指向两块不同的数据块，但是A的数据块存放的只是B的路径名. A和B之间 "主从"关系，如果B被删除了，A仍然存在,但指向的是一个无效的链接。

特点可以对目录创建软链接，遍历操作会忽略目录的软链接；可以跨越文件系统；可以对不存在的文件创建软链接，因为放的只是一个字符串，至于这个字符串是不是对于一个实际的文件，就是另外一回事了。

### 线程从创建到死亡

1. 新建( new )：新创建了一个线程对象。

2. 可运行( runnable )：线程对象创建后，其他线程(比如 main 线程）调用了该对象 的 start ()方法。该状态的线程位于可运行线程池中，等待被线程调度选中，获 取 cpu 的使用权 。

3. 运行( running )：可运行状态( runnable )的线程获得了CPU时间片 ，执行程序代码。

4. 阻塞( block )：阻塞状态是指线程因为某种原因放弃了CPU使用权，也即让出了CPU时间片 ，暂时停止运行。直到线程进入可运行( runnable )状态，才有 机会再次获得CPU时间片 转到运行( running )状态。阻塞的情况分三种：
   (一). 等待阻塞：运行( running )的线程执行 o . wait ()方法， JVM 会把该线程放 入等待队列中。
   (二). 同步阻塞：运行( running )的线程在获取对象的同步锁时，若该同步锁 被别的线程占用，则 JVM 会把该线程放入锁池( lock pool )中。
   (三). 其他阻塞: 运行( running )的线程执行 Thread . sleep ( long ms )或 t . join ()方法，或者发出了 I / O 请求时， JVM 会把该线程置为阻塞状态。 当 sleep ()状态超时、 join ()等待线程终止或者超时、或者 I / O 处理完毕时，线程重新转入可运行( runnable )状态。
5. 死亡( dead )：线程 run ()、 main () 方法执行结束，或者因异常退出了 run ()方法，则该线程结束生命周期。死亡的线程不可再次复生。 

### Linux常用命令

1. 显示文件目录命令ls    如ls
2. 改变当前目录命令cd    如cd /home
3. 建立子目录mkdir      如mkdir xiong
4. 删除子目录命令rmdir    如rmdir /mnt/cdrom
5. 删除文件命令rm      如rm /ucdos.bat
6. 文件复制命令cp      如cp /ucdos /fox
7. 获取帮助信息命令man   如man ls
8. 显示文件的内容less    如less mwm.lx
9. 重定向与管道type     如type readme>>direct，将文件readme的内容追加到文direct中

## 计算机网络

### OSI七层模型/TCP.IP四层模型/五层协议体系

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

   物理层解决如何在连接各种计算机的传输媒体上传输数据比特流，而不是指具体的传输媒体。物理层的主要任务描述为：确定与传输媒体的接口的一些特性，即：

   - 机械特性：例接口形状，大小，引线数目
   - 电气特性：例规定电压范围 ( -5V 到 +5V )
   - 功能特性：例规定 -5V 表示 0，＋5V 表示 1
   - 过程特性：也称规程特性，规定建立连接时各个相关部件的工作步骤

2. 数据链路层

   不同的网络类型，发送数据的机制不同，数据链路层就是将数据包封装成能够在不同的网络传输的帧。能够进行差错检验，但不纠错，监测处错误丢掉该帧。

   - 帧的开始和结束，透明传输，差错校验

3. 网络层

   为主机间提供数据传输服务，而运输层协议是为主机中的进程提供服务。网络层把运输层传递下来的报文段或者用户数据报封装成分组。（负责选择最佳路径 规划IP地址）路由器查看数据包目标IP地址，根据路由表为数据包选择路径。路由表中的类目可以人工添加（静态路由）也可以动态生成（动态路由）。

4. 运输层

   提供的是进程间的通用数据传输服务。由于应用层协议很多，定义通用的运输层协议就可以支持不断增多的应用层协议。运输层包括两种协议：

   - 传输控制协议 TCP，提供面向连接、可靠的数据传输服务，数据单位为报文段；
   - 用户数据报协议 UDP，提供无连接、尽最大努力的数据传输服务，数据单位为用户数据报。
   - TCP 主要提供完整性服务，UDP 主要提供及时性服务。

5. 会话层

   通过运输层（端口号：传输端口与接收端口）建立数据传输的通路。主要在你的系统之间发起会话或者接受会话请求（设备之间需要互相认识可以是IP也可以是MAC或者是主机名）

6. 表示层

   可确保一个系统的应用层所发送的信息可以被另一个系统的应用层读取。例如，PC程序与另一台计算机进行通信，其中一台计算机使用扩展二一十进制交换码（EBCDIC），而另一台则使用美国信息交换标准码（ASCII）来表示相同的字符。如有必要，表示层会通过使用一种通格式来实现多种数据格式之间的转换。 

7. 应用层

   是最靠近用户的OSI层。这一层为用户的应用程序（例如电子邮件、文件传输和终端仿真）提供网络服务。
   
   说明：五层协议没有表示层和会话层，而是将这些功能留给应用程序开发者处理。

### TCP/IP协议的概念及作用

- 概念

  TCP/IP 是因特网的通信协议，Transmission Control Protocol/Internet Protocol的简写，中译名为传输控制协议/因特网互联协议，又名网络通讯协议，是Internet最基本的协议、Internet国际互联网络的基础，由网络层的IP协议和传输层的TCP协议组成。

  tcp/ip协议家族的两个核心协议：TCP（传输控制协议）和IP（网际协议）。

  - TCP协议全称：传输控制协议，英文：Transmission Control Protocol，是基于字节流的传输层通信协议，它完成传输层所指定的功能。

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

### 运输层

#### TCP、UDP

##### 报文结构

- TCP报文结构

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200726161135825.png" alt="image-20200726161135825" style="zoom:67%;" />

- UDP报文结构

  <img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200726161258278.png" alt="image-20200726161258278" style="zoom:67%;" />

##### TCP/UDP优缺点以及区别

TCP的优点： 可靠，稳定 TCP的可靠体现在TCP在传递数据之前，会有三次握手来建立连接，而且在数据传递时，有确认、窗口、重传、拥塞控制机制，在数据传完后，还会断开连接用来节约系统资源。 TCP的缺点： 慢，效率低，占用系统资源高，易被攻击 TCP在传递数据之前，要先建连接，这会消耗时间，而且在数据传递时，确认机制、重传机制、拥塞控制机制等都会消耗大量的时间，而且要在每台设备上维护所有的传输连接，事实上，每个连接都会占用系统的CPU、内存等硬件资源。 而且，因为TCP有确认机制、三次握手机制，这些也导致TCP容易被人利用，实现DOS、DDOS、CC等攻击。

UDP的优点： 快，比TCP稍安全 UDP没有TCP的握手、确认、窗口、重传、拥塞控制等机制，UDP是一个无状态的传输协议，所以它在传递数据时非常快。没有TCP的这些机制，UDP较TCP被攻击者利用的漏洞就要少一些。但UDP也是无法避免攻击的，比如：UDP Flood攻击…… UDP的缺点： 不可靠，不稳定 因为UDP没有TCP那些可靠的机制，在数据传递时，如果网络质量不好，就会很容易丢包。 基于上面的优缺点，那么： 什么时候应该使用TCP： 当对网络通讯质量有要求的时候，比如：整个数据要准确无误的传递给对方，这往往用于一些要求可靠的应用，比如HTTP、HTTPS、FTP等传输文件的协议，POP、SMTP等邮件传输的协议。 在日常生活中，常见使用TCP协议的应用如下： 浏览器，用的HTTP FlashFXP，用的FTP Outlook，用的POP、SMTP Putty，用的Telnet、SSH QQ文件传输 ………… 什么时候应该使用UDP： 当对网络通讯质量要求不高的时候，要求网络通讯速度能尽量的快，这时就可以使用UDP。 比如，日常生活中，常见使用UDP协议的应用如下： QQ语音 QQ视频 TFTP ……

区别：

1. 基于连接与无连接；
2. 对系统资源的要求（TCP较多，UDP少）；
3. UDP程序结构较简单；
4. 流模式与数据报模式 ；TCP保证数据正确性，
5. UDP可能丢包，TCP保证数据顺序，UDP不保证。
6. UDP 是无连接的，即发送数据之前不需要建立连接。
7. UDP 使用尽最大努力交付，即不保证可靠交付，同时也不使用拥塞控制。
8. UDP 是面向报文的。UDP 没有拥塞控制，很适合多媒体通信的要求。
9. UDP 支持一对一、一对多、多对一和多对多的交互通信。
10. UDP 的首部开销小，只有 8 个字节。
11. TCP 是面向连接的运输层协议。
12. 每一条 TCP 连接只能有两个端点(endpoint)，每一条 TCP 连接只能是点对点的（一对一）。
13. TCP 提供可靠交付的服务。
14. TCP 提供全双工通信。
15. TCP是面向字节流。  
16. 首部最低20个字节。

##### TCP三次握手、四次挥手

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

#####  TCP流量控制

流量控制是为了控制发送方发送速率，保证接收方来得及接收。

接收方发送的确认报文中的窗口字段可以用来控制发送方窗口大小，从而影响发送方的发送速率。将窗口字段设置为 0，则发送方不能发送数据。

#####  拥塞控制

1. **拥塞控制的一般原理**

- 在某段时间，若对网络中某资源的需求超过了该资源所能提供的可用部分，网络的性能就要变坏——产生拥塞(congestion)。
- 出现资源拥塞的条件：对资源需求的总和 > 可用资源
- 若网络中有许多资源同时产生拥塞，网络的性能就要明显变坏，整个网络的吞吐量将随输入负荷的增大而下降。

如果网络出现拥塞，分组将会丢失，此时发送方会继续重传，从而导致网络拥塞程度更高。因此当出现拥塞时，应当控制发送方的速率。这一点和流量控制很像，但是出发点不同。流量控制是为了让接收方能来得及接收，而拥塞控制是为了降低整个网络的拥塞程度。

TCP 主要通过四种算法来进行拥塞控制：慢开始、拥塞避免、快重传、快恢复。

1. **慢开始与拥塞避免**

   发送的最初执行慢开始，令 cwnd=1，发送方只能发送 1 个报文段；当收到确认后，将 cwnd 加倍，因此之后发送方能够发送的报文段数量为：2、4、8 ...

   注意到慢开始每个轮次都将 cwnd 加倍，这样会让 cwnd 增长速度非常快，从而使得发送方发送的速度增长速度过快，网络拥塞的可能也就更高。设置一个慢启动阈值 ssthresh，当 cwnd >= ssthresh 时，进入拥塞避免，每个轮次只将 cwnd 加 1。

　　如果出现了超时，则令 ssthresh = cwnd/2，然后重新执行慢开始。

2. **快重传与快恢复**

   在接收方，要求每次接收到报文段都应该对最后一个已收到的有序报文段进行确认。例如已经接收到 M1 和 M2，此时收到 M4，应当发送对 M2 的确认。

   在发送方，如果收到三个重复确认，那么可以知道下一个报文段丢失，此时执行快重传，立即重传下一个报文段。例如收到三个 M2，则 M3 丢失，立即重传 M3。

   在这种情况下，只是丢失个别报文段，而不是网络拥塞。因此执行快恢复，令 ssthresh = cwnd/2 ，cwnd = ssthresh，注意到此时直接进入拥塞避免。慢开始和快恢复的快慢指的是 cwnd 的设定值，而不是 cwnd 的增长速率。慢开始 cwnd 设定为 1，而快恢复 cwnd 设定为 ssthresh。

3. **发送窗口的上限值**

   发送方的发送窗口的上限值应当取为接收方窗口 rwnd 和拥塞窗口 cwnd 这两个变量中较小的一个，

   即应按以下公式确定：发送窗口的上限值 = Min {rwnd, cwnd}

   当 rwnd < cwnd 时，是接收方的接收能力限制发送窗口的最大值。

   当 cwnd < rwnd 时，则是网络的拥塞限制发送窗口的最大值。

4. **流量控制和拥塞控制的区别**

- 拥塞控制所要做的都有一个前提，就是网络能够承受现有的网络负荷。
- 拥塞控制是一个全局性的过程，涉及到所有的主机、所有的路由器，以及与降低网络传输性能有关的所有因素。
- 流量控制往往指在给定的发送端和接收端之间的点对点通信量的控制。
- 流量控制所要做的就是抑制发送端发送数据的速率，以便使接收端来得及接收。
- 流量控制属于通信双方协商；拥塞控制涉及通信链路全局。
- 流量控制需要通信双方各维护一个发送窗、一个接收窗，对任意一方，接收窗大小由自身决定，发送窗大小由接收方响应的TCP报文段中窗口值确定；拥塞控制的拥塞窗口大小变化由试探性发送一定数据量数据探查网络状况后而自适应调整。
- 实际最终发送窗口 = min{流控发送窗口，拥塞窗口}。

##### RTO，RTT和超时重传

- **超时重传**

  ：发送端发送报文后若长时间未收到确认的报文则需要重发该报文。可能有以下几种情况：

  - 发送的数据没能到达接收端，所以对方没有响应。
  - 接收端接收到数据，但是ACK报文在返回过程中丢失。
  - 接收端拒绝或丢弃数据。

- **RTO**

  ：从上一次发送数据，因为长期没有收到ACK响应，到下一次重发之间的时间。就是重传间隔。

  - 通常每次重传RTO是前一次重传间隔的两倍，计量单位通常是RTT。例：1RTT，2RTT，4RTT，8RTT......
  - 重传次数到达上限之后停止重传。

- **RTT**：数据从发送到接收到对方响应之间的时间间隔，即数据报在网络中一个往返用时。大小不稳定。

### 应用层

#### URL、URI、URN区别

- URI（Uniform Resource Identifier，统一资源标识符），web服务器资源的名字，例如： index.html
- URL（Uniform Resource Locator，统一资源定位符）
- URN（Uniform Resource Name，统一资源名称），例如 urn:isbn:0-486-27557-4。

#### [HTTP/HTTPS]( https://www.jianshu.com/p/6c46ef63c407 )（待完成）

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200801111745737.png" alt="image-20200801111745737" style="zoom:50%;" />

 HTTP+加密+认证+完整性保护 = HTTPS 

**散列函数 Hash**：

**对称加密：**

**非对称加密** :

#### HTTP2.0特性（待完成）

#### 访问网页的全过程

参照《计算机网络自顶向下》

简化版：

1. 浏览器查询 DNS，获取域名对应的IP地址:具体过程包括浏览器搜索自身的DNS缓存、搜索操作系统的DNS缓存、读取本地的Host文件和向本地DNS服务器进行查询等。对于向本地DNS服务器进行查询，如果要查询的域名包含在本地配置区域资源中，则返回解析结果给客户机，完成域名解析(此解析具有权威性)；如果要查询的域名不由本地DNS服务器区域解析，但该服务器已缓存了此网址映射关系，则调用这个IP地址映射，完成域名解析（此解析不具有权威性）。如果本地域名服务器并未缓存该网址映射关系，那么将根据其设置发起递归查询或者迭代查询；
2. 浏览器获得域名对应的IP地址以后，浏览器向服务器请求建立链接，发起三次握手；
3. TCP/IP链接建立起来后，浏览器向服务器发送HTTP请求；
4. 服务器接收到这个请求，并根据路径参数映射到特定的请求处理器进行处理，并将处理结果及相应的视图返回给浏览器；
5. 浏览器解析并渲染视图，若遇到对js文件、css文件及图片等静态资源的引用，则重复上述步骤并向服务器请求这些资源；
6. 浏览器根据其请求到的资源、数据渲染页面，最终向用户呈现一个完整的页面。

#### HTTP请求报文/响应报文

##### 请求报文

HTTP请求报文由3部分组成（请求行+请求头+请求体）：

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200802155750842.png" alt="image-20200802155750842" style="zoom:50%;" />

请求行：

①是请求方法，GET和POST是最常见的HTTP方法，除此以外还包括DELETE、HEAD、OPTIONS、PUT、TRACE。

②为请求对应的URL地址，它和报文头的Host属性组成完整的请求URL。

③是协议名称及版本号。

请求头：

④是HTTP的报文头，报文头包含若干个属性，格式为“属性名:属性值”，服务端据此获取客户端的信息。

与缓存相关的规则信息，均包含在header中

请求体：

⑤是报文体，它将一个页面表单中的组件值通过param1=value1&param2=value2的键值对形式编码成一个格式化串，它承载多个请求参数的数据。不但报文体可以传递请求参数，请求URL也可以通过类似于“/chapter15/user.html? param1=value1&param2=value2”的方式传递请求参数。 

##### 响应报文

HTTP的响应报文也由三部分组成（响应行+响应头+响应体）：

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200802155814996.png" alt="image-20200802155814996" style="zoom:50%;" />

响应行：

①报文协议及版本； 
②状态码及状态描述；

响应头：

③响应报文头，也是由多个属性组成；

响应体：

④响应报文体，即我们真正要的数据

#### HTTP状态

| 状态码 | 类别                             | 原因短语                   |
| ------ | -------------------------------- | -------------------------- |
| 1XX    | Informational（信息性状态码）    | 接收的请求正在处理         |
| 2XX    | Success（成功状态码）            | 请求正常处理完毕           |
| 3XX    | Redirection（重定向状态码）      | 需要进行附加操作以完成请求 |
| 4XX    | Client Error（客户端错误状态码） | 服务器无法处理请求         |
| 5XX    | Server Error（服务器错误状态码） | 服务器处理请求出错         |

#### TCP与HTTP的区别

TCP是传输层协议，定义数据传输和连接方式的规范。握手过程中传送的包里不包含数据，三次握手完毕后，客户端与服务器才正式开始传送数据。

HTTP 超文本传送协议(Hypertext Transfer Protocol )是应用层协议，定义的是传输数据的内容的规范。

HTTP协议中的数据是利用TCP协议传输的，特点是客户端发送的每次请求都需要服务器回送响应，它是TCP协议族中的一种，默认使用 TCP 80端口。

好比网络是路，TCP是跑在路上的车，HTTP是车上的人。每个网站内容不一样，就像车上的每个人有不同的故事一样。

#### GET/PUT/POST的区别

- PUT和POST
   PUT和POST都有更改指定URI的语义.但PUT被定义为idempotent的方法，POST则不是.idempotent的方法:如果一个方法重复执行

多次，产生的效果是一样的，那就是idempotent的。也就是说：

PUT请求：如果两个请求相同，后一个请求会把第一个请求覆盖掉。（所以PUT用来改资源）

Post请求：后一个请求不会把第一个请求覆盖掉。（所以Post用来增资源）

- get和post

1、GET参数通过URL传递，POST放在Request body中。

2、GET请求会被浏览器主动cache，而POST不会，除非手动设置。

3、GET请求参数会被完整保留在浏览器历史记录里，而POST中的参数不会被保留。

4、Get 请求中有非 ASCII 字符，会在请求之前进行转码，POST不用，因为POST在Request body中，通过 MIME，也就可以传输非 ASCII 字符。

5、 一般我们在浏览器输入一个网址访问网站都是GET请求

6、HTTP的底层是TCP/IP。HTTP只是个行为准则，而TCP才是GET和POST怎么实现的基本。GET/POST都是TCP链接。GET和POST能做的事情是一样一样的。但是请求的数据量太大对浏览器和服务器都是很大负担。所以业界有了不成文规定，（大多数）浏览器通常都会限制url长度在2K个字节，而（大多数）服务器最多处理64K大小的url。

7、GET产生一个TCP数据包；POST产生两个TCP数据包。对于GET方式的请求，浏览器会把http header和data一并发送出去，服务器响应200（返回数据）；而对于POST，浏览器先发送header，服务器响应100 continue，浏览器再发送data，服务器响应200 ok（返回数据）。

8、在网络环境好的情况下，发一次包的时间和发两次包的时间差别基本可以无视。而在网络环境差的情况下，两次包的TCP在验证数据包完整性上，有非常大的优点。但并不是所有浏览器都会在POST中发送两次包，Firefox就只发送一次。

**说完原理性的问题，我们从表面上来看看GET和POST的区别：**

- GET是从服务器上获取数据，POST是向服务器传送数据。 GET和 POST只是一种传递数据的方式，GET也可以把数据传到服务器，他们的本质都是发送请求和接收结果。只是组织格式和数据量上面有差别，http协议里面有介绍
- GET是把参数数据队列加到提交表单的ACTION属性所指的URL中，值和表单内各个字段一一对应，在URL中可以看到。POST是通过HTTP POST机制，将表单内各个字段与其内容放置在HTML HEADER内一起传送到ACTION属性所指的URL地址。用户看不到这个过程。 因为GET设计成传输小数据，而且最好是不修改服务器的数据，所以浏览器一般都在地址栏里面可以看到，但POST一般都用来传递大数据，或比较隐私的数据，所以在地址栏看不到，能不能看到不是协议规定，是浏览器规定的。
- 对于GET方式，服务器端用Request.QueryString获取变量的值，对于POST方式，服务器端用Request.Form获取提交的数据。 没明白，怎么获得变量和你的服务器有关，和GET或POST无关，服务器都对这些请求做了封装
- GET传送的数据量较小，不能大于2KB。POST传送的数据量较大，一般被默认为不受限制。但理论上，IIS4中最大量为80KB，IIS5中为100KB。 POST基本没有限制，我想大家都上传过文件，都是用POST方式的。只不过要修改form里面的那个type参数
- GET安全性非常低，POST安全性较高。 如果没有加密，他们安全级别都是一样的，随便一个监听器都可以把所有的数据监听到。

#### HTTP无状态与无连接性

##### 无连接

**无连接的含义是限制每次连接只处理一个请求。服务器处理完客户的请求，并收到客户的应答后，即断开连接。采用这种方式可以节省传输时间。**

早期这么做的原因是 HTTP 协议产生于互联网，因此服务器需要处理同时面向全世界数十万、上百万客户端的网页访问，但每个客户端(即浏览器)与服务器之间交换数据的间歇性较大(即传输具有突发性、瞬时性)，并且网页浏览的联想性、发散性导致两次传送的数据关联性很低，大部分通道实际上会很空闲、无端占用资源。因此 HTTP 的设计者有意利用这种特点将协议设计为请求时建连接、请求完释放连接，以尽快将资源释放出来服务其他客户端。

随着时间的推移，网页变得越来越复杂，里面可能嵌入了很多图片，这时候每次访问图片都需要建立一次 TCP 连接就显得很低效。后来，Keep-Alive 被提出用来解决这效率低的问题。

Keep-Alive 功能使客户端到服务器端的连接持续有效，当出现对服务器的后继请求时，Keep-Alive 功能避免了建立或者重新建立连接。市场上的大部分 Web 服务器，包括 iPlanet、IIS 和 Apache，都支持 HTTP Keep-Alive。对于提供静态内容的网站来说，这个功能通常很有用。但是，对于负担较重的网站来说，这里存在另外一个问题：虽然为客户保留打开的连接有一定的好处，但它同样影响了性能，因为在处理暂停期间，本来可以释放的资源仍旧被占用。当Web服务器和应用服务器在同一台机器上运行时，Keep-Alive 功能对资源利用的影响尤其突出。

这样一来，客户端和服务器之间的 HTTP 连接就会被保持，不会断开(超过 Keep-Alive 规定的时间，意外断电等情况除外)，当客户端发送另外一个请求时，就使用这条已经建立的连接。

##### 无状态

**无状态是指协议对于事务处理没有记忆能力，服务器不知道客户端是什么状态。即我们给服务器发送 HTTP 请求之后，服务器根据请求，会给我们发送数据过来，但是，发送完，不会记录任何信息。**

HTTP 是一个无状态协议，这意味着每个请求都是独立的，Keep-Alive 没能改变这个结果。

缺少状态意味着如果后续处理需要前面的信息，则它必须重传，这样可能导致每次连接传送的数据量增大。另一方面，在服务器不需要先前信息时它的应答就较快。

HTTP 协议这种特性有优点也有缺点，优点在于解放了服务器，每一次请求“点到为止”不会造成不必要连接占用，缺点在于每次请求会传输大量重复的内容信息。

客户端与服务器进行动态交互的 Web 应用程序出现之后，HTTP 无状态的特性严重阻碍了这些应用程序的实现，毕竟交互是需要承前启后的，简单的购物车程序也要知道用户到底在之前选择了什么商品。于是，两种用于保持 HTTP 连接状态的技术就应运而生了，一个是 Cookie，而另一个则是 Session。

Cookie可以保持登录信息到用户下次与服务器的会话，换句话说，下次访问同一网站时，用户会发现不必输入用户名和密码就已经登录了(当然，不排除用户手工删除Cookie)。而还有一些Cookie在用户退出会话的时候就被删除了，这样可以有效保护个人隐私。

Cookies 最典型的应用是判定注册用户是否已经登录网站，用户可能会得到提示，是否在下一次进入此网站时保留用户信息以便简化登录手续，这些都是 Cookies 的功用。另一个重要应用场合是“购物车”之类处理。用户可能会在一段时间内在同一家网站的不同页面中选择不同的商品，这些信息都会写入 Cookies，以便在最后付款时提取信息。

与 Cookie 相对的一个解决方案是 Session，它是通过服务器来保持状态的。

当客户端访问服务器时，服务器根据需求设置 Session，将会话信息保存在服务器上，同时将标示 Session 的 SessionId 传递给客户端浏览器，浏览器将这个 SessionId 保存在内存中，我们称之为无过期时间的 Cookie。浏览器关闭后，这个 Cookie 就会被清掉，它不会存在于用户的 Cookie 临时文件。

以后浏览器每次请求都会额外加上这个参数值，服务器会根据这个 SessionId，就能取得客户端的数据信息。

如果客户端浏览器意外关闭，服务器保存的 Session 数据不是立即释放，此时数据还会存在，只要我们知道那个 SessionId，就可以继续通过请求获得此 Session 的信息，因为此时后台的 Session 还存在，当然我们可以设置一个 Session 超时时间，一旦超过规定时间没有客户端请求时，服务器就会清除对应 SessionId 的 Session 信息。

#### Cookie和session区别

1、数据存放位置不同du：

cookie数据存放在客户的浏览器上，session数据放在服务器上。
2、安全程度不同：

cookie不是很安全，别人可以分析存放在本地的COOKIE并进行COOKIE欺骗,考虑到安全应当使用session。
3、性能使用程度不同：

session会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能,考虑到减轻服务器性能方面，应当使用cookie。

4、数据存储大小不同：

单个cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie，而session则存储与服务端，浏览器对其没有限制。

5、会话机制不同

session会话机制：session会话机制是一种服务器端机制，它使用类似于哈希表（可能还有哈希表）的结构来保存信息。

cookies会话机制：cookie是服务器存储在本地计算机上的小块文本，并随每个请求发送到同一服务器。 Web服务器使用HTTP标头将cookie发送到客户端。在客户端终端，浏览器解析cookie并将其保存为本地文件，该文件自动将来自同一服务器的任何请求绑定到这些cookie。

### 网络层

#### DHCP协议

1. 发现阶段

   在DHCP服务配置完成后，DHCP Client启动时，由于没有IP地址，会自动发送以discover的广播报文，源地址为0.0.0.0目的地址为255.255.255.255。网络上的所有支持TCP/IP的主机都会收到该DHCP Discovery报文，但是只有DHCP Server会响应该报文。

2. DHCP Server offer响应阶段

   DHCP Server收到discover报文后，通过解析报文，查询dhcpd.conf配置文件，如果在地址池中能找到合适的IP地址，DHCP Server会给DHCP Client发送offer报文，告诉DHCP Client，该DHCP Server拥有资源，可以提供DHCP服务。

3. DHCP Client请求使用阶段

   当DHCP Client收到offer报文时，知道在本网段中有可用的DHCP Server可以提供DHCP服务，因此，它会发送一个request请求报文，向该DHCP Server请求IP地址、掩码、网关、DNS等信息，以便登陆网络。

4. DHCP Server确认使用阶段（获得IP地址）

   当DHCP Server收到DHCP Client发送的DHCP Request后，确认要为该DHCP Client提供的IP地址后，便向该DHCP Client响应一个包含该IP地址以及其他Option的报文，来告诉DHCP Client可以使用该IP地址了。然后DHCP Client即可以将该IP地址与网卡绑定。另外其他DHCP Server都将收回自己之前为DHCP Client提供的IP地址。

5. DHCP Client重新登录网络阶段

   当DHCP Client重新登录后，发送一个以前的DHCP Server分配的IP地址信息的DHCP Request报文，当DHCP Server收到该请求后，会尝试让DHCP客户端继续使用该IP地址。并回答一个ACK报文。

   如果该IP地址无法再次分配给该DHCP Client后，DHCP回复一个NAK报文，当DHCP Client收到该NAK报文后，会重新发送DHCP Discovery报文来重新获取IP地址。

6. DHCP Client续约阶段

   DHCP获取到的IP地址都有一个租约，租约过期后，DHCP Server将回收该IP地址，所以如果DHCP Client如果想继续使用该IP地址，则必须更新器租约。更新的方式就是，当当前租约期限过了一半后，DHCP Client都会发送DHCP Renew报文来续约租期。

#### 地址解析协议ARP

1. 每个主机都会在自己的 ARP 缓冲区中建立一个 ARP 列表，以表示 IP 地址和 MAC 地址之间的对应关系。
2. 主机（网络接口）**新加入网络时**（也可能只是mac地址发生变化，接口重启等）， 会发送免费ARP报文把**自己IP地址与Mac地址的映射关系广播给其他主机。**
3. 网络上的主机接收到免费ARP报文时，会更新自己的ARP缓冲区。将新的映射关系更新到自己的ARP表中。
4. 某个主机需要发送报文时，首先检查 ARP 列表中是否有对应 IP 地址的目的主机的 MAC 地址，如果有，则直接发送数据，如果没有，就向本网段的所有主机发送 ARP 数据包，该数据包包括的内容有：源主机 IP 地址，源主机 MAC 地址，目的主机的 IP 地址等。
5. 当本网络的所有主机收到该 ARP 数据包时：

​       A 首先检查数据包中的 IP 地址是否是自己的 IP 地址，如果不是，则忽略该数据包。

​       B 如果是，则首先从数据包中取出源主机的 IP 和 MAC 地址写入到 ARP 列表中，如果已经存在，则覆盖。

​       C 然后将自己的 MAC 地址写入 ARP 响应包中，告诉源主机自己是它想要找的 MAC 地址。

​     6.源主机收到 ARP 响应包后。将目的主机的 IP 和 MAC 地址写入 ARP 列表，并利用此信息发送数据。如果源主机一直没有收到 ARP 响应数据包，表示 ARP 查询失败。

#### IP掩码作用

子网掩码是一个32位地址，是与IP地址结合使用的一种技术。它的主要作用有两个，一是用于屏蔽IP地址的一部分以区别网络标识和主机标识，并说明该IP地址是在局域网上，还是在远程网上。二是用于将一个大的IP网络划分为若干小的子网络。

#### 交换机和路由器的区别

1. 路由器可以给你的局域网自动分配IP，虚拟拨号，就像一个交通警察，指挥着你的电脑该往哪走，你自己不用操心那么多了。交换机只是用来分配网络数据的。
2. 路由器在网络层，路由器根据IP地址寻址，路由器可以处理TCP/IP协议，交换机不可以。
3. 交换机在中继层，交换机根据MAC地址寻址。路由器可以把一个IP分配给很多个主机使用，这些主机对外只表现出一个IP。交换机可以把很多主机连起来，这些主机对外各有各的IP。
4. 路由器提供防火墙的服务，交换机不能提供该功能。集线器、交换机都是做端口扩展的，就是扩大局域网(通常都是以太网)的接入点，也就是能让局域网可以连进来更多的电脑。路由器是用来做网间连接，也就是用来连接不同的网络。

交换机是利用**物理地址或者说MAC地址**来确定转发数据的目的地址。而路由器则是利用不同网络的ID号(即IP地址)来确定数据转发的地址。IP地址是在软件中实现的，描述的是设备所在的网络，有时这些第三层的地址也称为协议地址或者网络地址。MAC地址通常是硬件自带的，由网卡生产商来分配的，而且已经固化到了网卡中去，一般来说是不可更改的。而IP地址则通常由网络管理员或系统自动分配。

**路由器和交换机的区别一**：交换机是一根网线上网，但是大家上网是分别拨号，各自使用自己的宽带，大家上网没有影响。而路由器比交换机多了一个虚拟拨号功能，通过同一台路由器上网的电脑是共用一个宽带账号，大家上网要相互影响。 

**路由器和交换机的区别二**：交换机工作在中继层，交换机根据MAC地址寻址。路由器工作在网络层，根据IP地址寻址，路由器可以处理TCP/IP协议，而交换机不可以。

**路由器和交换机的区别三**：交换机可以使连接它的多台电脑组成局域网，如果还有代理服务器的话还可以实现同时上网功能而且局域网所有电脑是共享它的带宽速率的，但是交换机没有路由器的自动识别数据包发送和到达地址的功能。路由器可以自动识别数据包发送和到达的地址，路由器相当于马路上的警察，负责交通疏导和指路的。

**路由器和交换机的区别四**：举几个例子,路由器是小邮局，就一个地址(IP)，负责一个地方的收发(个人电脑，某个服务器，所以你家上网要这个东西)，交换机是省里的大邮政中心，负责由一个地址给各个小地方的联系。简单的说路由器专管入网，交换机只管配送，路由路由就是给你找路让你上网的，交换机只负责开门，交换机上面要没有路由你是上不了网的。

**路由器和交换机的区别五**：路由器提供了防火墙的服务。路由器仅仅转发特定地址的数据包，不传送不支持路由协议的数据包传送和未知目标网络数据包的传送，从而可以防止广播风暴

#### 广播风暴及解决方法

★网络设备原因：交换机是点对点转发，一般情况下不会产生广播风暴。但在我们购买网络设置时，购买的交换机，通常被奸商用智能型的Hub来代替。这样，在网络繁忙的时候，产生广播风暴了的可能性就会大大增加。

★网卡损坏：损坏的网卡，不停向交换机发送大量的数据包，产生了大量无用的数据包，产生了广播风暴。由于网卡物理损坏引起的广播风暴，故障比较难排除，因为损坏的网卡一般还能上网，一般可借用Sniffer局域网管理软件，查看网络数据流量，来判断故障点的位置。

★网络环路：如果有一条双绞线的两端插在同一个交换机的不同端口上，会导致了网络性能急骤下降，打开网页非常困难，这样就会导致广播风暴（这只是网络回路的一种，在下面的知识链接部分我会给大家介绍其他几种网络回路）。网络环路的产生，一般是由于一条物理网络线路的两端，同时接在了一台网络设备中。

★网络病毒：一些比较流行的网络病毒如Funlove、震荡波、RPC等病毒，一旦有机器中毒后，会立即通过网络进行传播。网络病毒的传播，就会损耗大量的网络带宽，引起网络堵塞，引起广播风暴。

★软件的使用：一些上网者，经常利用网络执法官、网络剪刀手等软件，对网吧的内部网络进行攻击，由于这些软件的使用，网络也可能会引起广播风暴。

★网络视频引发广播风暴：部分视频网络传输设备为了便于网络视频点播，常常采用udp的方式，以广播数据包的形式对外进行发送，如果在专用网络中也使用这种方式，很容易引发广播风暴，导致网络阻塞，因此必须通过相关设置来杜绝这类故障。
对策：将视频网络传输设备所连接的交换机端口进行一些设置，对设备本身的网络传输模式以及传送协议类型进行更改，消除网络广播风暴。

解决方法：

  一、在局域网中安装wsus补丁服务器，保证局域网所有计算机都能及时打上最新的补丁。
  二、最好在局域网内安装网络版的防毒服务器，如无条件，起码也得保证单机版的防毒软件的病毒库是经常更新的。
  三、检查每一台计算机的网卡、网线和交换机的每一个端口，检查是否有故障。
  四、当广播风暴发生时，观察交换机的指示灯不失为很好的方法，可直接观察网络连通性及网络流量。

避免广播风暴：

采用恰当划分vlan、缩小广播域、隔离广播风暴，还可在千兆以太网口上启用广播风暴控制，最大限度地避免网络再次陷入瘫痪。当端口接受到大量的广播、单播或组播的包时，就会发生广播风暴。转发这些包会导致网络速度变慢或超时，在交换机上借助对端口的广播风暴控制可以有效避免硬件损坏或链路故障导致的广播风暴的网络瘫痪。
从实际经验来看，90%以上的网络广播风暴是病毒所致，因此，在局域网中配备防病毒系统，购置ids入侵检测系统、网络流量检测工具等，以加强网络 病毒的防治，加强对网络线路运行状态的监控，及时发现和处理网络上的异常流量和病毒攻击等问题，并制定计算机安全管理制度，确保网络线路的正常运行。

## 数据库

### ACID四大特性

**A 原子性（Atomicity）** 

就是把事物分割成像原子一样，表示我们事物需要细微的去控制。比如我给你转钱，里面有我扣钱，你到账。总不能我扣了钱，你没到账这种情况吧。所以就是指转账这个事物， 里面的所有环节哪怕一个出错，都需要事物回滚，就是一切回到之前那样。

**C 一致性（Consistency）**

 一致性是指事务必须使数据库从一个一致性状态变换到另一个一致性状态，也就是说一个事务执行之前和执行之后都必须处于一致性状态。

还是转账来说，假设用户A和用户B两者的钱加起来一共是1000，那么不管A和B之间如何转账，转几次账，事务结束后两个用户的钱相加起来应该还得是1000，这就是事务的一致性。

**I 隔离性（Isolation）**

隔离性是当多个用户并发访问数据库时，比如操作同一张表时，数据库为每一个用户开启的事务，不能被其他事务的操作所干扰，多个并发事务之间要相互隔离。
即要达到这么一种效果：对于任意两个并发的事务T1和T2，在事务T1看来，T2要么在T1开始之前就已经结束，要么在T1结束之后才开始，这样每个事务都感觉不到有其他事务在并发地执行。

**D 持久性（Durability）**

持久性是指一个事务一旦被提交了，那么对数据库中的数据的改变就是永久性的，即便是在数据库系统遇到故障的情况下也不会丢失提交事务的操作。

### 并发一致性问题

- **丢失修改**：一个事务对数据进行了修改，在事务提交之前，另一个事务对同一个数据进行了修改，覆盖了之前的修改；
- **脏读**（Dirty Read）：一个事务读取了被另一个事务修改、但未提交（进行了回滚）的数据，造成两个事务得到的数据不一致；
- **不可重复读**（Nonrepeatable Read）：在同一个事务中，某查询操作在一个时间读取某一行数据和之后一个时间读取该行数据，发现数据已经发生修改（可能被更新或删除了）；
- **幻读**（Phantom Read）：当同一查询多次执行时，由于其它事务在这个数据范围内执行了**插入操作**，会导致每次返回不同的结果集PS:幻读和不可重复读的区别：针对的是一个数据整体/范围；并且需要是插入操作 

### 四种隔离级别

- **未提交读**（Read Uncommited）：在一个事务提交之前，它的执行结果对其它事务也是可见的。会导致脏读、不可重复读、幻读；
- **提交读**（Read Commited）：一个事务只能看见已经提交的事务所作的改变。可避免脏读问题；
- **可重复读**（Repeatable Read）：可以确保同一个事务在多次读取同样的数据时得到相同的结果。（MySQL的默认隔离级别）。可避免不可重复读；
- **可串行化**（Serializable）：强制事务串行执行，使之不可能相互冲突，从而解决幻读问题。可能导致大量的超时现象和锁竞争，实际很少使用。

### 乐观锁/悲观锁

- 悲观锁：认为数据随时会被修改，因此每次读取数据之前都会上锁，防止其它事务读取或修改数据；应用于**数据更新比较频繁**的场景；

- 乐观锁：操作数据时不会上锁，但是更新时会判断在此期间有没有别的事务更新这个数据，若被更新过，则失败重试；适用于

  读多写少的场景。乐观锁的实现方式有：

  - 加一个版本号或者时间戳字段，每次数据更新时同时更新这个字段；
  - 先读取想要更新的字段或者所有字段，更新的时候比较一下，只有字段没有变化才进行更新

### 什么是三级封锁协议？

- 一级封锁协议：事务在修改数据之前必须先对其加X锁，直到事务结束才释放。可以解决丢失修改问题（两个事务不能同时对一个数据加X锁，避免了修改被覆盖）；
- 二级封锁协议：在一级的基础上，事务在读取数据之前必须先加S锁，读完后释放。可以解决脏读问题（如果已经有事务在修改数据，就意味着已经加了X锁，此时想要读取数据的事务并不能加S锁，也就无法进行读取，避免了读取脏数据）；
- 三级封锁协议：在二级的基础上，事务在读取数据之前必须先加S锁，直到事务结束才能释放。可以解决不可重复读问题（避免了在事务结束前其它事务对数据加X锁进行修改，保证了事务期间数据不会被其它事务更新）

### 什么是两段锁协议？

事务必须严格分为两个阶段对数据进行**加锁和解锁**的操作，第一阶段加锁，第二阶段解锁。也就是说一个事务中一旦释放了锁，就不能再申请新锁了。

**可串行化调度**是指，通过并发控制，使得并发执行的事务结果与某个串行执行的事务结果相同。事务遵循两段锁协议是保证可串行化调度的充分条件。

### 索引(待完成)

#### 解释下聚簇索引和非聚簇索引

#### mysql用B+树做索引而不用B-树/红黑树

B-树、B+树、红黑树，是**平衡查找树**，那么查询效率上讲，平均都是O(logn)。使用什么哪种数据结构，肯定是出于提高数据库的查询效率的考虑。

**一、B+树做索引而不用B-树**
Mysql如何衡量查询效率呢？– **磁盘IO次数**。
一般来说索引非常大，尤其是关系性数据库这种数据量大的索引能达到亿级别，所以为了减少内存的占用，索引也会被存储在磁盘上。B-树/B+树 的特点就是每层节点数目非常多，层数很少，目的就是为了减少磁盘IO次数，但是B-树的每个节点都有data域（指针），这无疑增大了节点大小，说白了增加了磁盘IO次数（磁盘IO一次读出的数据量大小是固定的，单个数据变大，每次读出的就少，IO次数增多，一次IO多耗时），而B+树除了叶子节点其它节点并不存储数据，节点小，磁盘IO次数就少。

优点一： B+树只有叶节点存放数据，其余节点用来索引，而B-树是每个索引节点都会有Data域。

优点二： B+树所有的Data域在叶子节点，并且所有叶子节点之间都有一个链指针。 这样遍历叶子节点就能获得全部数据，这样就能进行区间访问啦。在数据库中基于范围的查询是非常频繁的，而B树不支持这样的遍历操作。

**二、B+树做索引而不用红黑树**
AVL 树（平衡二叉树）和红黑树（二叉查找树）基本都是存储在内存中才会使用的数据结构。在大规模数据存储的时候，红黑树往往出现由于树的深度过大而造成磁盘IO读写过于频繁，进而导致效率低下的情况。为什么会出现这样的情况，要获取磁盘上数据，必须先通过磁盘移动臂移动到数据所在的柱面，然后找到指定盘面，接着旋转盘面找到数据所在的磁道，最后对数据进行读写。磁盘IO代价主要花费在查找所需的柱面上，树的深度过大会造成磁盘IO频繁读写。根据磁盘查找存取的次数往往由树的高度所决定，所以，只要我们通过某种较好的树结构减少树的结构尽量减少树的高度，**B树可以有多个子女，从几十到上千，可以降低树的高度。**

数据库系统的设计者巧妙利用了磁盘预读原理，将一个节点的大小设为等于一个页，这样每个节点只需要一次I/O就可以完全载入。为了达到这个目的，在实际实现B-Tree还需要使用如下技巧：每次新建节点时，直接申请一个页的空间，这样就保证一个节点物理上也存储在一个页里，加之计算机存储分配都是按页对齐的，就实现了一个node只需一次I/O。

#### 建立索引的原则

1．选择唯一性索引

唯一性索引的值是唯一的，可以更快速的通过该索引来确定某条记录。例如，学生表中学号是具有唯一性的字段。为该字段建立唯一性索引可以很快的确定某个学生的信息。如果使用姓名的话，可能存在同名现象，从而降低查询速度。

2．为经常需要排序、分组和联合操作的字段建立索引

经常需要ORDER BY、GROUP BY、DISTINCT和UNION等操作的字段，排序操作会浪费很多时间。如果为其建立索引，可以有效地避免排序操作。

3．为常作为查询条件的字段建立索引

如果某个字段经常用来做查询条件，那么该字段的查询速度会影响整个表的查询速度。因此，为这样的字段建立索引，可以提高整个表的查询速度。

4．限制索引的数目

索引的数目不是越多越好。每个索引都需要占用磁盘空间，索引越多，需要的磁盘空间就越大。修改表时，对索引的重构和更新很麻烦。越多的索引，会使更新表变得很浪费时间。

5．尽量使用数据量少的索引

如果索引的值很长，那么查询的速度会受到影响。例如，对一个CHAR(100)类型的字段进行全文检索需要的时间肯定要比对CHAR(10)类型的字段需要的时间要多。

6．尽量使用前缀来索引

如果索引字段的值很长，最好使用值的前缀来索引。例如，TEXT和BLOG类型的字段，进行全文检索会很浪费时间。如果只检索字段的前面的若干个字符，这样可以提高检索速度。

7．删除不再使用或者很少使用的索引

表中的数据被大量更新，或者数据的使用方式被改变后，原有的一些索引可能不再需要。数据库管理员应当定期找出这些索引，将它们删除，从而减少索引对更新操作的影响。

8 . 最左前缀匹配原则，非常重要的原则。

mysql会一直向右匹配直到遇到范围查询(>、<、between、like)就停止匹配，比如a 1=”” and=”” b=”2” c=”“> 3 and d = 4 如果建立(a,b,c,d)顺序的索引，d是用不到索引的，如果建立(a,b,d,c)的索引则都可以用到，a,b,d的顺序可以任意调整。

9 .=和in可以乱序。

比如a = 1 and b = 2 and c = 3 建立(a,b,c)索引可以任意顺序，mysql的查询优化器会帮你优化成索引可以识别的形式

10 . 尽量选择区分度高的列作为索引。

区分度的公式是count(distinct col)/count(*)，表示字段不重复的比例，比例越大我们扫描的记录数越少，唯一键的区分度是1，而一些状态、性别字段可能在大数据面前区分度就 是0，那可能有人会问，这个比例有什么经验值吗？使用场景不同，这个值也很难确定，一般需要join的字段我们都要求是0.1以上，即平均1条扫描10条 记录

11 .索引列不能参与计算，保持列“干净”。

比如from_unixtime(create_time) = ’2014-05-29’就不能使用到索引，原因很简单，b+树中存的都是数据表中的字段值，但进行检索时，需要把所有元素都应用函数才能比较，显然成本 太大。所以语句应该写成create_time = unix_timestamp(’2014-05-29’);

12 .尽量的扩展索引，不要新建索引。 
比如表中已经有a的索引，现在要加(a,b)的索引，那么只需要修改原来的索引即可

13、当单个索引字段查询数据很多，区分度都不是很大时，则需要考虑建立联合索引来提高查询效率

注意：选择索引的最终目的是为了使查询的速度变快。上面给出的原则是最基本的准则，但不能拘泥于上面的准则。读者要在以后的学习和工作中进行不断的实践。根据应用的实际情况进行分析和判断，选择最合适的索引方式。

# 杂谈

### CyclicBarrier与CountDownLatch（待完成）

#  面经问题

## 常见面试点

- Java map+基础知识
- JVM 运行时数据区、GC收集、类加载过程
- HTTPS、TCP、网页输入URL
- 进程、线程、协程概念及通信方式
- Linux常用命令
- 海量数据TOP K问题

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

    