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

**Question:** What does this code return if the target key isn't found?
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

How long does `lookup` take to run?

<div class="fragment">
<p>It's doing a binary search, so `\(O(log(n))\)` right?</p>

<p class="small">`\(n\)` is the number of nodes in the tree</p>
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

<p class="fragment">That tree looks suspiciously like a linked list...</p>

---

## Tree Vocab

We need some new vocab to help us better analyze trees

We'll define these terms:

- Depth
- Leaf
- Balance
- Height

---

## Depth

The **depth of a node** is the number of nodes on the path between it and the root

<p class="small">Root has depth 1, its children have depth 2, etc</p>

<!-- https://app.diagrams.net/#G1gxLQ7oC6m75MGNlBnWGQIxEGRDvP9zab -->

@snap[south span-100]
![](binary-trees/images/bst-depth.png)
@snapend

---

## Leaf

A **leaf** is an **empty link** in a tree

![](binary-trees/images/bst-balanced-with-leaves.png)

<p class="small">The red circles with X's are leaves. What is their depth?</p>

---

## Balance

A tree is **perfectly balanced** if all **leaves** have the **same depth**

A tree is **unbalanced** if there's a **big difference** in the depth of its leaves

A tree is **mostly balanced** if leaf depths are **similar**

<p class="small">Within a small constant factor, e.g. no leaf is more than twice as deep as any other</p>

<p class="fragment">Most of the time, mostly balanced is good enough. When I say "balanced", I usually mean "mostly balanced".</p>

---

## Is it Balanced?

![](binary-trees/images/bst-balanced-uncolored.png)

---

## Is it Balanced?

![](binary-trees/images/bst-balanced-with-leaves.png)

Yes - perfectly balanced

---

## Is it Balanced?

![](binary-trees/images/bst-unbalanced-uncolored.png)

---

## Is it Balanced?

![](binary-trees/images/bst-unbalanced-with-leaves.png)

No

---

## Is it Balanced?

![](binary-trees/images/bst-mostly-balanced.png)

---

## Is it Balanced?

![](binary-trees/images/bst-mostly-balanced-with-leaves.png)

<p class="fragment">**Mostly balanced** - no leaf is more than twice as deep as any other</p>

---

## Height

The height `\(h\)` of the tree is the maximum depth of any (non-empty) node
<br>
<br>

<div class="fragment">
`\[
h = 
\begin{cases}
  O(log(n)) & \quad \text{for a balanced tree} \\
  O(n) & \quad \text{for an unbalanced tree}
\end{cases}
\]`
<br>

<p class="small">Intuitively, in a balanced tree most nodes split the search space, while in an unbalanced tree most nodes do not</p>


<!-- <p class="small">The formal proof relies on induction on the height of a node's subtree</p> -->
</div>

---

## Height and Lookup

Worst case scenario for lookup: go all the way down to the deepest node

Lookup is `\(O(h)\)`

<ul class="small">
<li>For a balanced tree lookup is `\(O(log(n))\)`</li>
<li>For an unbalanced tree lookup is `\(O(n)\)`</li>
</ul>

---

## Insert

Very similar to `lookup`, still `\(O(h)\)` time

If you find the target, replace its value

If you come to a leaf, add a new node in its place with the new key-value pair

Remember the [BST Visualizer](https://www.cs.usfca.edu/~galles/visualization/BST.html)

---

## Expected Height

If you build a tree by inserting records in a random order, the **expected** height of the tree is `\(O(log(n))\)`

<p class="small">**Expected:** average across all possible input orderings</p>

Intuitive idea: for a given set of keys, there are many more balanced trees than unbalanced trees

<p class="small">The [formal proof](https://cs.stackexchange.com/questions/6342/proof-that-a-randomly-built-binary-search-tree-has-logarithmic-height) requires some statistics that are beyond the scope of this course</p>

---

## Pathological

**Pathological:** intentionally constructed to be as hard for our algorithm as possible

What is a pathological insertion order for our BST?

<p class="small">Can you force the tree to be unbalanced? [Try it in the visualizer](https://www.cs.usfca.edu/~galles/visualization/BST.html)!</p>
<br>

<div class="fragment">
<p>Sorted input results in an unbalanced tree</p>
<p class="small">Unfortunately sorted input is fairly common in the real world</p>
</div>

---

## Delete

`delete` is left as an exercise to the reader!

<p class="small">The form is similar to `lookup` and `insert`, but you need to do some extra work to patch things up. Feel free to [look up a description of how it works](https://www.geeksforgeeks.org/binary-search-tree-set-2-delete/).</p>

Run time is still `\(O(log(n))\)`

**Question:** Why didn't we have to do extra work for `insert`?

<p class="fragment small">With `delete` we need to worry about children. `insert` always adds a node to the bottom of the tree, so children aren't a concern.</p>

---

## Space Workflows

`insert` allocates one node (constant space)

Inserting `\(n\)` records allocates `\(O(n)\)` space

`delete` frees the node, so `\(n\)` `insert`s and `\(n\)` `delete`s takes constant space

---

## Iterate

Remember the BST property

<p class="small">All nodes on the left come before, all nodes on the right come after</p>

<p class="small">A node plus all its descendants are a **subtree**</p>

Idea: recursive function to visit a subtree

<ol>
<li>Visit the left subtree</li>
<li>Do the thing to this node</li>
<li>Visit the right subtree</li>
<li>(Return to the parent)</li>
</ol>

---

## Iterate

```js
forEach(callback) {
  const visitSubtree = (node, callback) => {
    if (node) {
      visitSubtree(node.left, callback);
      callback(node.key, node.value);
      visitSubtree(node.right, callback);
    }
  }
  visitSubtree(this.root, callback)
}
```

**Question:** How does this algorithm know when to stop?

---

## Iterate Time

What is the time complexity of `iterate`?

<div class="fragment">
<p>It visits every node once, so `\(O(n)\)`</p>
</div>

---

## Iterate Space

What is the space complexity of `iterate`?

<p class="small">Hint: remember the **program stack**</p>

<div class="fragment">
<ul class="small">
<li>Every time we make a recursive call we add a stack frame</li>
<li>Every time we return we remove a stack frame</li>
</ul>
<p>What is the maximum stack depth?</p>
</div>

<p class="fragment">The height of the tree!</p>

---

## BST Complexity

| Operation                             | Time         | Space      |
| ------------------------------------- | ------------ | ---------- |
| `lookup`                              | `\(O(h)\)`   | `\(O(1)\)` |
| `insert`                              | `\(O(h)\)`   | `\(O(1)\)` |
| `delete`                              | `\(O(h)\)`   | `\(O(1)\)` |
| `forEach`                             | `\(O(n)\)`   | `\(O(h)\)` |
| `\(n\)` `inserts`                     | `\(O(n*h)\)` | `\(O(n)\)` |
| `\(n\)` `inserts` + `\(n\)` `deletes` | `\(O(n*h)\)` | `\(O(1)\)` |

@snap[south span-100]
@math
`\[
  h = 
  \begin{cases}
    O(log(n)) & \quad \text{for a balanced tree} \\
    O(n) & \quad \text{for an unbalanced tree}
  \end{cases}
\]`
@mathend
@snapend

---

## Summary

The height `\(h\)` of a tree is the longest distance from the root to a leaf

The complexity of most BST operations depends on the height of the tree

<ul class="small">
<li>Single-record operations (`lookup`, `insert`, `delete`) take `\(O(h)\)` time</li>
<li>Iteration takes `\(O(h)\)` space due to the stack</li>
</ul>

The height is usually `\(O(log(n))\)`, but can be as bad as `\(O(n)\)`

<p class="small fragment">In the next section we'll discuss a technique for keeping a BST balanced</p>

---

## Vocab

| Term | Definition |
| ---- | ---------- |

Height
Balanced
Expected
Pathological

---

## Review Questions
