## 题目描述

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have ***exactly\* one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

 

**Example 1:**

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**Example 2:**

```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**Example 3:**

```
Input: nums = [3,3], target = 6
Output: [0,1]
```

 

**Constraints:**

- `2 <= nums.length <= 104`
- `-109 <= nums[i] <= 109`
- `-109 <= target <= 109`
- **Only one valid answer exists.**

------

> ### 三种解法
>
> 1. 暴力解法
>    - 两个for loop
> 2. Hashmap解法
> 3. 用 Two pointers解法（假如input已经由小到大排序好了）
>

## 暴力解法

#### Pyhton3

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range (len(nums)):
            for j in range (i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i, j]
```

执行用时：3176 ms

内存消耗：15.4 MB

## Hashmap解法

#### Pyhton3

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        # 建立Hashmap
        lookup = {}

        for idx, number in enumerate(nums):
            if target - number in lookup:
                return [idx, lookup[target - number]]
            else:
                # 更新Hashmap
                lookup[number] = idx
```

执行用时：36 ms

内存消耗：16 MB

## Two pointers解法

#### Python3

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        # if nums is sorted
        # [2,7,11,15]
        sorted_num = sorted(zip(nums, range(len(nums))))   
        # sorted_num: [(2,0), (7,1), (11,2), (15,3)]

        left = 0
        right = len(nums) - 1

        while  left < right:
            value = sorted_num[left][0] + sorted_num[right][0]

            if value == target:
                return [sorted_num[left][1], sorted_num[right][1]]
            if value < target:
                left += 1
            if value > target:
                right -= 1

```

执行用时：48 ms

内存消耗：16.2 MB（额外做了一个sorted）