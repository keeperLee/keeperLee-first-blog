---
layout: post
title:  "来到github Pages的第一篇博客"
categories: 记事
tags: github
author: JerryLee
---

* content
{:toc}
以前一直没有接触过github，还有git，近段时间才开始研究这两者，不知不觉之间进入了一个全球最大的同性交流平台。
作为第一篇在github Pages上写的博客，在此娱乐一下，带来几个小测验：
## 智力小测验
> ##### 测验一：如何通过java来计算5的阶乘，50的阶乘呢？

计算5的阶乘有比较多的方法，这里使用递归的方式来处理：

```js
  public static long jiecheng(int n){
    if(n==1)
      return 1;
    return n*jiecheng(n-1);
  }

  public static void main(String[] args){
    System.out.println(jiecheng(5));
  }
```

但是当计算50的阶乘时就会出问题了，得到的值会是负值，这时需要改变策略：


```js
  public static long jiecheng(int n){
    if(n==1)
      return 1;
    return n*jiecheng(n-1);
  }

  public static void main(String[] args) {
		BigDecimal s = BigDecimal.valueOf(1);
		for(int i=1;i<=50;i++){
			s = s.multiply(BigDecimal.valueOf(i));
		}
		System.out.println(s);
	}
```
