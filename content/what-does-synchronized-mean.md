# 什么是synchronized？
[What does 'synchronized' mean?](https://stackoverflow.com/questions/1085709/what-does-synchronized-mean)

___



> 1

synchronized这个关键字是关于不同的线程读写同一个变量、对象和资源

synchronized的方法可以实现一个简单的策略来防止线程干扰和内存的一致性错误：如果一个对象对多个线程可见，则所有对该对象变量的读写操作都是通过同步方法完成的。

在非常非常小的情况下：如果有两个线程正在读取和写入相同的“资源”，比如一个名为foo的变量，则需要确保这些线程以原子方式访问该变量。 如果没有synchronized关键字，你的线程1可能看不到线程2对foo的改变，或者更糟的是，它可能中途改变。 这不会是你所期望的。

> 2

 `synchronized` 防止在多线程中并发地访问一段代码或者对象. 默认的,  `Hashtable` 就是 `synchronized`, 所以只有一个线程可以访问table同一时间。

如果用了 `non-synchronized` 比如 `HashMap`,你必须建立线程安全特性来防止内存一致性错误