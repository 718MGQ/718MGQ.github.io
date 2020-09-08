---
title: 二分法查找
date: 2020-06-07 14:58:21
tags:
- leetcode
- algorithm
- 面试题
categories: 
- 算法
---

### 摘要
--------------------
> 二分法查找：又称折半查找。适用于有序数据集合的目标值查找。
    
    二分法思想：假设有一个按升序排好序的数列data，查找目标值target，过程如下：
    1.将数列进行折半，判断data[mid]是否等于target, 相等则返回index, 否则，判断中间值和target大小；
    2.若 target > data[mid]，将data右一半执行第一步，否则，将data左一半执行第一步；
    3.返回index

<!--more-->
### code
---------------------
废话不多说，上代码
```java
public class BinarySearch {

    public int getIndex(int[] data, int target) {

        int left = 0;
        int right = data.length - 1;

        while (left <= right) {
            //定义一个中间值索引
            int mid = left + (right - left) / 2;
            if(data[mid] == target) {
                //查到目标值，直接返回索引值
                return mid;
            } else if(data[mid] < target) {
                //目标值在数列的右半部分
                left = mid + 1;
            } else {
                //目标值在数列的左半部分
                right = mid - 1;
            }
        }
        //结束，未找到target，返回-1
        return -1;
    }
}
```

### 变异
> 假如数列中出现了重复项，那我们查到的index便不确定，那如何在重复项得到最小的一个位置呢？
#### 二分查找 + 顺序查找

```java
public int getRepeatIndex(int[] data, int target) {
        int left = 0;
        int right = data.length - 1;
        
        while (left <= right) {
            int mid = left + (right - left) / 2;
            //这里做一改变
            //如果定位到目标值，不立即返回，顺序查找到最靠前的一个
            if(data[mid] == target) {
                while (mid >= 0) {
                    if(data[mid] != target) {
                        break;
                    }
                    mid --;
                }
                //循环时多-1，返回时加上
                return mid + 1;
            } else if(data[mid] < target) {
                //目标值在数列的右半部分
                left = mid + 1;
            } else {
                //目标值在数列的左半部分
                right = mid - 1;
            }
        }
        //如果可以找到，left则为对应的索引值
        if(data[left] == target) {
            return left;
        } else {
            return -1;
        }
    }
```

#### 二分法到底
> 可能大多数考虑到上述的情况就结束了，仔细想想，还可不可以更快一点儿呢，回答是肯定的

```java
public int getRepeatIndex(int[] data, int target) {
        int left = 0;
        int right = data.length - 1;
        //如果数组空直接返回，防止数组越界
        if(data.length == 0) {
            return -1;
        }
        //'<'不是'<=',如果等于会出现死循环
        while (left < right) {
            int mid = left + (right - left) / 2;
            //关键部位！！！
            //保持要查到的值始终是最小索引的，二分查比顺序查要快
            if(data[mid] >= target) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        //如果可以找到，left则为对应的索引值
        if(data[left] == target) {
            return left;
        } else {
            return -1;
        }
    }
```

-------------------