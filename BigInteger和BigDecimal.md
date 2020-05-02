# BigInteger

1.如果我们使用的整数范围超过了long型，那么就用软件来模拟一个大整数，java.math.BigInteger就是用来表示任意大小的整数。如

```
BigInteger bi = new BigInteger("1234567890");
System.out.println(bi.pow(5)); // 2867971860299718107233761438093672048294900000

//对BigInteger做运算的时候，只能使用实例方法，例如，加法运算：
BigInteger i2 = new BigInteger("12345678901234567890");
BigInteger sum = bi.add(i2); // 12345678902469135780

```

2.将BigInteger转换成long型：

```
BigInteger i = new BigInteger("123456789000");
System.out.println(i.longValue()); // 123456789000
```

# BigDecimal

1.和`BigInteger`类似，`BigDecimal`可以表示一个任意大小且精度完全准确的浮点数。 

```
BigDecimal bd = new BigDecimal("123.4567");
```

2.BigDecimal`用`scale()表示小数位数 ，如

```
System.out.println(bd.scale()); // 3,三位小数
```

3.stripTrailingZeros()方法，可以将一个BigDecimal格式化为一个相等的，但去掉了末尾0的BigDecimal

```
BigDecimal d1 = new BigDecimal("123.4500");
BigDecimal d2 = d1.stripTrailingZeros();
System.out.println(d1.scale()); // 4
System.out.println(d2.scale()); // 2,因为去掉了00
```

4.设置scale

BigDecimal d1 = new BigDecimal("123.456789");
BigDecimal d2 = d1.setScale(4, RoundingMode.HALF_UP); // 四舍五入，123.4568
BigDecimal d3 = d1.setScale(4, RoundingMode.DOWN); // 直接截断，123.4567

5.比较BigDecimal

在比较两个`BigDecimal`的值是否相等时，要特别注意，使用`equals()`方法不但要求两个`BigDecimal`的值相等，还要求它们的`scale()`相等，可使用 `compareTo()`方法来比较 ：

```
BigDecimal d1 = new BigDecimal("123.456");
BigDecimal d2 = new BigDecimal("123.45600");
System.out.println(d1.equals(d2)); // false,因为scale不同
System.out.println(d1.equals(d2.stripTrailingZeros())); // true,因为d2去除尾部0后scale变为2
System.out.println(d1.compareTo(d2)); // 0
```

