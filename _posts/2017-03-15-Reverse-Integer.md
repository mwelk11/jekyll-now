---
layout: post
title: LeetCode - Reverse Integer
---

### [Problem Statement](https://leetcode.com/problems/reverse-integer/#/description)

Reverse digits of an integer. The input is assumed to be a 32-bit signed integer. 
Your function should return 0 when the reversed integer overflows.

### Initial Thoughts

I know that I can retrieve the singles digit of any number by doing a modulo operation with that number and 10. 
I can remove the singles digit from the number by dividing that number by 10 (since the remainder will be trunctated). 
I should be able to continually do these operations in a loop until I have reversed the number. 
This should work the same exact way for positive and negative numbers.

The part that stumped me was to return a 0 if an integer overflow occurred. I needed some sort of method that would throw an
exception if an overflow occurred. I could not think of a method to use off the top of my head, so I did a quick Google search 
and was able to find the Math.multiplyExact and Math.addExact methods. These methods will do the arithmetic that I need, and will 
throw an unchecked Arithmetic Exception if an Integer overflow occurs.

```java
  public int reverse(int x) {
      int reverseNum = 0;
      while(x != 0) {
          try {
              reverseNum = Math.multiplyExact(reverseNum, 10);
              reverseNum = Math.addExact(reverseNum, (x%10));
          } catch(ArithmeticException e) {
              return 0;
          }
          x = x/10;
      }
      return reverseNum;
  }
```

### Complexity

*Time*: O(log n)&nbsp;&nbsp;--> Dividing the input by 10 on every loop.
   
*Space*: O(1)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;--> Constant space. I only declare one variable in this method (reverseNum).
