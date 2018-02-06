# Java中是“值传递”还是“引用传递”？
[Is Java “pass-by-reference” or “pass-by-value”?](https://stackoverflow.com/questions/40480/is-java-pass-by-reference-or-pass-by-value)

___



> 1

Java总是值传递，但是不幸的是，他们绝对把一个对象的位置叫做“引用”,当我们传递一个对象的值，我们实际上是在传递一个引用，这个很容易困惑，它是这样处理的

```java
public static void main( String[] args ) {
    Dog aDog = new Dog("Max");
    // 我们传递了对象给foo
    foo(aDog);
    // aDog 变量仍然指向 "Max" dog 当 foo(...) returns
    aDog.getName().equals("Max"); // true, java passes by value
    aDog.getName().equals("Fifi"); // false 
}

public static void foo(Dog d) {
    d.getName().equals("Max"); // true
    // 在 foo() 内部让d指向了一个新的 Dog instance "Fifi"
    d = new Dog("Fifi");
    d.getName().equals("Fifi"); // true
}
```

在这个例子中`aDog.getName()` 会返回 `"Max"`.  `aDog` 这个值不在 `main` 而在 `foo` 并没有变成 `Dog` `"Fifi"` 因为是作为值来传递. 如果它时引用传递, 那么在调用`foo`之后 `aDog.getName()` 在 `main` 将会返回 `"Fifi"` 

同样的

```java
public static void main( String[] args ) {
    Dog aDog = new Dog("Max");
    foo(aDog);
    // when foo(...) returns, the name of the dog has been changed to "Fifi"
    aDog.getName().equals("Fifi"); // true
}

public static void foo(Dog d) {
    d.getName().equals("Max"); // true
    // this changes the name of d to be "Fifi"
    d.setName("Fifi");
}
```

在上面的例子中， `foo(aDog)` 在调用之后dog名变成了 `Fifi` 因为object's name  `foo(...)`在里面被设置了。