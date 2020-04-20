@snap[midpoint]

# Design and Implementation

### Array Queues

@snapend

---

## Learning Goals

By the end of this module, students will be able to...

---

## What is Implementation

@quote[The process of moving an idea from concept to reality](wictionary)

Writing the code to make our data structure work



---

## System Capabilities

---

## JavaScript Capabilities

Pause the video and spend a few minutes to list out all the things that JavaScript can do

Think about data types, built in functions, syntax sugar, etc.

Anything that could maybe be useful for our implementation

---

@snap[north-west span-50]
### Data Types

Primitives

Arrays

Objects (hashes)

ES6 Classes
@snapend

@snap[north-east span-50]
### Language Features

Stack and heap

Dynamic types

Higher-order functions

Event loop, async / await, promises

Garbage collector, JIT compiler
@snapend

---

## Arrays

Dynamic resizing - grow automatically (typically double at powers of two), never shrink

Insert is still **amortized** O(1)

<p class="small">Amortized: "this is always the average, but it's possible the worst case will be really bad"</p>

Heterogenous - can contain multiple types

Not guaranteed to be contiguous

---

## An Omission

Turns out JavaScript Arrays already implement the queue interface

<p class="small">That makes this problem not very interesting</p>

For this module only, pretend that `Array.push`, `Array.pop`, `Array.shift`, `Array.unshift`, and `Array.forEach` don't exist

<p class="small">I promise this is the only time we'll "turn off" language features like this</p>

---

## The Hard Part

We know what our language can do

We know what our DS needs to do

Now we need a plan for how our DS will use the language to do what it needs to do

---

## Brainstorming

Pause the video and brainstorm how we might implement our queue DS

<ul class="small">
<li>**Enqueue** (insert at the back)</li>
<li>**Dequeue** (remove from the front)</li>
<li>**Cancel** (remove specific record)</li>
<li>**Count** records</li>
<li>Possibly **iterate**</li>
</ul>

Hint: Arrays are used to store ordered lists, and a queue is kind of like a list...

---

## Array Queue

Store queued elements in an array in insertion order

Enqueue at the end of the array (big indices)

Dequeue from the front of the array (small indices)

Canceled elements are set to `undefined`

---

## TODO: AQ visualization

---

## Array Queue Code

[Check it out on GitHub]()

## TODO Link

Comprehension questions on the code?

---

## Problem

Array insertion 


---

Planning

Need to go back and forth between impl and anls

Why study linked lists?
- Fast insert/remove
- Good intro to other DS that involve links (tree, graph)
- Can be included in other DS (LRU, some tree impls (DOM?))





---

## Summary

---

## Vocab

| Term | Definition |
| ---| ---------- |

---

## Review Questions


---

## Planning for Discussion Questions

- Ring buffer
- Dynamic array insertion is O(1)

---

## Credits

[Implementation definition](https://en.wiktionary.org/wiki/implementation)
