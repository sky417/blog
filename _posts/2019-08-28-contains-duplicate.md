---
layout: post
current: post
navigation: True
class: post-template
subclass: 'post'
title: Contains Duplicate
tags: [coding,leetcode]
author: ayoon
---
[Contains Duplicate]("https://leetcode.com/problems/contains-duplicate/")

별거 없다 이번꺼는. 새 아이템은 Hashmap에 넣고, 만약 해당 key가 이미 있으면 True.
Time O(n), space O(n)

```python
class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        
        '''
        Use dict, if key exists return True
        '''
        dict = {}
        
        for i in range(0, len(nums)):
            if nums[i] in dict:
                return True
            else:
                dict[nums[i]] = 1
                
        # no duplicate found. false
        return False
```