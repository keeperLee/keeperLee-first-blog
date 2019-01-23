---
layout: post
title:  "浮点运算丢失精度问题"
categories: JAVA
tags: JAVA
author: KeeperLee
---
* content
{:toc}
## BigDecimal的前生今世




>##### 在商业运算中总是会涉及到浮点型数值的运算，如果不加以处理，则会因为精度的丢失而造成一些意想不到的后果，下面给出了具体的例子。





``` java

public class BigDecimalTest {

    @Test
    public void test1(){
        System.out.println(0.05+0.01);
        System.out.println(1.0-0.42);
        System.out.println(4.015*100);
        System.out.println(123.3/100);
    }

    @Test
    public void test2(){
        BigDecimal b1 = new BigDecimal(0.05);
        BigDecimal b2 = new BigDecimal(0.01);
        System.out.println(b1.add(b2));

    }

    @Test
    public void test3(){
        BigDecimal b1 = new BigDecimal("0.05");
        BigDecimal b2 = new BigDecimal("0.01");
        System.out.println(b1.add(b2));

    }
}


```
- test1的结果：精度丢失严重：
![嘻嘻嘻](/images/Util/1.png)  
- test2虽然使用的是BigDecimal的构造器，但是始终有精度的丢失。
![嘻嘻嘻](/images/Util/2.png)  
- test3使用了BigDecimal的String参数的构造器，最后得到了我们想要的结果。
![嘻嘻嘻](/images/Util/3.png)  


>###### **综上所诉：在商业运算中涉及到浮点运算的计算都要使用BigDecimal的String参数的构造器。**
