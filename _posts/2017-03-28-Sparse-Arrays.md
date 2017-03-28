---
layout: post
title: HackerRank - Sparse Arrays
---

Selected a problem from the Arrays sections of HackerRank. Using Javascript this time.

### [Problem Statement](https://www.hackerrank.com/challenges/sparse-arrays)

There are N strings. Each string's length is no more than 20 characters. There are also Q queries. For each query, 
you are given a string, and you need to find out how many times this string occurred previously.

### Initial Thoughts

This smells like a HashMap problem to me. I will read the N strings and store them, mapping each key to the number of occurrences. 
I will then loop through the Q queries and print out how many times the string in that query is present in the HashMap. I'll use 
Javascript for this one to try and get out of my always-Java mindset.

```javascript
    function processData(input) {
        var inputArr = input.split('\n');
        var idx = 0;
        var N = parseInt(inputArr[idx]);
        idx++;
        var map = {};
        while(idx <= N) {
            if(!map[inputArr[idx]]) {
                map[inputArr[idx]] = 1;
            } else {
                map[inputArr[idx]]++;
            }
            idx++;
        }

        idx++; // Skip over Q, I can determine how many times to loop without it
        while(idx < inputArr.length) {
            if(map[inputArr[idx]]) {
                console.log(map[inputArr[idx]]);
            } else {
                console.log(0);
            }
            idx++;
        }
    }
```

### Complexity

*Time*: O(n)&nbsp;&nbsp;&nbsp;--> Only loop through the input data once.
   
*Space*: O(n)&nbsp;&nbsp;--> Due to the HashMap.
