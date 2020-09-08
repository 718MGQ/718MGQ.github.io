---
title: 爬楼梯
tags:
  - leetcode
  - 面试题
categories:
  - 算法
date: 2020-08-11 16:32:52
---

### 题目描述(leetcode 70)
> 假设你正在爬楼梯。需要 n 阶你才能到达楼顶。
每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？
注意：给定 n 是一个正整数。

    不建议使用递归，当n很大的时候，递归会超时！

<!--more-->
#### 解法一：流处理
```java
class Solution {
    public int climbStairs(int n) {
        int[] res =  Stream
                .iterate(new int[]{1, 2}, f -> new int[]{f[1], f[0] + f[1]})
                .limit(n)
                .mapToInt(f -> f[0])
                .toArray();
        return res[res.length - 1];
    }
}
```

#### 解法二：迭代
```java
class Solution {
    public int climbStairs(int n) {
        if(n <= 2) {
            return n;
        }
        int first = 0, second = 1;
        while(n-- != 0) {
            int tmp = second;
            second = first + second;
            first = tmp;
        }
        return second;
    }
}
```