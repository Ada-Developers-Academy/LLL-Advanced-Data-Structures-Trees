@snap[midpoint]
# Interfaces
@snapend

---

## Learning Goals

---

## What is an Interface

---

## How will we study Interfaces?

Motivating problem

Ask lots of questions to determine requirements

Write down formal definition

<p class="small">Sounds an awful lot like software engineering in general</p>

---

## Interfaces Aren't Real

In the same way that art and money aren't real

JavaScript is **dynamically typed**, so unlike Java or Go there is nothing called an "interface" in the language

Put your faith in duck typing!

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

<br>

I need a data structure to **keep track of waiting tasks**

---

@snap[northwest span-70]
## Questions

**What** is being stored?

How will we **interact** with stored data?

What **patterns** will this interaction follow?

Anything else to pay attention to?

<br>

As we proceed, keep the queue in mind (we'll come back to it)

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

---

## Interacting With Stored Data

- Retrieve one record at a time
- Remove records
- Iterate through all records

---

## Retrieval and Removal

- Lookup by key or index
- Search for the element
- "Fuzzy" search (partial matches, similarity, etc)

---

## Iterating Through Records

- Insertion order
- "Natural" order (like alphabetic or numeric)
- User-defined ordering (custom sort function)
- If unordered, does it need to be consistent?
- Can you modify elements as you iterate?

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
- Serializable to disk (database or flat file) or network
- Thread-safe
- Distributed

Generally beyond the scope of this course

---


## Summary

---

## Vocab

---

## Review Questions

---

## Credits