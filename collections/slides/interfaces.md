@snap[midpoint]

# Interfaces

@snapend

---

## Learning Goals

By the end of this module, students will be able to...

- **Define** the term interface and related keywords
- **Identify** questions to ask when designing an interface
- **Describe** the interface of a queue
- **Differentiate** between queries and commands

---

## What is an Interface

@quote[A shared boundary across which two or more separate components of a computer system exchange information](Wikipedia)

The methods our data structure exposes to the rest of the program

How you **use** it, not how it **works**

---

## How will we study Interfaces?

Motivating problem

Ask lots of questions to determine requirements

Write down formal definition

<p class="small">Sounds an awful lot like software engineering in general</p>

---

## Motivating Problem

I have some resource that does **tasks**

<ul class="small">
<li>Worker thread</li>
<li>Network card</li>
<li>3D printer</li>
<li>Customer support representative</li>
</ul>

The resource can only do **one task at a time**

Tasks should be done in **first-come-first-served** order

I need a data structure to **keep track of waiting tasks**

We'll call it a **queue** (think of a line of people)

---

@snap[northwest span-70]

## Questions

**What** is being stored?

How will we **interact** with stored data?

What **patterns** will this interaction follow?

Anything else to pay attention to?

<br>

Keep the queue in mind as we proceed, we'll come back to it

@snapend

@snap[east span-40]
@fa[question fa-6x color-fuscia]
@snapend

---

## What is Being Stored?

We'll call whatever is stored a **record**

- Individual elements
- Key-value pairs
- Something else

Are records unique?

Are there relationships between records?

Note: elements and values are **opaque**

---

## Interacting With Stored Data

- Count records
- Retrieve one record at a time
- Remove records
- Iterate through all records

---

## Retrieval and Removal

- Get the "next" element
- Lookup by key or index
- Search for the element
- "Fuzzy" search (partial matches, similarity, etc)

Note: remove usually returns the removed element

---

## Iterating Through Records

- Insertion order
- "Natural" order (like alphabetic or numeric)
- User-defined ordering (custom sort function)
- If unordered, does it need to be consistent?
- Can you modify elements as you iterate?

Note: in this course, iteration means implementing `forEach`

---

## Use Patterns

- Are records added in a batch or over time?
- Are records ever removed?
- Are reads and writes mixed together?
- Do reads or writes dominate the workflow?
- Any particular performance requirements?

---

## Other Requirements

- Immutable
- Observable (notify on change)
- Serializable to disk or network
- Fits in a relational database
- Thread-safe
- Distributed

Generally beyond the scope of this course

---

## The Queue

Pause the video and answer the following questions about our queue data structure:

- What **type of records** are we storing?
- What **operations** do we need to support?
- What (if any) **ordering** do we maintain?
- What **use pattern** do we expect?

---

## The Queue

Records are **individual elements**

Supported operations:

- **Enqueue** (insert at the back)
- **Dequeue** (remove from the front)
- **Count** records
- Possibly **iterate**

**Insertion order matters**, for both dequeue and iterate

<p class="small">First-in first-out</p>

Inserts and removes will be **mixed**

---

## Formal Definition

Our last step is to write down a formal definition of the data structure

Design documents, docstrings, method stubs, etc.

In this class we'll use a combination of docstrings (with JSDoc) and method stubs

---

## Queries and Commands

Every operation is either a query or a command

**Queries** retrieve information without changing the DS

**Commands** modify the DS

<p class="small">Labeling operations as queries and commands is useful!</p>

**Question:** Which of our queue operations are queries and which are commands?

---

## Performance

Performance guarantees can be part of an interface

In future weeks we'll often start with a performance requirement as part of our motivating problem

This week we'll hold off until after we've talked about analysis

---

## Queue Formal Definition

[Find it here]()

---

## Interfaces Aren't Real

In the same way that art and money aren't real

JavaScript is **dynamically typed**, so unlike Java or Go there is nothing called an "interface" in the language

Put your faith in duck typing!

<br>

<p class="small">Added bonus: we can store any type of object without having to mess with generics</p>

---

## Summary

An interface defines what can be done with our data structure

Steps for defining an interface:

- Start with a problem to solve
- Ask a bunch of questions
- Come up with an English description
- Write down a formal definition

---

## Vocab 1

| Term      | Definition                                                               |
| --------- | ------------------------------------------------------------------------ |
| Interface | The methods exposed by our data structure                                |
| Record    | Something stored by our DS, usually an opaque object or a key-value pair |
| Operation | Something our DS can do, like insert or iterate                          |
| Query     | An operation that retrieves data without modifying the DS                |
| Command   | Any operation that modifies the DS                                       |

---

## Vocab 2

| Term     | Definition                                                |
| -------- | --------------------------------------------------------- |
| Ordering | When we iterate records, how do we know which comes next? |
| Queue    | List of elements in first-in, first-out order             |
| Enqueue  | Add an element to the back of a queue                     |
| Dequeue  | Remove an element from the front of a queue               |

---

## Review Questions

---

## Credits
