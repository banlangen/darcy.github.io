---
layout: post
title: "Leetcode 28. Implement strStr()"
date: 2017-09-14 19:00:00 +0800 
categories: 算法
tags: 
    - ds-string
---
* content
{:toc}

这里收集[`LeetCode`](https://leetcode.com)上的算法题目，并根据能找到的解答，加上自己的理解和思考，重新整理。

<!-- more -->

## Implement strStr()

#### Description

> Implement strStr().  
> Retures the index of the first occurrence of needle in haystack, or -1 if needles is not part of haystack.  

#### Solution

&emsp;&emsp;题意是找needle这个string在haystack里面第一次出现的位置，可以for haystack里面的每一个位置，检查以这个位置开始的串是否与needle相同，但这个复杂度为O(n^2)。这里介绍下KMP算法，KMP算法可以将时间复杂度降低到O(m + n)的时间复杂度。  
&emsp;&emsp;KMP算法的实现建立在一个longest prefix suffix数组上，所以构建这个longest prefix suffix数组是KMP算法的第一步，那么什么是longeset prefix suffix数组？现在我们以LPS数组来代表longest prefix suffix数组，i代表LPS的下标，needle是我们的输入字符串，那么LPS[i]代表的是needle.substr(0, i + 1)(也就是说needle[0]~needle[i]所构成的字符串)中，既是longest proper prefix又是longest proper suffix的子字符串的长度，不明白什么意思？没关系，现在用实例来具体解释。  
&emsp;&emsp;有一个string : "abab"，那么它的proper prefixes就包括，"<fontcolor = red>a</fontcolor>>bab"

#### Code

```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int ret = 0;
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] != val) {
                nums[ret++] = nums[i];
            }
        }
        return ret;
    }
};
```


#### Time Complexity

O(n);