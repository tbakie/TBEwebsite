+++
title = "LeetCode"
date = "2023-10-16T11:02:08-07:00"
author = " Efesoy "


+++
 I will post the interview questions I did here on **leetcode** and share important information about them here, such as important points I found important, parts I had difficulty with and new things I learned.

 ## Longest Common Prefix
Write a function to find the longest common prefix string amongst an array of strings.
If there is no common prefix, return an empty string "".
👇
- I actually watched editorial video to get some help, becasue I stucked at how to find common letter, because I was trying to examine the words letter by letter. Moreover I also noticed **strs[index].indexOf(prefix) == 0** means they are same
 ```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if(strs.length == 0){
            return "";
        }
        
        String prefix = strs[0];
        for(int index = 1; index < strs.length; index++){
            while(strs[index].indexOf(prefix) != 0){
                prefix = prefix.substring(0, prefix.length() - 1);
                if(prefix.isEmpty()){
                    return "";
                }
            }
        }
        
        return prefix;
    }
}
 ```

## Roman to Integer
Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX.
👇
- I use map to match character corresponding to the their numbers. The important thing was **m.get(s.charAt(i)) < m.get(s.charAt(i + 1))** Therefore we can get IX as a "9" not "11".
```java
class Solution {
    public int romanToInt(String s) {
        Map<Character, Integer> m = new HashMap<>();
        
        m.put('I', 1);
        m.put('V', 5);
        m.put('X', 10);
        m.put('L', 50);
        m.put('C', 100);
        m.put('D', 500);
        m.put('M', 1000);
        
        int ans = 0;
        
        for (int i = 0; i < s.length(); i++) {
            if (i < s.length() - 1 && m.get(s.charAt(i)) < m.get(s.charAt(i + 1))) {
                ans -= m.get(s.charAt(i));
            } else {
                ans += m.get(s.charAt(i));
            }
        }
        
        return ans;
    }
}
```


 ## FIZZ BUZZ
 Given an integer n, return a string array answer (1-indexed) where:
answer[i] == "FizzBuzz" if i is divisible by 3 and 5.
answer[i] == "Fizz" if i is divisible by 3.
answer[i] == "Buzz" if i is divisible by 5.
answer[i] == i (as a string) if none of the above conditions are true.
👇
- The key of the solving problem is making **divisibleBy3** and **divisibleBy5**

```java
class Solution {
    public List<String> fizzBuzz(int n) {

        // ans list
        List<String> ans = new ArrayList<String>();

        for (int num = 1; num <= n; num++) {

            boolean divisibleBy3 = (num % 3 == 0);
            boolean divisibleBy5 = (num % 5 == 0);

            if (divisibleBy3 && divisibleBy5) {
                // Divides by both 3 and 5, add FizzBuzz
                ans.add("FizzBuzz");
            } else if (divisibleBy3) {
                // Divides by 3, add Fizz
                ans.add("Fizz");
            } else if (divisibleBy5) {
                // Divides by 5, add Buzz
                ans.add("Buzz");
            } else {
                // Not divisible by 3 or 5, add the number
                ans.add(Integer.toString(num));
            }
        }

        return ans;
    }
}
```

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