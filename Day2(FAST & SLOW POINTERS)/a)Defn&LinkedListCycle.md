
---

# 1️⃣ Question

**Detect Cycle in a Linked List**

Given the **head of a linked list**, determine whether the linked list contains a **cycle**.

A cycle occurs when a node’s `next` pointer points back to a **previous node** in the list instead of pointing to `null`.

Return:

* `true` → if a cycle exists
* `false` → if no cycle exists

This problem is commonly solved using **Floyd's Cycle Detection Algorithm**, also called the **Fast and Slow Pointer technique**.

---

# 2️⃣ ListNode Class (Node Structure)

Before solving the problem, we define a node of a linked list.

```java
class ListNode {

    int val;        // value stored in node
    ListNode next;  // pointer to next node

    ListNode(int x) {
        val = x;
        next = null;
    }
}
```

### Explanation

Each node contains:

| Part   | Purpose                             |
| ------ | ----------------------------------- |
| `val`  | stores the data                     |
| `next` | stores the address of the next node |

Example structure:

```
[ value | next address ]
```

Example linked list:

```
1 → 2 → 3 → 4 → null
```

If there is a **cycle**:

```
1 → 2 → 3 → 4 → 5
        ↑       ↓
        ← ← ← ←
```

---

# 3️⃣ Full Code (Cycle Detection)

```java
public boolean hasCycle(ListNode head) {

    ListNode slow = head;
    ListNode fast = head;

    while (fast != null && fast.next != null) {

        slow = slow.next;
        fast = fast.next.next;

        if (slow == fast) {
            return true;
        }
    }

    return false;
}
```

---

# 4️⃣ Line-by-Line Explanation

### Line 1

```java
public boolean hasCycle(ListNode head)
```

This method checks **whether a cycle exists in the linked list**.

* `head` → starting node of the list
* return type → `boolean`

---

### Line 3

```java
ListNode slow = head;
```

Create a **slow pointer**.

It moves **one step at a time**.

---

### Line 4

```java
ListNode fast = head;
```

Create a **fast pointer**.

It moves **two steps at a time**.

---

### Line 6

```java
while (fast != null && fast.next != null)
```

Loop continues while:

* `fast` is not null
* `fast.next` is not null

This prevents **NullPointerException** when moving two steps.

---

### Line 8

```java
slow = slow.next;
```

Move slow pointer **one node forward**.

---

### Line 9

```java
fast = fast.next.next;
```

Move fast pointer **two nodes forward**.

---

### Line 11

```java
if (slow == fast)
```

Check if both pointers **meet at the same node**.

If they meet → a **cycle exists**.

---

### Line 13

```java
return true;
```

Cycle detected.

---

### After Loop Ends

```java
return false;
```

If loop finishes, `fast` reached **null**.

That means **no cycle exists**.

---

# 5️⃣ Dry Run (Step-by-Step)

Example linked list with cycle

```
1 → 2 → 3 → 4 → 5
        ↑     ↓
        ← ← ←
```

### Initial State

| Step  | Slow | Fast |
| ----- | ---- | ---- |
| Start | 1    | 1    |

---

### Iteration 1

Slow moves **1 step**
Fast moves **2 steps**

| Step | Slow | Fast |
| ---- | ---- | ---- |
| 1    | 2    | 3    |

---

### Iteration 2

| Step | Slow | Fast |
| ---- | ---- | ---- |
| 2    | 3    | 5    |

---

### Iteration 3

| Step | Slow | Fast |
| ---- | ---- | ---- |
| 3    | 4    | 4    |

Now:

```
slow == fast
```

Pointers meet → **Cycle exists**

Return **true**.

---

# 6️⃣ Case Without Cycle

Example:

```
1 → 2 → 3 → 4 → 5 → null
```

| Step  | Slow | Fast |
| ----- | ---- | ---- |
| Start | 1    | 1    |
| 1     | 2    | 3    |
| 2     | 3    | 5    |
| 3     | 4    | null |

Fast becomes **null** → loop stops.

Return **false**.

---

# 7️⃣ Time & Space Complexity

| Type  | Complexity |
| ----- | ---------- |
| Time  | **O(n)**   |
| Space | **O(1)**   |

Reason:

* Only one traversal
* No extra memory used

---

# 8️⃣ One Key Interview Point

Always remember the rule:

```
slow → move 1 step
fast → move 2 steps
```

If there is a cycle, **fast will eventually catch slow**.

That’s the main idea of **Floyd's Cycle Detection Algorithm**.

---

✅ If you want, I can also show you the **most important follow-up interview question**:
**“How to find the exact starting node of the cycle”** (this is asked in companies a lot).
