---
layout: post
current: post
navigation: True
class: post-template
subclass: 'post'
title: Add Two Numbers
tags: [coding,leetcode]
author: ayoon
---
[Add Two Numbers]("https://leetcode.com/problems/add-two-numbers/")

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def parseList(self, ll):
        num = 0
        iter = ll
        power = 0
        while True:
            num += iter.val * (10 ** power)
            if iter.next is None:
                break
            else:
                iter = iter.next
                power += 1

        return num

    def numToList(self, num):
        l = ListNode(num % 10)
        iter = l
        num /= 10

        while num > 0:
            iter.next = ListNode(num % 10)
            iter = iter.next
            num /= 10

        return l

    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """

        '''
        1) parse lists into number
        2) convert the sum int list and return
        '''
        num1 = self.parseList(l1)
        num2 = self.parseList(l2)

        sum = num1 + num2
        print num1, "+", num2, "=", sum

        return self.numToList(sum)
```
