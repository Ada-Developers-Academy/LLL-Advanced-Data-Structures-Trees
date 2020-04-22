@snap[midpoint]

# Linked-List Queue

### Implementation and Analysis

@snapend

---

## Learning Goals

By the end of this module, students will be able to...

- **Define** the following terms: linked list, node, head, tail, sentinel
- **Describe** the structure of a linked list
- **Describe** the implementation of various linked list operations
- **Discuss** the role of a sentinel node in a linked list
- **Use** a linked list to implement the queue interface

---

## Motivation

Our array-based queue implementation has problems with space complexity

There are ways to address this and keep the array, but none of them are great

What if we use a different internal structure?

---

## Review - Linked Lists

Linear data structure (elements stored in order)

Series of **nodes** allocated on the heap

Each node keeps three references:

<ul class="small">
<li>Its element</li>
<li>The previous node</li>
<li>The next node</li>
</ul>

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

## Insert Tail

1. Create new node, `prev` points to current `tail`
1. Set current `tail`'s `next` to the new node
1. Set `tail` to the new node
1. Return the new node as the cancelation ticket

## TODO Image

Inserting at the head is similar

---

## Iterate

1. Create a variable `node` pointing to the head
1. While `node` is not `undefined`:
    - Visit `node`
    - Update `node` to reference the next node in the list, i.e. `node = node.next`

---

## Remove

Idea: "splice" the node out of the list

1. `node.next.prev = node.prev`
1. `node.prev.next = node.next`
1. Return the node's element

Remove head/tail are special cases

---

## Edge Cases

All of the previous operations have **edge cases** that require different behavior. What are they?

<div class="fragment">
<p>What if the **next or previous node doesn't exist** (i.e. this node is the head or the tail)?</p>
<p>What if the list is **empty**?</p>
</div>

<p class="fragment">This is going to be a lot of work to implement...</p>

---

## Sentinel

Idea: add a dummy node called the **sentinel**

The sentinel comes before the head and after the tail, has no element, and cannot be removed

<p class="small">That means our list is a loop!</p>

---

## Sentinel

Adding the sentinel gives us some new **invariants**:

<ul class="small">
<li>The list always has at least one node (the sentinel)</li>
<li>A node's `.next` and `.prev` references are always valid, either to another "regular" node or to the sentinel</li>
</ul>

That means we can skip logic for an empty list or missing next/prev

**Question:** Does adding a sentinel node increase our time or space complexity?

---

## TODO Sentinel Image

---

## Active Nodes

Each node will track whether or not it's "active"

Nodes start active, and are marked inactive on `remove`

The sentinel is never active

Trying to `remove` an inactive node does nothing

<p class="small">We call a command that is safe to run multiple times **idempotent**</p>

---

## LL Complexity

| Operation                 | Time       | Change in Space  |
| ------------------------- | ---------- | ---------------- |
| Insert (head or tail)     | `O(1)`     | Adds `O(1)`      |
| Insert (random)           | `O(n)`     | Adds `O(1)`      |
| Find node for element     | `O(n)`     | None             |
| **Remove (head or tail)** | **`O(1)`** | **Frees `O(1)`** |
| **Remove by node**        | **`O(1)`** | **Frees `O(1)`** |
| Remove by element         | `O(n)`     | Frees `O(1)`     |
| Iterate                   | `O(n)`     | None             |

---

## LL-Queue

**Question:** How can we build a queue using these operations?

<div class="fragment">

<p>**Enqueue:** insert at tail, return node as ticket</p>
<p>**Dequeue:** remove at head</p>
<p>**Cancel:** remove by node</p>
<p>Should solve our memory leak problem</p>
</div>

---

## Summary

We explored backing our **queue interface** with a **linked-list implementation**

<ul class="small">
<li>We opted for a **doubly-linked list**</li>
<li>Provides similar time complexity to an array implementation</li>
<li>Doesn't leak memory</li>
</ul>

Using a **sentinel node** allows us to simplify our list implementation

---

## Vocab

| Term        | Definition                                                                         |
| ----------- | ---------------------------------------------------------------------------------- |
| Linked list | Linear data structure made from a chain of linked objects                          |
| Node        | One object in our linked list, keeps references to next/prev nodes and its element |
| Head        | First node in the LL                                                               |
| Tail        | Last node in the LL                                                                |
| Sentinel    | Dummy node with no element used to simplify implementation                         |

---

## Review Questions

- What is the ticket in the LL Queue?
