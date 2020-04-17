> 网上很多人写threadLocal，看了很多版本越看懵逼，到后来不会知道它到底是什么？今天在这里说一下自己对threadLocal的理解，若有不对之处，望各位大佬轻喷！！

---
- ThreadLocal定义了一个内部类ThreadLocalMap，此类的作用类似于我们比较熟悉的HashMap,用于存储key,value的键值对。
- 线程类Thread中定义了一个ThreadLocalMap类型的成员变量 threadLocals，就是用它来存储线程变量。
- 现在有个变量 ,两个线程ThreadA、ThreadB希望存储不一样的值，这个时候就可以用threadLocal声明这个变量。
- 声明一个ThreadLocal变量 th1; ThreadA线程threadLocals存储key就是th1,value就是自己想存储的值，这个我们定义为varA;ThreadB线程threadLocals存储key就是th1,value定义为varB;

```
    ThreadA---->threadLocals.put("th1","varA");
    ThreadB---->threadLocals.put("th1","varB");
```
- 若有多个变量不需要共享，定义多个ThreadLocal变量;ThreadLocal th1,ThreadLocal th2

```
    ThreadA---->threadLocals.put("th1","varA");
    ThreadA---->threadLocals.put("th2","varC");
    ThreadB---->threadLocals.put("th1","varB");
    ThreadB---->threadLocals.put("th2","varD");
```



