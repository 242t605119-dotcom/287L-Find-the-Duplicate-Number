# LeetCode 287 - Find the Duplicate Number

## Problem Statement

Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]`.

There is exactly one repeated number, but it may be repeated more than once.

Return the duplicate number.

The solution should not modify the array and should use only constant extra space.

---

## Example

### Input

```text
nums = [1, 3, 4, 2, 2]
```

### Output

```text
2
```

### Explanation

The number `2` appears more than once, so the duplicate number is `2`.

---

## Approach

We use **Floyd's Cycle Detection Algorithm**, also called the **Tortoise and Hare algorithm**.

We treat the array like a linked list.

For every index:

```text
index → nums[index]
```

Because one number is duplicated, this structure must contain a cycle.

We use two pointers:

* `slow` moves one step at a time.
* `fast` moves two steps at a time.

When they meet, a cycle exists.

Then we reset `slow` to the beginning and move both pointers one step at a time.

The point where they meet again is the duplicate number.

---

## Algorithm

### Phase 1: Detect the Cycle

1. Initialize `slow` and `fast` to the first element.
2. Move:

   * `slow` one step.
   * `fast` two steps.
3. Continue until `slow == fast`.

### Phase 2: Find the Duplicate

1. Reset `slow` to `nums[0]`.
2. Move both `slow` and `fast` one step at a time.
3. When they meet, return that value.

---

## Example Walkthrough

Given:

```text
nums = [1, 3, 4, 2, 2]
```

The movement can be viewed as:

```text
0 → 1 → 3 → 2 → 4 → 2 → ...
```

The value `2` creates a cycle:

```text
2 → 4 → 2
```

Using Floyd's algorithm, the two pointers eventually meet inside this cycle.

After resetting the slow pointer and moving both pointers one step at a time, they meet at:

```text
2
```

Therefore:

```text
Answer = 2
```

---

## Why This Works

Because there are `n + 1` numbers but only `n` possible values (`1` to `n`), at least one value must be repeated.

The repeated value creates a cycle when the array is treated as a linked-list structure.

Floyd's cycle detection algorithm allows us to find the entrance of that cycle.

That entrance represents the duplicate number.

---

## Time Complexity

The array is traversed a constant number of times.

**Time Complexity:** `O(n)`

---

## Space Complexity

Only two pointers are used.

**Space Complexity:** `O(1)`

---

## Key Concept

The main concepts used are:

* Floyd's Cycle Detection
* Two Pointers
* Tortoise and Hare Algorithm
* Array as Linked List

---

## Language

Python

## LeetCode Problem

287 - Find the Duplicate Number

## Author

T. Nandhini
