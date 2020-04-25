# Binary Trees

## Interface

### Motivating Problem

Specific problem: tracking online users in an IM program
- Inserts and deletes whenever someone goes on or offline
- Search for users by name (to send a message)
- Ordered iteration any time someone looks at the room details

General problem: Ordered dictionary

Needs to be pretty good at everything

### Operations

Records are k/v pairs
Keys have a natural ordering
Insert
Lookup
Delete
Iterate

Behavior for duplicate keys?
- For simplicity, we'll say replace

## Binary Search Trees

### Design

Tree definition

Tree + Node classes

Binary search tree property

Visualizer
http://btv.melezinek.cz/binary-search-tree.html

### Implementation

Lookup implementation

Insert implementation

ForEach implementation

### Analysis

Lookup
- Walk down a path, choosing left or right each time
- Stop when we find what we're looking for, or find the bottom of the tree
- Worst case?
- Space - constant

The height of the tree is key! We'll call this h

Insert
- Similar to lookup

Analyzing recursive methods
- Induction!
- Remember the stack for space

ForEach
- At each node visitation, we reduce the remaining work to be done by 1, split what's left in half, then queue up each half
- Space is stack depth is the height of the tree
- Visualization will be key, especially for space

OK, let's talk about height.  What can we say about this?
- Clearly not worse than O(n)
- Worst case is, in fact, O(n), but that's pathological
- What if we build a tree with a random input order?
- Hand-wave the math, expected height is O(log(n))
- But there's still that worst case...

## Red-Black Trees

Trigger warning (black child, black parent)
- Invented by a dude named Rudolf Bayer, thus R-B trees
- Or maybe he's just a bulls fan

### Design

Goal: guarantee that the tree height is always O(log(n))

How? Rebalance the tree after every insert (and delete)

Red nodes and black nodes

Rules:
- Each node is either black or red
- The root is always black
- You can't have 2 red nodes in a row (2 blacks is OK)
- Number of black nodes is the same for every path from a leaf to the root

Add a sentinel node
- Colored black
- Root's parent, all leaves

Nodes we know are black:
- Root
- Root's parent (sentinel)
- All leaves (sentinel)

Question: does this keep the height O(log(n))

Yes!

Intuitive reasoning:
- No path from the root to a leaf is more than twice the length of any other path
- We're forcing the tree to be "pretty balanced"
- Works out to 2log(n+1), which is in fact O(log(n))
- You can do some fancy math to prove it, it's by induction if you want to try it yourself

OK cool, if we can maintain those properties every time we insert, then we'll have a balanced tree, and the height will be O(log(n)), so our inserts and lookups are guaranteed to be fast!

### Implementation

### Analysis

## Lab

- BST Delete
- RBT Insert
