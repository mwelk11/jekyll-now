---
layout: post
title: HackerRank - Min Max Sum
---

This is my first coding problem post! I hope you enjoy!

### [Problem Statement](https://www.hackerrank.com/challenges/mini-max-sum)

Given five positive integers, find the minimum and maximum values that can be calculated by summing exactly four of the five integers. 
Then print the respective minimum and maximum values as a single line of two space-separated long integers.

#### Initial Thoughts

I decided to implement a function that takes in an array of any size, and calculates the min/max sum of that array minus one number. 
If we are calculating the min/max of a set of numbers by removing one number, then the min can be calculated by removing the 
largest number, and the max can be calculated by removing the smallest number.

```java
public void minMaxSum(long[] nums) {

  long min = nums[0];
  long max = nums[0];
  long sum = 0;
  
  for(int i = 0; i < nums.length; i++) {
      if(nums[i] < min) {
          min = nums[i];
      }
      if(nums[i] > max) {
          max = nums[i];
      }
      sum += nums[i];
  }

  System.out.println((sum-max) + " " + (sum-min));
}
```

I can calculate the min, max, and sum all within one loop of the array. I then subtract the max from the sum in order to calculate 
the min sum. I subtract the min from the sum in order to calculate the max sum. I print both of these values to the console.

### Complexity

*Time*: O(n)&nbsp;&nbsp;&nbsp;&nbsp;--> Only loop through the array one time   
   
*Space*: O(1)&nbsp;&nbsp;&nbsp;--> Constant space. I store three variables every time (min, max, sum).
