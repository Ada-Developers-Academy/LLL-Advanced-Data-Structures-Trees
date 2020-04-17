@snap[midpoint]

# ArrayQueue Ananlysis

@snapend

---

## Learning Goals

By the end of this module, students will be able to...

- **Describe** the time and space complexity of each operation on our ArrayQueue
- **Analyze** the complexity of workflows
- **Explain** the reasoning behind an amortized complexity

---

## Constructor

```js zoom-12
constructor() {
  this.storage = [];
  this.head = 0;
  this.tail = 0;
  this.cancelCount = 0;
}
```

What are the time and space complexities?

<div class="fragment">
<p>Constant time, constant space!</p>
<p>This is typical of constructors</p>
</div>

---

## Enqueue

```js zoom-12
enqueue(element) {
  const ticket = this.tail;
  this.storage[this.tail] = element;
  this.tail += 1;
  return ticket;
}
```

<div class="fragment">
<p>Constant time, constant space</p>
<p class="small">Remember, array insert is amortized `O(1)`</p>
</div>

---

## Enqueue Workflow

It's often useful to analyze **workflows** in addition to individual operations

What are the time and space complexities of...

Enqueueing `n` elements?

<p class="small">No dequeues or cancels yet</p>

<div class="fragment">
<p>`O(n)` time, `O(n)` space</p>
<p>This is what we would expect</p>
</div>

---

## Cancel

```js zoom-12
cancel(ticket) {
  if (this.storage[ticket] !== undefined) {
    this.storage[ticket] = undefined;
    this.cancelCount += 1;
  }
}
```

<div class="fragment">
<p>Constant time, constant space!</p>
<p>Note that cancel does not free any memory</p>
<p class="small">This may cause problems later</p>
</div>

---

## Cancel Workflow

What are the time and space complexities of...

Enqueueing and then cancelling n elements?

<div class="fragment">
<p>`O(n)` time (as expected)</p>
<p>`O(n)` space (not so good)</p>
<p class="small">The number of elements in the queue is `0`, but we use `n` space!</p>
</div>

## TODO Picture

---

## Terminology

| Term | Meaning                                                            |
| ---- | ------------------------------------------------------------------ |
| `n`  | Number of elements **currently** in the queue                      |
| `c`  | Number of elements that have been **cancelled**                    |
| `d`  | Number of elements that have been **dequeued**                     |
| `h`  | Total number of elements we've **ever** enqueued (`h` for history) |

@snap[south-west span-100]
Invariant: `n + c + d = h`

<p class="small">An **invariant** is something that's always true about your code</p>
@snapend

---

## Cancel Workflow

What are the time and space complexities of...

Enqueueing and then cancelling c elements?

<p>`O(c)` time (as expected)</p>
<p>`O(c)` space (not so good)</p>
<p class="small">`n = 0, c = h`</p>

---

## Dequeue

```js zoom-10
dequeue() {
  // skip cancelled elements at the front of the queue
  while (this.head < this.tail &&
      this.storage[this.head] === undefined) {
    this.head += 1;
    this.cancelCount -= 1;
  }

  if (this.head === this.tail) {
    return undefined;
  }

  const element = this.storage[this.head];
  this.storage[this.head] = undefined;
  this.head += 1;
  return element;
}
```

---

## Dequeue - Space

Constant space, but doesn't free memory

Same problem as cancellation

A workflow of `d` enqueues and dequeues uses `d` memory to store `0` objects

## TODO picture

---

## Dequeue - Time

All `O(1)` except for the while loop

```js zoom-12
// skip cancelled elements at the front of the queue
while (this.head < this.tail && this.storage[this.head] === undefined) {
  this.head += 1;
  this.cancelCount -= 1;
}
```

Depends on our workflow - what is the **worst case**?

<div class="fragment">
<p>`c` cancelled elements at the head of the queue</p>
<p>Dequeue is `O(c)`</p>
</div>

<p class="small fragment">It's not quite as bad as it sounds</p>

---

## Dequeue Workflow

Enqueue `h`, then cancel or dequeue everything

`\[n = 0,\quad h = c + d\]`

What is the **average** time complexity of a dequeue?

<div class="fragment">
<p>Each dequeue "gets rid of" some number of cancels</p>
</div>

<div class="fragment">
`\[
\frac{c}{d} \quad \text{cancels per dequeue} \\
O\left(\frac{c}{d}\right) \quad \text{amortized dequeue cost} 
\]`
</div>

## TODO picture

---

## Dequeue Workflow

**Amortized** dequeue is `\[O\left(\frac{c}{d}\right)\]`

What if workflow is 80% dequeue, 20% cancel?

<div class="fragment">
`\[
c=0.2h, \quad d=0.8h \\
\frac{c}{d} = \frac{0.2h}{0.8h} = \frac{0.2}{0.8} = 0.25 \\
O\left(\frac{c}{d}\right) = O(0.25) = O(1)
\]`
</div>

---

## Dequeue Workflow

What if workflow is 99.8% cancel, 0.2% dequeue?

<div class="fragment">
`\[
c=0.998h, \quad d=0.002h \\
\frac{c}{d} = \frac{0.998h}{0.002h} = \frac{0.998}{0.002} = 499 \\
O\left(\frac{c}{d}\right) = O(499) = O(1)
\]`
</div>
<br>
<p class="fragment">As long as dequeues are a consistent percentage of the workflow, **amortized dequeue is constant**</p>

---

## Dequeue Complexity

| Resource | Type       | Complexity | Note                        |
| -------- | ---------- | ---------- | --------------------------- |
| Space    | Always     | `O(1)`     | Doesn't free space          |
| Time     | Worst-case | `O(c)`     |                             |
| Time     | Amortized  | `O(1)`     | Assumes consistent workflow |

---

## Count

```js zoom-12
count() {
  return this.tail - this.head - this.cancelCount;
}
```

Constant! No gotchas.

---

## ForEach

```js zoom-10
forEach(callback) {
  let skipCount = 0;
  for (let i = this.head; i < this.tail; i += 1) {
    if (this.storage[i] === undefined) {
      skipCount += 1;
      continue;
    }
    const index = i - this.head - skipCount;
    callback(this.storage[i], index, this);
  }
}
```

<div class="fragment">
<p>Similar to dequeue, we skip cancelled elements</p>
`\[O(n + c)\]`
</div>

---

## Summary - Time

Time complexities are good!

**Constant** enqueue, cancel

**Linear** forEach

Dequeue is **worst-case linear**, but **amortized constant**

About what you'd expect

---

## Summary - Space

Space complexity for individual operations is OK

Space complexity for **workflows** is **worse** than expected

**Linear** in the **total** number of records ever enqueued

<p class="small">We would expect linear in the number of records **currently** in the queue</p>

Dequeue and cancel don't free memory!

---

## Review Questions
