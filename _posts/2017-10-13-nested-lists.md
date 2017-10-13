---
layout: post
title: HackerRank - Second Lowest Grade
---

I'm doing another Python problem today. Again, nothing too crazy but just trying to pickup on the different data structures that can be 
used and the differences between this language and my usual Java.

### [Problem Statement](https://www.hackerrank.com/challenges/nested-list/problem)

Given the names and grades for each student in a Physics class, print the student(s) with the second lowest grade. If multiple students 
have the second lowest grade, then print them in alphabetical order.

### Initial Thoughts

The problem says to use a nested list. I tried a nested list, but then switched to a dictionary because it seemed more logical to me. 
This is a pretty obvious key->value problem in my opinion. I use the name as the key and grade as the value. This assumes that there are 
no duplicate names in the class, which should be the case for the majority of classes if we are using full names. If we happen to get two 
students with the same exact full name, then we could enhance this to use unique student ID's as the keys.

In order to find the second lowest grade, I extracted the dictionary values into a list. I grab the min of the list and then remove that 
value from everywhere in the list since there can be multiple students with the minimum grade. I then grab the min again, which should 
now be the second lowest grade. I then iterate through the dictionary in sorted order and print out the names that are associated with 
the second lowest grade. Because I am iterating in sorted order, this will print out the names alphabetically if there are multiple.

Here is the code:

```python
  if __name__ == '__main__':
    arr = {}
    for _ in range(int(input())):
        name = input()
        score = float(input())
        arr[name] = score
    
    grades = sorted(arr.values())
    minGrade = min(grades)
    while minGrade in grades:
        grades.remove(minGrade)
    minGrade = min(grades);
    
    for x, y in sorted(arr.items()):
        if y == minGrade:
            print (x)
```

### Complexity

*Time*: O(n)&nbsp;&nbsp;--> Need to loop through each student
   
*Space*: O(n)&nbsp;&nbsp;--> Because I use a dictionary
