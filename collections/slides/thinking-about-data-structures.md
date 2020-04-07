@snap[midpoint]
# Thinking About Data Structures
@snapend

---

## Learning Goals

---

## What is a Data Structure?

---

## Why Study DS?

Data structures are the bones of our program

Choosing a DS that matches the problem will make it **easy** to write clean, efficient code

You may need to customize a DS to your specific problem

---

## Why Study DS?

Opportunity to practice...

- Tricky implementations
- Analysis
- Design (OO and otherwise)

Data Structures problems tend to be **well-defined** and **isolated**, which makes them great practice problems

They're also common **interview questions**

---

## How Do You Study DS?

Three key categories of knowledge:

<ul class="small">
<li>**Interface**: what does it do?</li>
<li>**Implementation**: how does it work?</li>
<li>**Analysis**: how much does it cost?</li>
</ul>

Take them one at a time

Start with a motivating problem

Comparisons to other data structures are key

---

@snap[north-west text-left span-47]

## Interface

### What does it do?

- Methods, arguments, return values
- Conditions and assumptions
- Guarantees

What sorts of problems can you solve with it?

@snapend

@snap[east text-left span-47]

```js zoom-12
const stack = new Stack();

stack.push(1);
stack.push(2);
stack.push(3);

const first = stack.pop();
```

@snapend

---

## Implementation

### How does it work?

- Structure

- Algorithms

---

## Implementation

### Structure

How is the data organized?

- Classes, members, relations

- Does this DS rely on another?

- Draw a picture!

@snap[east span-40]
![avl tree](collections/images/tads-avl-tree.png)
@snapend

---

## Implementation

### Algorithms

How do the methods work?

- Edge cases

- Testing

- Draw a picture!

@snap[east span-45]
![tree rotation](collections/images/tads-tree-rotation.png)
@snapend

---

@snap[north-west text-left span-70]

## Analysis

### How much does it cost?

Time and space complexity

Interested in **growth**:

- If I double the size of my input, how much longer will it take?

- If I buy a computer with 4 times the memory, how much more data can I process?

@snapend

@snap[east span-30]
![complexity graph](collections/images/tads-complexity-graphs.png)
@snapend

---

## Example: Queues

In the next few modules we'll dive into each of those concepts deeper

<br>

As a running example we'll use a queue

<br>

If you don't quite recall how they work don't worry, we'll go through it piece by piece

---

## Summary

Finding the right DS for your problem is key

<br>

DS problems are great coding practice

<br>

When studying a new DS, we'll focus on **interface**, **implementation** and **analysis**

---

## Vocab

---

## Review Questions

---

## Image Sources

AVL tree: https://en.wikipedia.org/wiki/AVL_tree#/media/File:AVL-tree-wBalance_K.svg

Tree rotation: https://en.wikipedia.org/wiki/Tree_rotation#/media/File:Tree_rotation.png

Complexity graphs: https://en.wikipedia.org/wiki/File:Comparison_computational_complexity.svg