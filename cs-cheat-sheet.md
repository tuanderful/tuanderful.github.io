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
    <td>Obj Oriented</td>
  </tr>
</table>

<hr />

# Arrays

### Rotated Array

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









# Linked Lists

### Implementation

In all implementations, consider the case if the iterator (or head) points to null.

* `insert(x, p)` - Iterate to `p`. Set `x.next = p.next`, `p.next = x`
* `remove(x)` - As you iterate, if `itr.next.value = x`, then `itr.next = iter.next.next`

### Stack ADT

* **LIFO** Insertions and deletions can only be performed at the *top*
* **Postfix expressions** - Calculate 6 5 2 3 + 8 * + 3 + *
  * When a number is seen, push it on the stack
  * When an operator is seen, pop two numbers from the stack, apply operator, push result

### Queue ADT

* TBD








# Binary Tree

* **Path** from n<sub>1</sub> to n<sub>k</sub>: n<sub>i</sub> is the **parent** of n<sub>i+1</sub> for *i* in (1, k)
* **Length** of path is *k - 1*
* No node can have more than 2 children.
* Average depth is &radic;(2), worst case O(N-1)
* Traversal strategies
  * Pre-Order - perform work on node before processing children
  * In-Order - perform work on left child, current node, then right child
  * Post-Order - perform work on children before current node

### Simple Implementation

* Keep references to `firstChild` and `nextSibling`

### Binary Search Tree

<table class="table table-condensed">
  <tr>
    <td></td>
    <td>Indexing</td>
    <td>Search</td>
    <td>Insertion</td>
    <td>Deletion</td>
  </tr>
  <tr>
    <td>Average</td>
    <td><span class="btn btn-warning btn-xs">O(log n)</span></td>
    <td><span class="btn btn-success btn-xs">O(log n)</span></td>
    <td><span class="btn btn-success btn-xs">O(log n)</span></td>
    <td><span class="btn btn-success btn-xs">O(log n)</span></td>
  </tr>
  <tr>
    <td>Worst</td>
    <td><span class="btn btn-danger btn-xs">O(n)</span></td>
    <td><span class="btn btn-danger btn-xs">O(n)</span></td>
    <td><span class="btn btn-danger btn-xs">O(n)</span></td>
    <td><span class="btn btn-danger btn-xs">O(n)</span></td>
  </tr>
</table>

* For any node n, value of nodes on left subtree are smaller than n.value (similarly, right subtree nodes are greater)
* Average depth of BST is O(log n)
* `findMin()` - Traverse straight down the left side. Perhaps more efficient if done iteratively and not recursively.
* `findMax()` - 
* `find()` - Consider 4 cases:
  * If null, return
  * If less than current node value, go left.
  * If greater than current node value, go right.
  * Else return current node (equal). *(Match is least likely if/else case)*
* `insert()` - Similar to `find()`, but in the null case, create a new node.
* `remove(n)` - 
  * If node is leaf, remove immediately
  * If `n` has child, then delete `n` after parent has adjusted to point to the child

* **Lazy deletion** Instead of updating pointers, simply mark element as beind deleted, or update the count on the node.


### AVL Tree

* For every node, the height of the left and right subtrees can differ by at most 1
* Insertion
  * Outside: Single rotation
  * Inside: Double rotation

<table class="table table-condensed">
  <tr>
    <td></td>
    <td>Indexing</td>
    <td>Search</td>
    <td>Insertion</td>
    <td>Deletion</td>
  </tr>
  <tr>
    <td>Average</td>
    <td><span class="btn btn-warning btn-xs">O(log n)</span></td>
    <td><span class="btn btn-success btn-xs">O(log n)</span></td>
    <td><span class="btn btn-success btn-xs">O(log n)</span></td>
    <td><span class="btn btn-success btn-xs">O(log n)</span></td>
  </tr>
  <tr>
    <td>Worst</td>
    <td><span class="btn btn-warning btn-xs">O(log n)</span></td>
    <td><span class="btn btn-success btn-xs">O(log n)</span></td>
    <td><span class="btn btn-success btn-xs">O(log n)</span></td>
    <td><span class="btn btn-success btn-xs">O(log n)</span></td>
  </tr>
</table>






# Hash Table

* Ensure table size is prime
* **Horner's Rule** Polynomial expansion

        for(i in [0:length]): hashVal = 37 * hashVal + key[i]
        hashVal %= tableSize

* **Separate Chaining** Keep list of all elements that hash to the same value
  * Make table sie about as large as number of elements expected (load &lambda; &asymp; 1)

* **Open Addressing**
  * Resolve collision by looking at the next open slot
  * Results in *primary clustering*

* **Quadratic Probing** Look 1, 4, 9... i^2 away
  * No garauntee empty cell can be found if table is more than half full (&lambda; > .5)

* Rehasing
  * Rehash when insertion fails, or when load factor reaches a certain size







# Priority Queue (Heaps)

### Binary Heap

* Heaps have two properties:
  * **Structure** - Tree is completely filled. Can be implemented with an array.
  * **Heap Order** - For every node X, the key in the parent of X is smaller than the key in X.

* `insert` Start at end, *percolate up*, swapping nodes as needed
* `deleteMin` - create hole at root, then swap with the smaller of two children.

#### Selection Problem

Find the *k*th largest element.

* Build heap (in O(N) time), then perform *k* deleteMin operations (in O(k log N) time)












# Graphs

### Implementation

* `adjacencyList = []`
* `numVertices`
* `numEdges`
* `addEdge()` - need to increment edge count

### Depth-First Search (good for Toplogical Sort)

Follow a path from beginning to end before backtracking to the first level.

* Keep an array of marked vertices
* Traverse down each adjacent node
  * Look at 'children' before looking at 'neighbors'

{% highlight javascript %}function depthFirst(v, cb) {
  var marked = [];
  // for(var i = 0; i < numVertices; i++) this.marked = false;

  dfs(v);
  
  function dfs(someV) {
    marked[someV] = true;

    cb();

    for each (var w in adj.[v]) {
      if (!marked[v]) {
        dfs(w);
      }
    }
  }
}{% endhighlight %}


### Breadth-First Search (good for Shortest Path Algorithm)

* Queue up unvisited vertices.
* For each unvisited vertex, look at its adjacent vertices.
  * If they haven't been visited, queue them up.

{% highlight javascript %}function breadthFirst(s) { 
  var queue = [];
  var marked = [];
  // for(var i = 0; i < numVertices; i++) this.marked = false;

  queue.push(s);

  while (queue.length) {
    var v = queue.shift();

    // process element

    for each (var w in adj.[v]) {
      if (!marked[v]) {
        
      }
    }
  }
}{% endhighlight %}






# Sorting

<table class="table table-condensed">
  <tr>
    <td></td>
    <td>Best</td>
    <td>Average</td>
    <td>Worst</td>
    <td>Use Case</td>
  </tr>
  <tr>
    <td>Insertion</td>
    <td><span class="btn btn-warning btn-xs">n</span></td>
    <td><span class="btn btn-danger btn-xs">n<sup>2</sup></span></td>
    <td><span class="btn btn-danger btn-xs">n<sup>2</sup></span></td>
    <td>Small list, or mostly sorted</td>
  </tr>
  <tr>
    <td>Selection Sort</td>
    <td><span class="btn btn-danger btn-xs">n<sup>2</sup></span></td>
    <td><span class="btn btn-danger btn-xs">n<sup>2</sup></span></td>
    <td><span class="btn btn-danger btn-xs">n<sup>2</sup></span></td>
    <td></td>
  </tr>
  <tr>
    <td>Heap Sort</td>
    <td><span class="btn btn-warning btn-xs">n log n</span></td>
    <td><span class="btn btn-success btn-xs">n log n</span></td>
    <td><span class="btn btn-success btn-xs">n log n</span></td>
    <td>Good worst-case</td>
  </tr>
  <tr>
    <td>Merge Sort</td>
    <td><span class="btn btn-warning btn-xs">n log n</span></td>
    <td><span class="btn btn-success btn-xs">n log n</span></td>
    <td><span class="btn btn-success btn-xs">n log n</span></td>
    <td></td>
  </tr>
  <tr>
    <td>Quick Sort</td>
    <td><span class="btn btn-warning btn-xs">n log n</span></td>
    <td><span class="btn btn-success btn-xs">n log n</span></td>
    <td><span class="btn btn-danger btn-xs">n<sup>2</sup></span></td>
    <td>Good average case</td>
  </tr>
  <tr>
    <td>Bucket</td>
    <td><span class="btn btn-success btn-xs">n</span></td>
    <td><span class="btn btn-success btn-xs">n</span></td>
    <td><span class="btn btn-danger btn-xs">n<sup>2</sup></span></td>
    <td>Dense universe of items.</td>
  </tr>
  <tr>
    <td>Count Sort</td>
    <td><span class="btn btn-success btn-xs">n<sup></sup></span></td>
    <td></td>
    <td></td>
    <td>Uniformly partitioned with a fast hash f()</td>
  </tr>
</table>


### Insertion

* For each element from [i, n-1): `insert(x)`
* `insert` iterates backwards over the [0, i] until it finds an element that is less than x


### Selection Sort

* Iteratively pick the i<sup>th</sup> smallest element to go into slot i


### Heap Sort

Effectively builds a max-heap, and pops an element off to the tail

* Build a max-heap
  * Iterate from midpoint to 0, percolate down
* Iterate backwards (n, 1]:
  * Swap max to the back
  * Hapify the remains

### Merge Sort

* Recursively mergeSort left, then mergeSort right, then merge
* `merge` - while both cursors are less than end:
  * Iterate cursor if element is copied into tmpArray
  * When done, copy rest of the remaining arrays into tmpArray

* Not typically used because:
  * Linear extra memory
  * Additional work spent copying array back and forth



### Quick Sort

* Partition around a pivot, then recursively sort the left and right subarrays
* Picking a pivot: TBD



### Bucket Sort

Reduces processing costs at the expense of extra space. Only valid if:

* Uniform distribution
* Ordered Hash Function


















# Search

<table class="table table-condensed">
  <tr>
    <td></td>
    <td>Best</td>
    <td>Average</td>
    <td>Worst</td>
    <td>Use Case</td>
  </tr>
  <tr>
    <td>Sequential</td>
    <td><span class="btn btn-success btn-xs">1</span></td>
    <td><span class="btn btn-danger btn-xs">n</span></td>
    <td><span class="btn btn-danger btn-xs">n</span></td>
    <td>Small list, or mostly sorted</td>
  </tr>
</table>

### Sequential Search

* Variations:
  * Move to front on success
  * Move up on success - if element *i* is hit, swap *i* with *i-1*, bubbling *i* up
  * Move to back on success - *if unlikely to be queried again*





