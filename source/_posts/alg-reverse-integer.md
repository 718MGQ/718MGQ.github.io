---
title: 整数反转
date: 2020-06-13 13:14:04
tags:
- leetcode
- algorithm
- 面试题
categories:
- 算法
---

### 题目 
[力扣](https://leetcode-cn.com/problems/reverse-integer/)
> Given a 32-bit signed integer, reverse digits of an integer.
> 给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。

<!--more-->
### 分析
> 整数反转当然容易，但是要注意的是32位，溢出问题怎么处理？这里提供三种方式：**String**、**Long**、**Int**(***推荐***)

### 方法一：String
> 利用StringBuffer 的reverse()方法，进行逆置

```java
class Solution {
    public int reverse(int x) {
        //非负数标记，false为负数
        boolean flag = true;
        if(x < 0) {
            //如果x为-2147483648，-x超过Integer.MAX_VALUE
            if(x == Integer.MIN_VALUE) {
                return 0;
            }
            flag = false;
            x = -x;
        }
        //如果为负数，加-号
        String str = flag ? new StringBuffer(String.valueOf(x)).reverse().toString() : "-" + new StringBuffer(String.valueOf(x)).reverse();

        //判断是否超过Integer值范围
        if(Long.valueOf(str) > Integer.MAX_VALUE || Long.valueOf(str) < Integer.MIN_VALUE) {
            return 0;
        }
        return Integer.valueOf(str);
    }
}
```

### 方法二：Long
> 用Long值存下,对long值进行反转，最后再判断范围

```java
class Solution {
    public int reverse(int x) {
        Long result = 0L;
        //不断的取x的最后一位，加到result后面
        while(x != 0) {
            result = result * 10 + x % 10;
            x /= 10;
        }

        //判断是否超过Integer值范围
        if(result > Integer.MAX_VALUE || result < Integer.MIN_VALUE) {
            return 0;
        }
        return result.intValue();
    }
}
```

### 方法三：Int
> 以上两种方法都可以很好的解决这个问题，但是我们反思一下，或者我们来强制的加个条件，如果在运行中只能使用32位的整数，该怎么办呢？虽然现在的内存已经不宝贵了，但是我们还是要爱惜一下嘛～
> 那么更好的方法来了，这个题的关键就是输入值x在反转的过程中可能会超过int值的范围，那我们在循环的取数的时候，每次去判断下一个值是否会超过int的范围，这不就OK了

```java
class Solution {
    public int reverse(int x) {
        int result = 0;
        //不断的取x的最后一位，加到result后面
        while(x != 0) {
            int pop = x % 10;
            x /= 10;
            //判断是否超过Integer值范围
            if(result > Integer.MAX_VALUE / 10 || (result == Integer.MAX_VALUE / 10 && pop > Integer.MAX_VALUE % 10)) {
                return 0;
            }
            if(result < Integer.MIN_VALUE / 10 || (result == Integer.MIN_VALUE / 10 && pop < Integer.MIN_VALUE % 10)) {
                return 0;
            }
            result = result * 10 + pop;
        }
        return result;
    }
}
```

----------------------