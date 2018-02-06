# HashMap和Hashtable区别？
[Differences between HashMap and Hashtable?](https://stackoverflow.com/questions/40471/differences-between-hashmap-and-hashtable)

___



> 1

Java中的HashMap和Hashtable有一些不同:

1. [`Hashtable`](http://java.sun.com/javase/7/docs/api/java/util/Hashtable.html) is [同步的](https://stackoverflow.com/questions/1085709/what-does-synchronized-mean), 然而 [`HashMap`](http://java.sun.com/javase/7/docs/api/java/util/HashMap.html) 不是. 这就使得 [`HashMap`](http://java.sun.com/javase/7/docs/api/java/util/HashMap.html) 在非多线程应用时更高效, 因为一般来说，非同步对象比同步对象更加高效.
2. [`Hashtable`](http://java.sun.com/javase/7/docs/api/java/util/Hashtable.html) 不允许 `null` keys或者values. [`HashMap`](http://java.sun.com/javase/7/docs/api/java/util/HashMap.html) 允许一个 `null` key 任意数量的 `null` values.
3.  HashMap的一个子类是 [`LinkedHashMap`](http://java.sun.com/javase/7/docs/api/java/util/LinkedHashMap.html), 所以如果你想要按顺序遍历(默认是插入的顺序), 你用 [`LinkedHashMap`](http://java.sun.com/javase/7/docs/api/java/util/LinkedHashMap.html)可以很简单， 用 [`Hashtable`](http://java.sun.com/javase/7/docs/api/java/util/Hashtable.html)就不容易了

如果同步不是问题，那么建议使用 [`HashMap`](http://java.sun.com/javase/7/docs/api/java/util/HashMap.html). 如果要考虑同步问题，那你应该看看 [`ConcurrentHashMap`](http://docs.oracle.com/javase/7/docs/api/java/util/concurrent/ConcurrentHashMap.html).