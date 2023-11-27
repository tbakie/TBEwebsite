+++
title = "LeetCode"
date = "2023-10-16T11:02:08-07:00"
author = " Efesoy "


+++
 I will post the interview questions I did here on **leetcode** and share important information about them here, such as important points I found important, parts I had difficulty with and new things I learned.

## Question 1480
Given an array nums. We define a running sum of an array as runningSum[i] = sum(nums[0]…nums[i])
Return the running sum of nums.
👇 
- This is a basic beginner question, but one line is important for me, which is **nums[i] += nums[i - 1]** instead of **nums[i] += nums[i + 1]**   
```java
class Solution {
public int[] runningSum(int[] nums) {
        for (int i = 1; i < nums.length; i++) {
            // Result at index `i` is sum of result at `i-1` and element at `i`.
            nums[i] += nums[i - 1];
        }
        return nums;
    }
}
```