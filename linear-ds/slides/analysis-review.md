@snap[midpoint]

# Analysis

### Review

@snapend

---

## Learning Goals

By the end of this module, students will be able to...

- **Define** the terms analysis, complexity, order, worst case
- **Explain** how Big-O notation helps us compare algorithms
- **Recognize** the graph shapes of common complexity orders
- **Recall** the time complexity of various built-in operations
- **Describe** how to compose operations to analyze the complexity of a function

---

## What is Analysis

@quote[The process of breaking a complex topic or substance into smaller parts in order to gain a better understanding of it](Wikipedia)

What are we analyzing?

The resources used by our program

- Processor time
- Memory space

---

## Two Types of Analysis

**Theoretical:** reasoning about the **design** of our DS

<ul class="small">
<li>Drawing pictures</li>
<li>Finding patterns</li>
<li>Math and logic</li>
</ul>

**Practical:** measuring our DS's **implementation**

<ul class="small">
<li>Predictions and experiments</li>
<li>Direct measurements</li>
<li>Profiling tools</li>
</ul>

In this course we will focus on **theoretical analysis**

---

## Environment

Theoretical analysis can be difficult in JavaScript because the language hides details

<ul class="small">
<li>Dynamic arrays</li>
<li>Automatic memory management</li>
<li>The JIT</li>
</ul>

Sometimes JS finds a clever way to get around something that ought to be expensive

Sometimes it does something expensive behind the scenes

---

@snap[northwest span-70]

## Growth Shapes

When we analyze an algorithm, we're interested in growth

- If I double the size of my input, how much longer will it take?
- If I buy a computer with 4 times the memory, how much more data can I process?

@snapend

@snap[east span-30]
![complexity graph](linear-ds/images/tads-complexity-graphs.png)
@snapend

---

@snap[northwest span-70]

## Growth Shapes

We call the rate of growth **complexity**

Every algorithm is different, but we can identify common shapes

@snapend

@snap[east span-30]
![complexity graph](linear-ds/images/tads-complexity-graphs.png)
@snapend

---

## In Terms of What?

Growth is always **in terms of** something

Usually the number of **inputs** or **operations**

We'll use letters (usually `\(n\)`, `\(m\)`, `\(k\)`, etc) to represent these numbers

<ul class="small">
<li>How much space does our queue take to store `\(n\)` records?</li>
<li>If our queue contains `\(n\)` records, how long does it take to do `\(m\)` dequeues?</li>
</ul>

Always ask what `\(n\)` is!

---

## Big-O

The goal is to connect our complex real-world performance to a **simpler mathematical model**

<!-- <p class="small">This will make it easier for us to reason about performance and compare different algorithms</p> -->

<p class="small">We'll call the simpler equation the **order** our algorithm</p>

If our algorithm is `\(O(log(n))\)`, its graph has a **similar shape** to the graph of the equation `\(log(n)\)`

@snap[south span-80]
![](linear-ds/images/analysis-log-n.png)
@snapend

---

## Common Shapes

Let's look at some common growth curves, along with examples

These examples will be the basic units of our analysis

Remember, the important piece is growth. If you double the size of the input, what happens to the time or space required?

The key is that the real graph and the equation graph **grow in the same way**

---

@snap[northwest span-60]

## Constant

A constant operation doesn't grow

<p class="small">This is as good as it gets!</p>

Constant operations:

<ul class="small">
<li>Math and comparisons on individual values</li>
<li>Entering or returning from a function</li>
<li>Hash / array insert and lookup</li>
<li>Appending an element to an array</li>
<li>Allocating a block of memory takes constant time</li>
</ul>

@snapend

@snap[east span-40 text-center]
@math
`\(O(1)\)`
@mathend

![complexity graph](linear-ds/images/tads-complexity-graphs.png)

<p class="small">The purple line is **constant**</p>
@snapend

---

@snap[northwest span-60]

## Logarithmic

A logarithmic operation grows slower when the input is big

Every time the input **doubles**, its log **increases by 1**

Logarithmic operations:

<ul class="small">
<li>Binary search</li>
<li>Many tree operations</li>
</ul>
@snapend

@snap[east span-40 text-center]
@math
`\(O(log(n))\)`
@mathend

![complexity graph](linear-ds/images/tads-complexity-graphs.png)

<p class="small">The blue line is **logarithmic**</p>
@snapend

---

@snap[northwest span-60]

## Linear

A linear operation grows at the **same rate** as its input

Double the input, double the time or space required

Linear operations:

<ul class="small">
<li>Allocating memory takes linear space</li>
<li>Looping through an array takes linear time</li>
<li>Most array operations (slice, splice, filter, map, reduce, etc) are linear</li>
</ul>

@snapend

@snap[east span-40 text-center]
@math
`\(O(n)\)`
@mathend

![complexity graph](linear-ds/images/tads-complexity-graphs.png)

<p class="small">The green line is **linear**</p>
@snapend

---

@snap[northwest span-60]

## Log-linear

A log-linear operation grows **a little faster** than the input

Log-linear time operations:

<ul class="small">
<li>Sort a list of size n</li>
<li>Do a logarithmic operation n times</li>
</ul>

<p class="small">This graph doesn't show it well, but on large inputs log-linear is much closer to linear (green) than to quadratic (red)</p>

@snapend

@snap[east span-40 text-center]
@math
`\(O(n*log(n))\)`
@mathend

![complexity graph](linear-ds/images/tads-complexity-graphs.png)

<p class="small">The orange line is <b>log-linear</b></p>
@snapend

---

@snap[northwest span-60]

## Polynomial

A polynomial operation grows faster when its input is bigger

<p class="small">Bigger exponents grow faster</p>

Polynomial operations:

<ul class="small">
<li>Comparing all the pairs of elements in two lists of size `\(n\)` takes `\(O(n^2)\)` time</li>
<li>Nested loops often take polynomial time</li>
</ul>

<p class="small">`\(O(n^2)\)` is often called **quadratic**</p>

@snapend

@snap[east span-40 text-center]
@math
`\(O(n^2),  O(n^3), ...\)`
@mathend

![complexity graph](linear-ds/images/tads-complexity-graphs.png)

<p class="small">The red line is **polynomial**</p>
@snapend

---

## Orders

| Order             | Name        | Growth                     | Operations        |
| ----------------- | ----------- | -------------------------- | ----------------- |
| `\(O(1)\)`        | Constant    | None!                      | Do one thing      |
| `\(O(log(n))\)`   | Logarithmic | Slower than input          | Binary search     |
| `\(O(n)\)`        | Linear      | Same as input              | Loop over list    |
| `\(O(n*log(n))\)` | Log-linear  | Slightly faster than input | Sort a list       |
| `\(O(n^2)\)`      | Polynomial  | Much faster than input     | Compare two lists |

---

## Worst Case

Unless otherwise stated, assume we're analyzing the performance in the worst case scenario

Establishing an **upper bound** for complexity

Often makes the analysis easier

Often the best we can do without knowledge of the **workflow**

<p class="small">Better to be pleasantly surprised...</p>

---

## Composing Orders

Algorithms are created by chaining together multiple basic operations

- Doing one thing after another (in sequence)
- Doing the same thing many times (iteration)

How can we use this to build up our understanding of complexity?

---

## Sequence

For a sequence of operations (one after the other), we add the complexities together

<p class="small">We do this, then we do that</p>

We **ignore** any coefficients (constant multipliers)

<p class="small">They don't change the shape of the curve, just the angle</p>

`\[ n*log(n) + n + 2n + 1 + 4n^2 \\ \text{turns into} \\ n*log(n) + n + 1 + n^2 \]`

---

## Sequence

The **fastest-growing** operation determines the order

<p class="small">We say it **dominates** the complexity</p>

`\[ n^2 + n*log(n) + n + 1 \\ \text{turns into} \\ O(n^2) \]`

Exception: different inputs (`\(m\)` and `\(n\)`) don't dominate each other

---

## Sequence

@snap[south span-100]
![](linear-ds/images/analysis-sequence.png)

@math
<p>When `\(n\)` is large, all 3 curves look linear</p>
@mathend
@snapend

---

## Sequence

```js zoom-12
// n is the length of the list
const sortedEvens = (list) => {
  list = list.sort();

  return list.filter((el) => el % 2 === 0);
};
```

What is the time complexity?

---

## Sequence

```js zoom-12
// n is the length of the list
const sortedEvens = (list) => {
  // O(n*log(n))
  list = list.sort();

  // O(n)
  return list.filter((el) => el % 2 === 0);
};
```

Adding the pieces together gives `\(n*log(n) + n\)`

Since `\(n*log(n)\)` grows faster it **dominates**

This function is `\(O(n*log(n))\)`

---

## Sequence

What is the time complexity?

```js
const sumEvenLengthsOfEveryTenthWord = (wordList) => {
  return wordList

    .filter((word, i) => i % 10 === 0)

    .map((word) => word.length)

    .filter((length) => length % 2 === 0)

    .reduce((memo, length) => memo + length, 0);
};
```

---

## Sequence

`\[O(n)\]`

```js
const sumEvenLengthsOfEveryTenthWord = (wordList) => {
  return wordList
    // filter n words
    .filter((word, i) => i % 10 === 0);
    // map n/10 words
    .map(word => word.length)
    // filter n/10 words
    .filter(length => length % 2 === 0)
    // assume worst case: all words are even length
    // reduce n/10 words
    .reduce((memo, length) => memo + length, 0);

  // Operations are in sequence, so we sum then drop the coefficient
  // n + n/10 + n/10 + n/10 = 1.3*n => O(n)
};
```

---

## Iteration

If code is nested in a loop, we **multiply** the complexity of the loop body by the length of the loop

<p class="small">We do this, that many times</p>

---

## Iteration

What is the complexity?

```js zoom-12
// n is the length of the list
const countMatches = (list, target) => {
  let count = 0;

  list.forEach((el) => {
    if (el === target) {
      count += 1;
    }
  });

  return count;
};
```

---

## Iteration

`\[O(n)\]`

```js zoom-12
// n is the length of the list
const countMatches = (list, target) => {
  let count = 0;

  // n * order of loop body (O(1))
  // => O(n)
  list.forEach((el) => {
    if (el === target) {
      count += 1;
    }
  });

  return count;
};
```

---

## Iteration

What is the complexity?

```js zoom-12
const allPairs = (list) => {
  const pairs = [];
  list.forEach((left) => {
    list.forEach((right) => {
      pairs.push([left, right]);
    });
  });
};
```

---

## Iteration

`\[O(n^2)\]`

```js zoom-12
const allPairs = (list) => {
  const pairs = [];

  // n times
  list.forEach((left) => {
    // n times
    list.forEach((right) => {
      // constant
      pairs.push([left, right]);
    });
  });
};

// n * n * 1 = n^2
```

---

## Summary

For operations in sequence:

<ul class="small">
<li>Add complexities</li>
<li>Drop coefficients</li>
<li>Find the dominant term</li>
</ul>

For operations in a loop:

<ul class="small">
<li>Figure out complexity of the loop body</li>
<li>Multiply by the number of iterations</li>
</ul>

Always assume the worst case

---

## Vocab

| Term       | Definition                                                         |
| ---------- | ------------------------------------------------------------------ |
| Analysis   | Determining how much time or space is used by an algorithm         |
| Complexity | How the resources used by an algorithm grow                        |
| Order      | Simplest equation that has a growth curve similar to our algorithm |
| Worst case | Analyzing the most expensive possibility                           |

---

## Orders

| Order              | Name        | Growth                     | Operations        |
| ------------------ | ----------- | -------------------------- | ----------------- |
| `\(O(1)\)`         | Constant    | None!                      | Do one thing      |
| `\(O(log(n))\)`    | Logarithmic | Slower than input          | Binary search     |
| `\(O(n)\)`         | Linear      | Same as input              | Loop over list    |
| `\(O(n*log(n))\)` | Log-linear  | Slightly faster than input | Sort a list       |
| `\(O(n^2)\)`       | Polynomial  | Much faster than input     | Compare two lists |

---

## Review Questions

---

## Credit

[Analysis definition](https://en.wikipedia.org/wiki/Analysis)

Additional: https://www.youtube.com/watch?v=D6xkbGLQesk
