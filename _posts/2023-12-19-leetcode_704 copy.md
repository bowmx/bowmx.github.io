---
layout: post
title: 日拱一卒之leetcode-704
date: 2023-12-19 00:35 +0800
categories: [日拱一卒, 算法]
tags: [算法]   
---
## leetcode-704 二分查找
### 思路
- 复健第一题, 没啥说的. 但有一个需要注意的点就是要注意数组的遍历区间**是开区间**还是**左开右闭** 
- 做以后其它需要遍历数组的题也要注意遍历的区间, 先确定区间, 一旦确定区间后严格按照区间定义去写代码
### Code
#### C++
```c++
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int left = 0;
        int right = nums.size() - 1;

        while (left <= right) {
            int mid = left + (right - left) >> 2;  
            if (nums[mid] == target) {
                return mid;    
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return -1;
    }
};
```
#### Python
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left = 0
        right = len(nums)- 1

        while left <= right:
            mid = left + (right - left) // 2

            if nums[mid] == target:
                return mid
            elif nums[mid] > target:
                right = mid - 1
            else: 
                left = mid + 1
                
        return -1
```