## 题目描述

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

 

**Example 1:**

```
Input: nums = [1,2,3,1]
Output: true
```

**Example 2:**

```
Input: nums = [1,2,3,4]
Output: false
```

**Example 3:**

```
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true
```

 

**Constraints:**

- `1 <= nums.length <= 105`
- `-109 <= nums[i] <= 109`

------

> ### 三种解法
>
> 1. 暴力解法
> 2. Sorting解法
> 3. Set解法：最优解（set会把重复的东西去掉）
>

## 暴力解法

#### Pyhton3

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        for i in range(len(nums)):
            for j in range (i + 1, len(nums)):
                if nums[i] == nums[j]:
                    return True
        return False
```

执行用时：超出时间限制（提交不过）

## Sorting解法

#### Pyhton3

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        nums.sort()

        for i in range (1, len(nums)):
            if nums[i] == nums[i-1]:
                return True
        return False
```

执行用时：104 ms

内存消耗：23.9 MB

## Set解法

#### Python3

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return True if len(set(nums)) != len(nums) else False

```

执行用时：60 ms

内存消耗：25.6 MB