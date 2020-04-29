@snap[midpoint]

# Implementation

### Array Queues

@snapend

---

## Learning Goals

By the end of this module, students will be able to...

- **Define** the terms implementation, design, amortized
- **List** the important capabilities of JavaScript
- **Explain** how we'll use an array to implement the queue interface

---

## What is Implementation

@quote[The process of moving an idea from concept to reality](Wictionary)

Writing the code to make our data structure work

---

## JavaScript Capabilities

Pause the video and spend a few minutes to list out all the things that JavaScript can do

Think about data types, built in functions, syntax sugar, etc.

Anything that could maybe be useful for our implementation

---

@snap[north-west span-50]

### Data Types

Primitives (boolean, number, string)

Dynamic arrays

Objects (hashes)

ES6 Classes
@snapend

@snap[north-east span-50 text-left]

### Features

Stack and heap

Dynamic types

Exception handling

Higher-order functions

Event loop, async / await, promises

Garbage collector, JIT compiler
@snapend

---

## Arrays

Dynamic resizing - grows automatically (typically doubles at powers of two), never shrinks

Append is **amortized** `\(O(1)\)`

<p class="small">Amortized: "this is the average, but it's possible the worst case will be really bad"</p>

Heterogenous - can contain multiple types

Not guaranteed to be contiguous

---

## Whoops

Turns out JavaScript Arrays already implement the queue interface

<p class="small">That makes this problem not very interesting!</p>

For this module only, pretend that `Array.push`, `Array.pop`, `Array.shift`, `Array.unshift`, and `Array.forEach` don't exist

<p class="small">This is the only time we'll "turn off" language features like this</p>

---

## Design

We know what our language can do

We know what our DS needs to do

Now we need a plan for how our DS will use the language to do what it needs to do

---

## Brainstorming

Pause the video and brainstorm how we might design our queue DS

Think about **structure** and **algorithms**

<ul class="small">
<li>**Enqueue** (insert at the back)</li>
<li>**Dequeue** (remove from the front)</li>
<li>**Cancel** (remove specific record)</li>
<li>**Count** records, **iterate**</li>
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

## Summary

Implementation is the process of writing code to fit an interface

The first step of implementation is **design**

Implementation can be split into **structure** and **algorithms**

To start, we will implement our queue using an array

---

## Vocab

| Term           | Definition                                                                                             |
| -------------- | ------------------------------------------------------------------------------------------------------ |
| Implementation | Writing code to make our data structure work                                                           |
| Design         | Figuring out how the implementation will work                                                          |
| Amortized      | Averaged over a large number of operations, implies that the worst case is much worse than the average |

---

## Review Questions

---

## Planning for Discussion Questions

- Ring buffer
- Dynamic array insertion is O(1)

---

## Credits

[Implementation definition](https://en.wiktionary.org/wiki/implementation)
