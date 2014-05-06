---
layout: default-narrow
title: CS Cheat Sheet
group: navigation
markdown: redcarpet
permalink: cs-cheat-sheet/
---

<table class="table">
  <tr>
    <th>Data Structures</th>
    <th>Algorithms</th>
    <th>Concepts</th>
  </tr>
  <tr>
    <td>Linked List</td>
    <td>BFS</td>
    <td>Bit Manipulation</td>
  </tr>
  <tr>
    <td>Binary Tree</td>
    <td>DFS</td>
    <td>Singleton</td>
  </tr>
  <tr>
    <td>Tries</td>
    <td>Binary Search</td>
    <td>Factory</td>
  </tr>
  <tr>
    <td>Stacks</td>
    <td>Merge Sort</td>
    <td>Memory (Stack vs Heap)</td>
  </tr>
  <tr>
    <td>Queue</td>
    <td>Quick Sort</td>
    <td>Recursion</td>
  </tr>
  <tr>
    <td>Vector/ArrayList</td>
    <td>Tree Insert/Find</td>
    <td>Big-O</td>
  </tr>
  <tr>
    <td>Hash Table</td>
    <td></td>
    <td></td>
  </tr>
</table>

<hr />

## Arrays

#### Rotated Array

* Elements shifted so that they're still sorted up to a `pivot`
* Finding an element
  * Split array into two at the mid-point.
    * If mid-point is key, return
    * If left-most < mid-point, then LHS is sorted. Else, RHS is sorted.
    * Whichever side is sorted, see if the key is between the range. If so, look in that range on next iteration.

### Problems

**1.1 - Determine if a string has all unique characters**

* Unicode or Ascii (128)?
* Array of booleans. Time: O(n), Space: O(1). Or also bit vector.
* Suboptimal: Compare each character. Time: O(n<sup>2</sup>)
* Sort string in O(n log n) time.

**1.3 - Determine if two strings are permutations of each other.**

* Sort the string
* Identical character count

**1.6 - Rotate an NxN Image 90 degrees**

* Proceed Layer by layer. Instead of swapping out an entire side at a time (takes N space), swap in place.
* At best, this runs in O(n<sup>2</sup>) time

**1.7 - Write an algorithm such that if an element in an MxN matrix is 0, its entire row and column will be 0**

* Iterate through matrix. For each 0, note column and row in two separate arrays (don't need the exact point)
* Iterate through matrix again. For each element in rowArray, zero out the row.

**1.8 - Write an isRotation() by using isSubstring() once to determine if s2 is a rotation of s1**

* isSubstring(s1+s1, s2)





** Binary Tree **

* **Path** from n<sub>1</sub> to n<sub>k</sub>: n<sub>i</sub> is the **parent** of n<sub>i+1</sub> for *i* in (1, k)
* **Length** of path is *k - 1*
* 










