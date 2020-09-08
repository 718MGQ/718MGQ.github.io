---
title: 链表逆置
date: 2020-06-12 20:00:04
tags:
- leetcode
- algorithm
- 面试题
categories:
- 算法
---

### 链表逆置
> 定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。

示例：
> 输入: 1->2->3->4->5->NULL
> 输出: 5->4->3->2->1->NULL

<!--more-->
### 解题
> 头插法简单明了 [code](https://leetcode-cn.com/problems/fan-zhuan-lian-biao-lcof/)
```
public class ReverseList {
    /**
     * Definition for singly-linked list.
     */
    public static class ListNode {
        int val;
        ListNode next;

        ListNode(int x) {
            val = x;
        }
    }

    public ListNode getReverseList(ListNode head) {
        //定义一个空的头节点
        ListNode newList = new ListNode(-1);
        while (head != null) {
            //定一个临时指针，指向下一个节点
            ListNode nextNode = head.next;
            //断开当前节点与下一个节点连接，并接到新链表的前面
            head.next = newList.next;
            //当前节点插入到头节点之后（头插法）
            newList.next = head;
            //当前节点向后移
            head = nextNode;
        }
        return newList.next;
    }
}
```

------------------