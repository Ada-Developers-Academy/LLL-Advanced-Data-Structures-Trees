# Collections Discussion Questions

Please read through these before class, and come prepared to have a meaningful discussion with your peers

For each question we'll discuss in small groups, then as a big group

## General

- What questions or comments do you have after watching the video lectures?
- What about JavaScript makes analysis difficult? What can we do to deal with this?
- The video mentions that array insert is amortized `O(1)`, even though allocating a new buffer and copying existing elements is `O(n)`. How does this work?
- Work with your group to design an array-based queue that doesn't leak memory. How does it work? What constraints does it have?

## Stacks

A stack similar to a queue in many ways. You can insert and remove elements, and elements are stored and removed relative to the order they were inserted.

The big difference is a stack removes elements in the opposite order of a queue. With a queue you always get the oldest element, but with a stack you get the youngest.

### Queue

![](images/discussion-queue.png)

### Stack

![](images/discussion-stack.png)

### Stack Facts

- Stacks are linear (elements are stored in order)
- Insert is called `push`
- Remove is called `pop`
- `pop` removes elements in first-in last-out order (youngest first)

### Questions

- How would you implement a stack with a linked list?
    - What are the time and space complexities of `push` and `pop`?
    - Do you still need a doubly-linked list?
- How would you implement a stack with an array?
    - What are the time and space complexities of `push` and `pop`?
    - Does an array-based stack leak memory like an array-based queue?

## Extra

These questions aren't very practical, but they are interesting! Borrowed from _Introduction to Algorithms_ by Cormen et al.

- Explain how to implement a queue using two stacks. Analyze the time complexity of enqueue and dequeue.
- Explain how to implement a stack using two queues. Analyze the time complexity of push and pop.