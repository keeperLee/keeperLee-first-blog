---
layout: post
title:  "practise"
categories: JAVA
tags: JAVA
author: 李健
---
* content
{:toc}
## practise makes perfect!




> 1.使用数组方式，计算Fibonacci数列的前20个元素的和。

``` java

public class Fibonacci{
    public static void main(String args[]){
    int[] array = new int[20];
        int sum = 0;
        for(int i=0;i<20;i++){
            if(i==0||i==1){
                array[i] = 1;
            }
            if(i>=2){
                array[i] = array[i-1] + array[i-2];
            }
            sum = sum +array[i];
        }
        System.out.print("前20个元素的和为"+sum);
    }
}
```


> 2.使用递归，计算1+2+...+n的和。

``` java

public class Sum {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int num = sc.nextInt();
        int result = recursionSum(num);
        System.out.println(result);
    }
    
    public static int recursionSum(int num) {
        if(num == 1) {
            return 1;
        }else {
            return recursionSum(num-1) + num;
        }
    }
}

```

> 3.找出一百个随机数的最大值、最小值和大于50的值。

``` java
public class MaxMin {
    public static void main(String[] args) {
        double[] arr = new double[100];
        int s = 0; // 定义 统计大于50的整数个数 变量
        double max = 0, min = 100; // 定义 最大值 最小值 变量
        for (int i = 0; i < 100; i++) {
            double d = 100 * Math.random();// 获取随机数
            arr[i] = (int) d;
            if (arr[i] < min) {
                min = arr[i];
            }
            if (arr[i] > max) {
                max = arr[i];
            }
            if (arr[i] > 50) {
                s++;
            }
        }
        System.out.println(max);
        System.out.println(min);
        System.out.println(s);
    }
}

```
