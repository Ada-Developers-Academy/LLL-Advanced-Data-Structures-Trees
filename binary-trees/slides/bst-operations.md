@snap[midpoint]

# Binary Search Tree

### Implementation and Analysis

@snapend

---

## Learning Goals

By the end of this module, students will be able to...

- **Define** the terms

---

## Classes

One class for nodes, another for the tree

Tree has a reference to the root

Each node has reference to parent, left and right children

Any node reference may be `undefined`

---

@snap[northwest span-45]
## Lookup

Walk down a path, choosing left or right each time

Stop when we find what we're looking for, or find the bottom of the tree

@snapend

@snap[east text-left span-50]
```js
lookup(key) {
  let node = this.root;

  while (node) {
    if (key < node.key) {
      node = node.left;
    } else if (key > node.key) {
      node = node.right;
    } else { // equal
      return node.value;
    }
  }
}
```
@snapend

---

## Lookup Analysis

How long does lookup take to run?

<div class="fragment">
<p>It's doing a binary search, so `O(log(n))` right?</p>

<p class="small">`n` is the number of nodes in the tree</p>
</div>

<p class="fragment">What is the **worst case scenario**?</p>

---

## Lookup Analysis

How many comparisons to find `42`?

![](binary-trees/images/bst-transformed.png)

<p class="fragment">Not great, but not the worst case</p>

---

## Lookup Analysis

How many comparisons to find `42`?

![](binary-trees/images/bst-unbalanced.png)

---

## Height

Lookup is linear in the height of the tree `\(h\)`

`\[
h =
\begin{cases}
O(log(n)) & \quad \text{for a } balanced \text{ tree} \\
O(n)      & \quad \text{for an } unbalanced \text{ tree}
\end{cases}
\]`

---

## Summary

---

## Vocab

| Term | Definition |
| ---- | ---------- |

---

## Review Questions
