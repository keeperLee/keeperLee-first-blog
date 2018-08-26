---
layout: post
title:  "小程序Storage缓存"
categories: 小程序
tags: weChat  缓存
author: JerryLee
---

* content
{:toc}

## 1.wx.setStorageSync(同步的缓存)
生成缓存：wx.setStorageSync('key',"helloworld")  
修改缓存：wx.setStorageSync('key',"newworld")  
清除缓存：  
1.清除所有缓存：wx.clearStorageSync();  
2.清楚指定缓存：wx.removeStorageSync('key')

## 2.wx.setStorage(异步的缓存)
生成缓存：wx.setStorage('key',"helloworld")  
修改缓存：wx.setStorage('key',"newworld")  
清除缓存：  
1.清除所有缓存：wx.clearStorage();  
2.清楚指定缓存：wx.removeStorage('key')
