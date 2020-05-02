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

![image](https://github.com/liuyu105/Java_basic/blob/master/images/1580910773076.png)

## 3.String的构造方法

​	String(String original):把字符串数据封装成字符串对象
​	String(char[] value):把字符数组的数据封装成字符串对象
​	String(char[] value, int index, int count):把字符数组中的一部分数据封装成字符串对象

## 4.String类的判断功能

  boolean equals(Object obj):比较字符串的内容是否相同
  boolean equalsIgnoreCase(String str):比较字符串的内容是否相同,忽略大小写
  boolean startsWith(String str):判断字符串对象是否以指定的str开头
  boolean endsWith(String str):判断字符串对象是否以指定的str结尾

`String`还提供了`isEmpty()`和`isBlank()`来判断字符串是否为空和空白字符串：

```
"".isEmpty(); // true，因为字符串长度为0
"  ".isEmpty(); // false，因为字符串长度不为0
"  \n".isBlank(); // true，因为只包含空白字符
" Hello ".isBlank(); // false，因为包含非空白字符
```

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

## 7.去除首尾空白字符

（1） 空白字符包括空格，`\t`，`\r`，`\n` 

​        String s2 = "  hello  ";
​		// 去除字符串两端空格**String trim()**
​		System.out.println(s2.trim());

（2） 另一个`strip()`方法也可以移除字符串首尾空白字符。它和`trim()`不同的是，类似中文的空格字符`\u3000`也会被移除 

如："\u3000Hello\u3000".strip(); // "Hello"

## 8.分割字符串

// 按照指定符号分割字符串String[] split(String str)
​	String s3 = "aa,bb,cc";
​	String[] arr = s3.split(",");
​	for (int i = 0; i < arr.length; i++) {
​		System.out.println(arr[i]);
​	}

## 9.拼接字符串

拼接字符串使用静态方法`join()`，它用指定的字符串连接字符串数组：

```
String[] arr = {"A", "B", "C"};
String s = String.join("***", arr); // "A***B***C"
```

## 10.格式化字符串

字符串提供了`formatted()`方法和`format()`静态方法，可以传入其他参数，替换占位符，然后生成新的字符串：

public class Main {
    public static void main(String[] args) {
        String s = "Hi %s, your score is %d!";
        System.out.println(s.formatted("Alice", 80));
        System.out.println(String.format("Hi %s, your score is %.2f!", "Bob", 59.5));
    }
}

<<<<<<< HEAD
=======
- String-->StringBuilder
  StringBuilder strb=new StringBuilder(str); //StringBuilder(String str):通过构造方法就可以完成转换
>>>>>>> df567eea1408ab5c98e5c3153f7fa4720118a5fc
