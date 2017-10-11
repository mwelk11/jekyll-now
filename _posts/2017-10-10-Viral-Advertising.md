---
layout: post
title: HackerRank - Viral Advertising
---

I'm back after six months of not posting anything, but don't worry. I've been keeping plenty busy. My girlfriend and I decided to move 
all the way across the country to Seattle! We rented a truck, packed everything up, and drove all the way out. I'm still working for 
Liberty Mutual Insurance; I just transferred from the Boston office to the Seattle one. I'm very excited to see what this city has to offer!

And now let's get into a coding problem! This one was taken from HackerRank. I am going to try something new and use a language that I 
have never used before. I will code this solution in Python. I've heard a lot of great things about this language and I'm excited to learn 
it.

### [Problem Statement](https://www.hackerrank.com/challenges/strange-advertising/problem)

An advertising company sends an advertisement to 5 people. Half of these people (rounding down) will "like" the advertise and show it to 
3 friends. The other half with delete the advertisement. Of the next group of people that see the advertisement, the same thing happens. 
Half will "like" it and show it to 3 friends, and half will delete it. This pattern continues each day, with one group of people being shown the 
advertisements per day. Given the number of days, n, output the total number of people who "liked" the advertisement.

### Initial Thoughts

This seems like a fairly simple problem. I wanted to keep it simple for my first time using Python. We should just have to loop over 
the number of days, and for each day we calculate the number of people who "liked" the advertisement and add it to the total. We can 
calculate the number of people who "like" an advertisement by dividing the total number who received the advertisement that day by 2 and 
dropping the remainder. We multiple this by 3 to get the total number of people who see the advertisement for the next day.

Here is the code:

```python
  import math
  import sys

  n = int(input())

  total = 0
  people = 5

  while (n > 0):
    liked = math.floor(people/2)
    total += liked
    n = n-1
    people = 3*liked

  print (total)
```

### Complexity

*Time*: O(n)&nbsp;&nbsp;--> Need to loop through the number of days
   
*Space*: O(1)&nbsp;&nbsp;--> Constant
