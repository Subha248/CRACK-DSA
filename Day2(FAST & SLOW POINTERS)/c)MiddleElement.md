
---

# Problem: Find the middle of a linked list

Imagine this list:

```
1 → 2 → 3 → 4 → 5 → null
```

We want to return **3** (the middle node).

Unlike arrays, a linked list **doesn't know its size**.
So we can’t just do `length / 2`.

---

# Brute Force Way (boring but works)

Step 1 → Count nodes

```
1 → 2 → 3 → 4 → 5
count = 5
```

Step 2 → Go again to `5/2 = 2`

```
1 → 2 → 3
        ↑ middle
```

Problem: **You traverse the list twice.**

---

# Smart Way (Fast + Slow Pointer)

Instead of counting, we use **two pointers**.

```
slow → moves 1 step
fast → moves 2 steps
```

Start:

```
slow = 1
fast = 1
```

---

## Step 1

```
slow moves 1
fast moves 2
```

```
1 → 2 → 3 → 4 → 5
     ↑
    slow

         ↑
        fast
```

slow = 2
fast = 3

---

## Step 2

Move again.

```
1 → 2 → 3 → 4 → 5
          ↑
         slow

                ↑
               fast
```

slow = 3
fast = 5

---

## Step 3

Now fast tries to move 2 steps but **hits null**.

So the loop stops.

```
1 → 2 → 3 → 4 → 5
          ↑
        slow (middle)
```

Boom. Middle found.

---

# The key idea

Fast moves **twice as fast**.

So when fast reaches the **end**, slow only traveled **half** the distance.

Half distance = **middle**.

---

# Beginner Code (clean version)

```java
public ListNode middleNode(ListNode head) {

    ListNode slow = head;
    ListNode fast = head;

    while (fast != null && fast.next != null) {

        slow = slow.next;        // move 1 step
        fast = fast.next.next;   // move 2 steps

    }

    return slow;
}
```

---

# Why this condition?

```
fast != null && fast.next != null
```

Because `fast.next.next` must exist.
Otherwise Java throws **NullPointerException**.

---

# Visual Memory Trick (this helps a lot)

Imagine:

🐢 **Tortoise (slow)** → walking
🐇 **Rabbit (fast)** → running

Rabbit reaches the finish line.
Tortoise will be **exactly halfway**.

---

# Time Complexity

| Method            | Time                   |
| ----------------- | ---------------------- |
| Brute force       | O(n) + O(n)            |
| Fast/slow pointer | **O(n)** (single pass) |

---

# One more thing (important interview detail)

If list is:

```
1 → 2 → 3 → 4 → 5 → 6
```

Your code returns:

```
4
```

Because it returns the **second middle**.

Interviewers usually accept that.

---

