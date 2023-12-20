+++
title = "LeetCode"
date = "2023-10-16T11:02:08-07:00"
author = " Efesoy "


+++
 I will post the interview questions I did here on **leetcode** and share important information about them here, such as important points I found important, parts I had difficulty with and new things I learned.


 ## Palindrome Number
Given an integer x, return true if x is a palindrome(An integer is a palindrome when it reads the same forward and backward.), and false otherwise.
👇
- I wanted to convert this integer to String first, and the most important point is **size/2**, because if the size is odd, we do not touch the middle number and easily iterate front and back one by one.
 ```java
class Solution {
    public boolean isPalindrome(int x) {
        String s = String.valueOf(x);
        System.out.println(s);
        int size = s.length();

        for(int i = 0; i < size/2; i++){
            if(s.charAt(i) != s.charAt(size-i-1)){
                return false;
            }
        }
        return true; 
    }
}
 ``` 

## Two Sum
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
👇
- The important thing for me is **j = i + 1** and **nums.length - 1** therefore i and j will be never equal
```java
 class Solution {
    public int[] twoSum(int[] nums, int target) {
        
        for (int i = 0; i < nums.length - 1; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[]{};
    }
}
```

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