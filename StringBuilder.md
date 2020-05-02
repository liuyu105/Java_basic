# 1.StringBuilder

为了能高效拼接字符串，Java标准库提供了StringBuilder，它是一个可变对象，可以预分配缓冲区，这样，往StringBuilder中新增字符时，不会创建新的临时对象。

String和StringBuilder的区别：

​       String的内容是固定的

​       StringBuilder的内容是可变的

# 2.+=拼接字符串耗费内存原因:

每次拼接都会产生新的字符串对象，而利用StringBuilder来拼接字符串自始至终用的都是同一个StringBuilder容器

![1580911779954](C:\Users\梦晨涌京\AppData\Roaming\Typora\typora-user-images\1580911779954.png)

# 3.常用方法

A:构造方法:

​    StringBuilder()

B:成员方法:

   public int capacity():返回当前容量 (理论值)

​    public int length():返回长度(已经存储的字符个数)

​    public StringBuilder append(任意类型):添加数据，并返回自身对象

​    public StringBuilder reverse():反转功能

# 4.String与StringBuilder相互转换

- StringBuilder-->String
  String str=stringBuilder.toString(); //public String toString():通过toString()就可以实现转换

- String-->StringBuilder
  StringBuilder strb=new StringBuilder(str); //StringBuilder(String str):通过构造方法就可以完成转换

# 5.Stringjoiner

（1）Stringjoiner可以用来高效拼接字符串，

```java
String []names={"Bob","Alice","Grace"};
StringJoiner sj=new StringJoiner(", ");
//指定开头结尾
StringJoiner sj1=new StringJoiner(", ","Hello ","!");
for(String name:names){  
  sj.add(name);
}
System.out.println(sj.toString());//Bob,Alice,Grace
System.out.println(sj1.toString());//Hello Bob,Alice,Grace！

```

（2）String.join()

`String`还提供了一个静态方法`join()`，这个方法在内部使用了`StringJoiner`来拼接字符串，在不需要指定“开头”和“结尾”的时候，用`String.join()`更方便：

```
String[] names = {"Bob", "Alice", "Grace"};
String s = String.join(",", names);//Bob,Alice,Grace
```

