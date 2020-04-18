@snap[midpoint]

# Linked-List Queue

### Implementation and Analysis

@snapend

---

## Learning Goals

By the end of this module, students will be able to...

---

## Motivation

Our array-based queue implementation has problems with space complexity

There are ways to address this and keep the array, but none of them are great

What if we back

---

## Review - Linked Lists

Linear data structure (elements stored in order)

Series of **nodes** allocated on the heap

Each node references one element

Each node keeps a reference to the next node in the list

---

## Linked Lists

## TODO Picture

---

## Single vs Double

Linked lists can be **singly**- or **doubly**-linked

Singly-linked: each node knows about the next node

<p class="small">Uses less space</p>

Doubly linked: each node knows about the next and previous nodes

<p class="small">Makes some operations faster</p>

---

## Complexity

For a **doubly**-linked list

| Operation             | Time   | Change in Space |
| --------------------- | ------ | --------------- |
| Insert (head or tail) | `O(1)` | Adds `O(1)`     |
| Insert (random)       | `O(n)` | Adds `O(1)`     |
| Find node for element | `O(n)` | None            |
| Remove (head or tail) | `O(1)` | Frees `O(1)`    |
| Remove by node        | `O(1)` | Frees `O(1)`    |
| Remove by element     | `O(n)` | Frees `O(1)`    |
| Iterate               | `O(n)` | None            |

@snap[south]
**Question:** How can we build a queue using these operations?
@snapend

---

## LL-Queue

**Enqueue:** insert at tail, return node as ticket

**Dequeue:** remove at head

**Cancel:** remove by node

Should solve our memory leak problem

---

## Summary

---

## Vocab

| Term | Definition |
| ---- | ---------- |


---

## Review Questions

- What is the ticket in the LL Queue?