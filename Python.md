# Leetcode - Python Summary

### 1. Two Sum
Input: nums = [2,7,11,15], target = 9 </br>
Output: [0,1] </br>
Output: Because nums[0] + nums[1] == 9, we return [0, 1]. </br>
#### Method 1: Brute Force
```
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        for i in range(len(nums)-1):
            for j in range(i+1, len(nums)-1):
                if(nums[i]+nums[j]==target):
                    return([i,j])
```
#### Method 2: Hash Table
```
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        hashmap = {}
        for i in range(len(nums)):
            if(nums[i] in hashmap):
                return [hashmap[nums[i]],i]
            hashmap[target-nums[i]] = i
```


### 2. Container With Most Water
Input: height = [1,8,6,2,5,4,8,3,7] </br>
Output: 49 </br>
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49. </br>
#### Method 1: Brute Force
```
class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        max = 0
        for i in range(len(height)-1):
            for j in range(i+1,len(height)):
                area = min(height[i],height[j]) * (j-i)
                if area > max:
                    max = area
        return max
```
#### Method 2:
```
class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        
        i = 0
        j = len(height)-1
        max = 0
        
        while i!=j:
            area = min(height[i],height[j])*(j-i)
            if area > max:
                max = area
            if height[i] >= height[j]:
                j -= 1
            else:
                i += 1

        return max
```

### 3. Find First and Last Position of Element in Sorted Array
Input: nums = [5,7,7,8,8,10], target = 8 </br>
Output: [3,4] </br>
Input: nums = [5,7,7,8,8,10], target = 6 </br>
Output: [-1,-1] </br>
Input: nums = [], target = 0 </br>
Output: [-1,-1] </br>
#### Method 1:
