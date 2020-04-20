@snap[midpoint]

# Thinking About Data Structures

@snapend

---

## Learning Goals

By the end of this module, students will be able to...

- **Define** the terms data structure, interface, implementation, structure, algorithm, analysis
- **Describe** this course's approach to studying data structures
- **Distinguish** between interface, implementation and analysis


---

## What is a Data Structure?

@quote[A data structure is a data organization, management, and storage format that enables efficient access and modification.](Wikipedia)

<br>

System to store and work with data in a computer's memory

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

The first step of implementation is design

---

## Implementation

### Structure

How is the data organized?

<ul>
<li>Classes, members, relations</li>
<li>Does this DS rely on another?</li>
<li>Draw a picture!</li>
</ul>

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

## Studying DS

![](collections/images/tads-study-workflow.png)

In the next few modules we'll dive into each of those concepts deeper

As a running example we'll use a queue

If you don't quite recall how they work don't worry, we'll go through it piece by piece

---

## Summary

Finding the right DS for your problem is key

DS problems are great coding practice

When studying a new DS, we'll focus on **interface**, **implementation** and **analysis**

---

## Vocab

| Term           | Definition                                                        |
| -------------- | ----------------------------------------------------------------- |
| Data structure | System to store and work with data in a computer's memory         |
| Interface      | View of a data structure from the **outside**                     |
| Implementation | How a data structure works on the **inside**                      |
| Structure      | How a DS organizes its data in memory                             |
| Algorithm      | How a DS accesses and modifies its data                           |
| Analysis       | Study of the **resources** (time, space) used by a data structure |

---

## Review Questions

---

## Image Sources

AVL tree: https://en.wikipedia.org/wiki/AVL_tree#/media/File:AVL-tree-wBalance_K.svg

Tree rotation: https://en.wikipedia.org/wiki/Tree_rotation#/media/File:Tree_rotation.png

Complexity graphs: https://en.wikipedia.org/wiki/File:Comparison_computational_complexity.svg
