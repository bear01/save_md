1. **java 八大基本类型**

   整型: byte(1) 	 short(2)	 int(4) 	long(8)

   浮点型：float(4) 	double(8)

   逻辑：boolean(1)

   字符型：char(2)

2. **String类能被继承吗，为什么。**

   不能被继承，因为String类有final修饰符。

   final和static的区别：static作用于成员变量，用来表示只保存一份副本。而final的作用是用来保证变量不可变，如果是引用的对象，其对象不变，对象内容可以变。

   ```java
   public final class String implements java.io.Serializable, Comparable<String>, CharSequence {
       // 省略...
   }
   ```

3. **String，Stringbuffer，StringBuilder的区别**

   

   一旦创建就不可变，包括对象中的字符序列也不可变，直到这个对象销毁。

   ~~~java
   String a = "123";
   a = "456";   // 并不是对原来堆中实例对象进行重新赋值，而是生成一个新的实例对象，之前的实例对象仍然存在，如果没有被再次引用，则会被垃圾回收。
   System.out.println(a)  // 打印出来的a为456
   ~~~

   StringBuffer对象则代表一个字符序列可变的字符串,可以改变内容，可以调用它的toString()方法将其转换为一个String对象。

   StringBuilder类也代表可变字符串对象。不同的是：StringBuffer是线程安全的（添加了synchronized关键字，锁**），而StringBuilder则没有实现线程安全功能，所以性能略高**

4.  **ArrayList 和 LinkedList 有什么区别。**

   ArrayList:**可以看作是能够自动增长容量的数组**,持续空间，查询速度快。

   LinkedList:**双链表,**在添加和删除元素时具有比ArrayList更好的性能，不需要持续空间

5. **继承和聚合的区别**

   **继承**：![image-20200302173850340](C:\Users\bear\AppData\Roaming\Typora\typora-user-images\image-20200302173850340.png)

   **聚合**：![image-20200302173909863](C:\Users\bear\AppData\Roaming\Typora\typora-user-images\image-20200302173909863.png)

   聚合体现的是整体与部分、拥有的关系，此时整体与部分之间是可分离的，他们可以具有各自的生命周期；比如计算机与CPU、公司与员工的关系等；

6. **类可以继承多个类么，接口可以继承多个接口么**

   **java类是单继承的**  **java接口可以多继承**（接口全都是抽象方法继承谁都无所谓，所以接口可以继承多个接口。）一个类实现了某个接口，就必须实现接口的所有方法。

7. **类的实例化顺序**

   1->父类静态成员和静态代码块

   2->子类静态成员和静态代码块

   3->父类非静态成员和非静态代码块

   4->父类构造方法

   5->子类非静态成员和非静态代码块

   6->子类构造方法

8. **Map 类**

   HashMap、HashTable、LinkedHashMap和TreeMap

   **HashMap:**线程不安全，同步，效率高。允许key或value为null。底层是哈希表数据结构，哈希表的基本结构就是“**数组+链表**”

   **Hashtable:**线程安全，不同步，效率低。不允许key或value为null。底层是哈希表数据结构

   **LinkedHashMap:**linkedHashMap最大的特点在于**有序**，但是它的有序主要体现在**先进先出FIFIO**上。主要依靠双向链表和hash表来实现的。

   **Treemap:**对Key进行**排序**,默认采用key由小到大的顺序输出键值对，底层是二叉树数据结构
   
9. **[反射原理](https://blog.csdn.net/a745233700/article/details/82893076)**

   Java反射机制是在运行状态中，对于任何一个类，都知道这个类的所有属性和方法；对于任何一个对象，都能调用它的任意方法和属性。
   
   功能: 
   
   ​		得到一个对象所属的类；反编译（.class-->.java）
   
   ​		获取一个类所有成员变量和方法；
   
   ​		在运行时创建对象；
   
   ​		在运行时调用对象的方法；
   
   ​		最重要的用途是开发各种通用框架，保证框架的通用性。
   
   优点：使用反射，我们就可以在运行时获得类的各种内容，进行反编译，对于Java这种先编译再运行的语言，能够让我们很方便的创建灵活的代码，这些代码可以在运行时装配，无需在组件之间进行源代码的链接，更加容易实现面向对象。
   
   缺点：（1）反射会消耗一定的系统资源，因此，如果不需要动态地创建一个对象，那么就不需要用反射；
   
   ​			（2）反射调用方法时可以忽略权限检查，因此可能会破坏封装性而导致安全问题。

