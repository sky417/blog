---
layout: post
current: post
navigation: True
class: post-template
subclass: 'post'
title: Two Sum
tags: [coding,leetcode]
author: ayoon
---
[Two Sum](https://leetcode.com/problems/two-sum/)

python syntax 연습도 할 겸, 그리고 이제 C로는 그만 좀 해야지.. 해서 python으로 하기로 했다. <br />
이번에는 좀 꾸준히 많이 풀어 보자. Hackerrank를 할까 Leetcode를 할까 하다가 그냥 Leetcode 1번부터 차례로 풀기로 정했다.

첫번째의 brute force로 풀면 간단하긴 하지만 시간이 정말 오래 걸린다. <br />
짱구를 열심히 굴린 두번째 방법은 O(n log n) 으로 줄어서 시간이 많이 빨라졌다. <br />
중간에 있는 오답은 신경쓰지 말자... <br />
Hash를 쓰면 O(n)까지 갈수 있을텐데.. 내일 하자.

<img src="/blog/assets/images/twosum.png" witdh="50">

```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        ret = []

        '''
        Easy brute force, O(n^2)

        for i in range(0, len(nums)):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    ret.append(i)
                    ret.append(j)
                    return ret
        '''

        '''
        1) Sort first with O(nlogn) to new_nums --- O(nlogn)
        2) Then start from new_nums[0] + new_nums[len(new_nums)] --- O(n)
        3) If found, find the index from nums --- O(n)
        Overall O(nlogn)
        '''
        new_nums = sorted(nums)
        left = 0
        right = len(new_nums) - 1
        while True:
            sum = new_nums[left] + new_nums[right]
            if sum == target:
                idx1 = nums.index(new_nums[left])
                nums.remove(nums[idx1])

                idx2 = nums.index(new_nums[right])
                if idx2 >= idx1:
                    idx2 += 1

                ret.append(idx1)
                ret.append(idx2)
                return ret
            elif sum < target:
                left += 1
            else:
                right -= 1

            if left == right:
                # no such pair, return empty list
                return ret

        # no such pair, return empty list
        return ret
```
