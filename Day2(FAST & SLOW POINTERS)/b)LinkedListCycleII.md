
#142 Leetcode  https://leetcode.com/problems/linked-list-cycle-ii/description/
---

# 1️⃣ Question

**Find the Starting Point of a Cycle in a Linked List**

Given the **head of a linked list**, return the **node where the cycle begins**.
If there is **no cycle**, return `null`.

A cycle occurs when a node’s `next` pointer points back to a **previous node** instead of `null`.

Example:

```text
1 → 2 → 3 → 4 → 5
        ↑     ↓
        ← ← ←
```

Cycle starts at **node 3**, so the output should be **node 3**.

This problem is commonly solved using **Floyd's Cycle Detection Algorithm**.

---

# 2️⃣ Node Structure (ListNode Class)

```java
class ListNode {
    int val;
    ListNode next;

    ListNode(int x) {
        val = x;
        next = null;
    }
}
```

### Explanation

| Part   | Meaning              |
| ------ | -------------------- |
| `val`  | value stored in node |
| `next` | pointer to next node |

Example node:

```
[ value | next ]
```

Example linked list:

```
1 → 2 → 3 → null
```

---

# 3️⃣ Full Code

```java
public ListNode detectCycle(ListNode head) {

    ListNode slow = head;
    ListNode fast = head;

    while (fast != null && fast.next != null) {

        slow = slow.next;
        fast = fast.next.next;

        if (slow == fast) {

            slow = head;

            while (slow != fast) {
                slow = slow.next;
                fast = fast.next;
            }

            return slow;
        }
    }

    return null;
}
```

---

# 4️⃣ Line-by-Line Code Explanation

### Function Declaration

```java
public ListNode detectCycle(ListNode head)
```

* Takes the **head of the linked list**
* Returns the **node where the cycle begins**

---

### Initialize Pointers

```java
ListNode slow = head;
ListNode fast = head;
```

Two pointers start at the **head node**.

| Pointer | Speed   |
| ------- | ------- |
| slow    | 1 step  |
| fast    | 2 steps |

---

### Loop Condition

```java
while (fast != null && fast.next != null)
```

This prevents **NullPointerException** when fast moves two steps.

---

### Move Pointers

```java
slow = slow.next;
```

Slow moves **one step**.

---

```java
fast = fast.next.next;
```

Fast moves **two steps**.

---

### Check if They Meet

```java
if (slow == fast)
```

If both pointers meet → **cycle exists**.

---

### Reset Slow Pointer

```java
slow = head;
```

Move slow back to the **head of the list**.

Fast stays at the **meeting point**.

---

### Move Both Pointers One Step

```java
while (slow != fast)
```

Move both pointers **one step at a time**.

```java
slow = slow.next;
fast = fast.next;
```

---

### Return Cycle Start

```java
return slow;
```

Where they meet = **starting node of the cycle**.

---

### If No Cycle

```java
return null;
```

If fast reaches `null`, there is **no cycle**.

---

# 5️⃣ Dry Run Example

Linked list:

```
1 → 2 → 3 → 4 → 5
        ↑     ↓
        ← ← ←
```

Cycle start = **3**

---

## Phase 1 – Detect Cycle

| Step  | Slow | Fast |
| ----- | ---- | ---- |
| Start | 1    | 1    |
| 1     | 2    | 3    |
| 2     | 3    | 5    |
| 3     | 4    | 4    |

Slow and fast meet at **4**.

Cycle confirmed.

---

## Phase 2 – Find Cycle Start

Reset slow:

```
slow = head
```

Positions:

| Pointer | Node |
| ------- | ---- |
| Slow    | 1    |
| Fast    | 4    |

---

### Move both pointers

| Step | Slow | Fast |
| ---- | ---- | ---- |
| 1    | 2    | 5    |
| 2    | 3    | 3    |

Both meet at **node 3**.

So:

```
Cycle starts at node 3
```

Return **3**.

---

# 6️⃣ Time and Space Complexity

| Type  | Complexity |
| ----- | ---------- |
| Time  | O(n)       |
| Space | O(1)       |

Reason:

* Only one traversal of the list
* No extra memory used

---

# 7️⃣ Key Concept to Remember (Interview Trick)

Just remember these **three steps**:

1️⃣ Detect cycle

```java
slow = slow.next
fast = fast.next.next
```

2️⃣ When they meet

```java
slow = head
```

3️⃣ Move both one step

```java
slow = slow.next
fast = fast.next
```

Where they meet again = **cycle start**.

---

