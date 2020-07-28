### jdk8的特征



##### Lambda表达式 + 函数式接口  ---（函数式编程）

> (parameters参数) ->(expression表达式或方法体)
>
> > lambda表达式，本质上是一段匿名内部类，也可以是一段可以传递的代码
>
> > 其中 ->：可理解为“被用于”的意思
> >
> > ~~~ java
> >  //匿名内部类
> >   Comparator<Integer> cpt = new Comparator<Integer>() {
> >       @Override
> >       public int compare(Integer o1, Integer o2) {
> >           return Integer.compare(o1,o2);
> >       }
> >   };
> >   TreeSet<Integer> set = new TreeSet<>(cpt);
> >   //使用lambda表达式
> >   Comparator<Integer> cpt2 = (x,y) -> Integer.compare(x,y);
> >   TreeSet<Integer> set2 = new TreeSet<>(cpt2);
> > ~~~
> >
> > 

##### 

##### Stream API



>HashMap ：进行了优化 底层数据结构：**数组+链表+红黑树**
>
>ConcurrentHashMap（锁定段机制）: jdk1.8采用CAS算法(无所算法，不再使用锁分段)，

