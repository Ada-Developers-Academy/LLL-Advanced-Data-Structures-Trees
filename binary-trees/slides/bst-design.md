@snap[midpoint]

# Binary Search Trees

### Design

@snapend

---

## Learning Goals

By the end of this module, students will be able to...

- **Define** the terms


---

## Is It Easy?

Think about the data structures we've seen so far

<ul class="small">
<li>Array</li>
<li>Linked list</li>
<li>Hash</li>
</ul>

Can we use any of these to solve the problem without inventing something?

If not, what can we learn from them?

---

## Arrays

Could store elements in **insertion order**

<p class="small">Insert is `O(1)`, but lookup is `O(n)` and iterate is `O(n log(n))`</p>

<br>

<div class="fragment">
<p>Could store elements in **sorted order**</p>

<p class="small">Lookup is `O(log(n))` via binary search, iterate is `O(n)`</p>
<p class="small">Insert is `O(n)` - need to search for the right spot, move following records to make a hole</p>
</div>

---

## Linked Lists

Once we know where to put it, adding a node is `O(1)`

Lookup by key is always `O(n)`

Linked lists really only work for stacks and queues

Maybe we can take some of the principles and apply them elsewhere...

---

## Hash

Insert and lookup are constant!

Iterate is `O(n log(n))` - need to sort first

Not too useful - we have to make too many tradeoffs to get constant access

---

## Learn from Experience

Records must be **stored in sorted order**
<ul class="small">
<li>Otherwise iterate requires an `O(n log(n))` sort</li>
<li>Lets us use **binary search** for `O(log(n))` lookups</li>
</ul>

<div class="fragment">
<p>Maybe we could **store records in nodes**</p>
<ul class="small">
<li>Similar to a linked list</li>
<li>Insert could be an `O(log(n))` lookup plus an `O(1)` node add</li>
<li>Lookup and delete are similarly `O(log(n))`</li>
</ul>
</div>

<p class="fragment">Plan: a **linked** data structure that supports **binary search**</p>

---

## Summary

---

## Vocab

| Term | Definition |
| ---- | ---------- |

---

## Review Questions
