@snap[midpoint]

# Binary Search Trees

### Design

@snapend

---

## Learning Goals

By the end of this module, students will be able to...

- **Define** the terms

---

## Is It Easy?

Think about the data structures we've seen so far

<ul class="small">
<li>Array</li>
<li>Linked list</li>
<li>Hash</li>
</ul>

Can we use any of these to solve the problem without inventing something?

If not, what can we learn from them?

---

## Arrays

Could store elements in **insertion order**

<p class="small">Insert is `\(O(1)\)`, but lookup is `\(O(n)\)` and iterate is `\(O(n*log(n))\)`</p>

<br>

<div class="fragment">
<p>Could store elements in **sorted order**</p>

<p class="small">Lookup is `\(O(log(n))\)` via binary search, iterate is `\(O(n)\)`</p>
<p class="small">Insert is `\(O(n)\)` - need to search for the right spot, move following records to make a hole</p>
</div>

---

## Linked Lists

Once we know where to put it, adding a node is `\(O(1)\)`

Lookup by key is always `\(O(n)\)`

Linked lists really only work for stacks and queues

Maybe we can take some of the principles and apply them elsewhere...

---

## Hash

Insert and lookup are constant!

Iterate is `\(O(n*log(n))\)` - need to sort first

Not too useful - we have to make too many tradeoffs to get constant access

---

## Learn from Experience

Records must be **stored in sorted order**

<ul class="small">
<li>Otherwise iterate requires an `\(O(n*log(n))\)` sort</li>
<li>Lets us use **binary search** for `\(O(log(n))\)` lookups</li>
</ul>

<div class="fragment">
<p>Maybe we could **store records in nodes**</p>
<ul class="small">
<li>Similar to a linked list</li>
<li>Insert could be an `\(O(log(n))\)` lookup plus an `\(O(1)\)` node add</li>
<li>Lookup and delete are similarly `\(O(log(n))\)`</li>
</ul>
</div>

<p class="fragment">Plan: a **linked** data structure that supports **binary search**</p>

---

## Search Review

The core idea of binary search is essential to understanding trees, so let's review it before going further

---

## Linear Search

Imagine we have a sorted array of integers, and we want to check whether it contains the value `42`. How do we find out?

**Linear search**: start on the left, look at values one by one until you find your target or run out of array.

![](binary-trees/images/array-linear-search.png)

What is the time complexity of linear search? `\(O(n)\)`

---

## Binary Search

If our array is sorted, we can do better!

![](binary-trees/images/array-binary-search.png)

Binary search is `\(O(log(n))\)`

`\(log_2(n)\)`: how many times can you cut `\(n\)` in half?

---

## Binary Search

We can think of binary search as following a "path" through the data

![](binary-trees/images/array-to-bst.png)

<p class="small">Go right, then left, then right</p>

---

## Binary Search Tree

If we turn each potential "decision point" in the path into a node, we have a **binary search tree**

![](binary-trees/images/bst-transformed.png)

---

![wide](binary-trees/images/TreeVocabulary.png)

---

## BST Notes

A tree (or subtree) is **balanced** if it has the same number of descendants on its left as on its right

<p class="small">As we'll see, balance is key for performance</p>

<div class="fragment">
<p>Subtrees are important - each subtree is itself a tree</p>

<p class="small">A subtree can have size 1 or even 0</p>

<p class="small">That means **recursion** will be a useful tool</p>
</div>

---

## BST Property

For every node...

All nodes in the node's left child's subtree have a key less than that node's key

All nodes in the right subtree have a greater key

---

## BST Visualizer

https://www.cs.usfca.edu/~galles/visualization/BST.html

---

## Summary

---

## Vocab

| Term | Definition |
| ---- | ---------- |


---

## Review Questions
