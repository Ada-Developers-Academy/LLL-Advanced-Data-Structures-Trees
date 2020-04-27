@snap[midpoint]

# Ordered Dictionary

### Interface

@snapend

---

## Learning Goals

By the end of this module, students will be able to...

- **Define** the terms

---

@snap[northwest span-70]

## Problem

Active user list in an instant messenger app like Slack or Discord

<ul class="small">
<li>Update list when a user goes on / offline</li>
<li>Search by name to see user details</li>
<li>Display list of users in alphabetical order</li>
</ul>

<div class="fragment">
<p>List of users may be very long, and update frequently</p>

<p class="small">Think `#general` for a big company</p>
</div>

<p class="fragment">We'll call this interface an **ordered dictionary**</p>
@snapend

@snap[east span-30]
![](binary-trees/images/user-list.png)
@snapend

---

## Interface Questions

Pause the video and answer the following questions about our **ordered dictionary** interface:

- What **type of records** are we storing?
- What **operations** do we need to support?
- What (if any) **ordering** do we maintain?
- What **use pattern** do we expect?

---

## Ordered Dictionary

Records are **key-value pairs**

<ul class="small">
<li>**Key:** username (unique `String`)</li>
<li>**Value:** user data (opaque)</li>
</ul>

Supported operations:

<ul class="small">
<li>**Insert** a key-value pair</li>
<li>**Lookup** by key</li>
<li>**Delete** by key</li>
<li>**Iterate** records in alphabetical key order</li>
</ul>

Operations are **mixed**

---

## Performance

Since operations are mixed, our data structure needs to be pretty good at everything

<div class="fragment">
<p>Insert, lookup and delete should all be **sub-linear** time, constant space</p>

<p class="small">**Sub-linear** means better than linear (grows slower than input)</p>
</div>

<div class="fragment">
<p>DS should use space **linear** in the number of currently stored records</p>
</div>

<div class="fragment">
<p>Iterate should be **linear** time, constant space</p>
</div>

---

## Formal Definition

[Find it here]()

---

## Summary

Today we introduced the **ordered dictionary** interface

<ul class="small">
<li>Records are key-value pairs</li>
<li>Retrieval is by key</li>
<li>Iteration is in key order</li>
</ul>

---

## Vocab

| Term               | Definition                                                                 |
| ------------------ | -------------------------------------------------------------------------- |
| Ordered Dictionary | Interface that supports insert / lookup by key and iterating keys in order |
| Sub-linear         | Better than linear (grows slower than input)                               |

---

## Review Questions
