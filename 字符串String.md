# 字符串String

## 1. 创建字符串对象两种方式的区别

通过构造方法创建的字符串对象和直接赋值方式创建的字符串对象有什么区别呢?
* 		通过构造方法创建字符串对象是在堆内存。
* 		直接赋值方式创建对象是在方法区的常量池。

## 2.==的区别

* 		基本数据类型：比较的是基本数据类型的值是否相同
* 		引用数据类型：比较的是引用数据类型的地址值是否相同

```
public class StringDemo2 {
	public static void main(String[] args) {
		String s1 = new String("hello");
		String s2 = "hello";
		

		System.out.println("s1:"+s1);
		System.out.println("s2:"+s2);
		
		System.out.println("s1==s2:"+(s1==s2)); //false
		
		String s3 = "hello";
		System.out.println("s1==s3:"+(s1==s3)); //false
		System.out.println("s2==s3:"+(s2==s3)); //true
	
	}

}
```

![1580910773076](C:\Users\梦晨涌京\AppData\Roaming\Typora\typora-user-images\1580910773076.png)

## 3.String的构造方法

​	String(String original):把字符串数据封装成字符串对象
​	String(char[] value):把字符数组的数据封装成字符串对象
​	String(char[] value, int index, int count):把字符数组中的一部分数据封装成字符串对象

## 4.String类的判断功能

  boolean equals(Object obj):比较字符串的内容是否相同
  boolean equalsIgnoreCase(String str):比较字符串的内容是否相同,忽略大小写
  boolean startsWith(String str):判断字符串对象是否以指定的str开头
  boolean endsWith(String str):判断字符串对象是否以指定的str结尾

## 5.String类的获取功能

  int length():获取字符串的长度，其实也就是字符个数

 char charAt(int index):获取指定索引处的字符

  int indexOf(String str):获取str在字符串对象中第一次出现的索引

 String substring(int start):从start开始截取字符串

 String substring(int start,int end):从start开始，到end结束截取字符串。包括start，不包括end

## 6.String类的转换功能

char[] toCharArray():把字符串转换为字符数组
String toLowerCase():把字符串转换为小写字符串
String toUpperCase():把字符串转换为大写字符串

## 7.其他功能

​       String s2 = "  hello  ";
​		// 去除字符串两端空格String trim()
​		System.out.println(s2.trim());

​	// 按照指定符号分割字符串String[] split(String str)
​	String s3 = "aa,bb,cc";
​	String[] arr = s3.split(",");
​	for (int i = 0; i < arr.length; i++) {
​		System.out.println(arr[i]);
​	}

## 8.StringBuilder

（1）StringBuilder：是一个可变的字符串。字符串缓冲区类。

String和StringBuilder的区别：

​       String的内容是固定的

​       StringBuilder的内容是可变的

（2）+=拼接字符串耗费内存原因:

每次拼接都会产生新的字符串对象，而利用StringBuilder来拼接字符串自始至终用的都是同一个StringBuilder容器

![1580911779954](C:\Users\梦晨涌京\AppData\Roaming\Typora\typora-user-images\1580911779954.png)

（3）常用方法

A:构造方法:

​    StringBuilder()

B:成员方法:

   public int capacity():返回当前容量 (理论值)

​    public int length():返回长度(已经存储的字符个数)

​    public StringBuilder append(任意类型):添加数据，并返回自身对象

​    public StringBuilder reverse():反转功能

（4）String与StringBuilder相互转换

- StringBuilder-->String
  String str=stringBuilder.toString(); //public String toString():通过toString()就可以实现转换

- String-->StringBuilder
  StringBuilder strb=new StringBuilder(str); //StringBuilder(String str):通过构造方法就可以完成转换