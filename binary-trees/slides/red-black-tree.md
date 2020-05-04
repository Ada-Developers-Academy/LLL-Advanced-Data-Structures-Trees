@snap[midpoint]

# Red-Black Trees

@snapend

---

## Learning Goals

By the end of this module, students will be able to...

- **Define** the terms

---

## Trigger Warning

Red-black trees are unfortunately named

<ul class="small">
<li>Nodes are red or black, we'll treat them differently based on color</li>
<li>We'll be talking about red parents, black children, etc</li>
</ul>

<p class="small fragment">Invented in 1972 by a German scientist named Rudolf Bayer</p>

---

## Complexity Warning

This is our first really complicated algorithm

<ul class="small">
<li>Big ideas first, then details</li>
<li>Draw a picture</li>
<li>Rewrite the steps (and their purpose) in your own words</li>
<li>Take a break if you need it</li>
</ul>

---

## Red-Black Trees

Goal: guarantee that the height of a BST is `\(O(log(n))\)`

<p class="small">In other words, keep the tree **balanced**</p>

How? **Rebalance** the tree after every `insert` and `delete`

To help us rebalance, we'll **color each node red or black**

We'll define rules about how colors interact

---

## RBT Rules

1. **BST Property** still holds
1. The root is always black
1. "Bogus" nodes count as black
    - Leaves, the root's parent
1. You can't have 2 red nodes in a row
    - 2 black nodes is OK
    - In other words, if a node is red, both its children must be black
1. Number of black nodes is the same for every path from a leaf to the root
    - We'll call this the **black-depth** of a node

<p class="small">After every insert or delete we'll "fix" the tree so it still follows the rules</p>

---

## RBT Rules

1. **BST Property** still holds

Same relationship between balance, height, size and complexity

We can keep the implementations of `lookup` and `forEach`

---

## RBT Rules

<ol start="2">
<li>The root is always black</li>
<li>"Bogus" nodes count as black
<ul><li>Leaves, the root's parent</li></ul>
</li>
</ol>

This is bookkeeping to simplify the implementation

We'll use a **sentinel** node to represent "bogus" nodes

---

## RBT Rules

<ol start="4">
<li>You can't have 2 red nodes in a row
<ul>
<li>2 black nodes is OK</li>
<li>In other words, if a node is red, both its children must be black</li>
</ul>
</li>
<li>Number of black nodes is the same for every path from a leaf to the root
<ul><li>We'll call this the **black-depth** of a node</li></ul>
</li>
</ol>

These are the key to keeping our tree balanced

---

## Example

![](binary-trees/images/rbt-black-depth.png)

Is this a red-black tree?

---

@snap[east span-40]
![](binary-trees/images/rbt-black-depth.png)
@snapend

@snap[northwest span-55]
## Balance

<p class="small">Because you can't have 2 red nodes in a row, the depth of a leaf is never more than twice its black-depth</p>

<p class="small fragment">The black-depth is the same for all leaves, so no leaf is more than twice as deep as any other</p>

<p class="small fragment">This means the tree is balanced, according to our definition</p>

<p class="small fragment">So the height is `\(O(log(n))\)`</p>
@snapend

---

## Rules Review

<ol class="small">
<li>**BST Property** still holds</li>
<li>The root is always black</li>
<li>Leaves, root's parent count as black</li>
<li>You can't have 2 red nodes in a row</li>
<li>Black-depth is the same for every leaf</li>
</ol>

Any tree that obeys these rules is a balanced BST

If we can find a way to make our trees follow these rules, we're set

---

## Insert Fixup

1. Do a **normal BST insert**, coloring the new node red
1. **Fixup the tree** so that it follows the rules

We can assume that the **rules held before we started** (why?)

<p class="fragment">Do the rules hold for a **tree of size one**?</p>

<p class="fragment">This kind of reasoning is called **induction**</p>

---

## Fixup Induction

![](binary-trees/images/rbt-induction.png)

---

## Rotation

There's one more tool we need: **rotation**

![](binary-trees/images/tree_rotation.png)

Idea: swap a node and one of its children, while maintaining the BST property

Code for left- and right-rotate is provided for you!

---

## Summary

---

## Vocab

| Term | Definition |
| ---- | ---------- |

---

## Review Questions
