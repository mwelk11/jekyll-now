---
layout: post
title: Cracking the Coding Interview - Group Anagrams
---

I took this problem from the book *Cracking the Coding Interview* by Gayle Laakmann McDowell.

### Problem Statement

Write a method to sort an array of strings so that all anagrams are next to each other.

### Initial Thoughts

The first piece of information needed to solve this problem is the definition of an anagram. Two words are anagrams if they have all 
the same characters and same number of occurrences of those characters. Essentially just one word that is a rearrangement of another. 
The easiest way I could think of to determine if two words are anagrams was to sort the characters in the strings and then compare. If 
the strings are anagrams of one another, then their sorted character arrays will match.

The more difficult part of the problem was to actually sort the array so that the anagrams are together. I initially thought to use an 
in place sorting algorithm; I tried to come up with a variation of quicksort to fit my needs. This proved to be more complicated than 
I expected. Eventually I realized that an easier method was to use a HashMap and use the sorted array as a key, and map to a 
list of strings which are anagrams of that sorted array. I could then iterate through the HashMap and repopulate the list with all the 
anagrams next to each other.

Here is the code:

```java
  void groupAnagrams(String[] arr) {
      HashMap<String, ArrayList<String>> hm = new HashMap<String, ArrayList<String>>();
      for(String s : arr) {
          char[] sorted = s.toCharArray();
          Arrays.sort(sorted);
          String sortedStr = new String(sorted);
          
          if(!hm.containsKey(sortedStr)) {
              hm.put(sortedStr, new ArrayList<String>());
          }
          hm.get(sortedStr).add(s);
      }

      int idx = 0;
      for(String s : hm.keySet()) {
          for(String s2 : hm.get(s)) {
              arr[idx] = s2;
              idx++;
          }
      }
  }
```

### Complexity

*Time*: O(n)&nbsp;&nbsp;--> Need to loop through entire list of Strings
   
*Space*: O(n)&nbsp;&nbsp;--> Due to the HashMap
