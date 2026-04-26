
---

# 🧩 PROBLEM: Minimum Size Subarray Sum

### 📌 Question

Given an array of positive integers `nums` and an integer `target`, return the **minimum length** of a subarray whose sum ≥ target.
If none exists → return 0.

---

# 🧠 APPROACH (how to THINK)

### Step 1: Identify pattern

* Subarray → contiguous → Sliding Window ✅
* Condition → sum ≥ target
* Goal → MIN length

---

### Step 2: Strategy

```text
Expand → until sum ≥ target  
Then → shrink to get smallest valid window
```

---

### 🔥 Golden Rule

```text
If sum < target → expand  
If sum ≥ target → shrink
```

---

# 💻 FULL CODE

```java id="g2y1ah"
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int currSum = 0;
        int left = 0;
        int minLen = Integer.MAX_VALUE;

        for (int right = 0; right < nums.length; right++) {
            currSum += nums[right];

            while (currSum >= target) {
                minLen = Math.min(minLen, right - left + 1);
                currSum -= nums[left];
                left++;
            }
        }

        return minLen == Integer.MAX_VALUE ? 0 : minLen;
    }
}
```

---

# 🔍 LINE BY LINE (next to code logic)

| Line | Code                       | Meaning               |
| ---- | -------------------------- | --------------------- |
| 1    | `currSum = 0`              | current window sum    |
| 2    | `left = 0`                 | window start          |
| 3    | `minLen = MAX`             | store smallest length |
| 4    | `for right`                | expand window         |
| 5    | `currSum += nums[right]`   | add element           |
| 6    | `while(currSum >= target)` | condition satisfied   |
| 7    | `minLen = ...`             | update answer         |
| 8    | `currSum -= nums[left]`    | remove left           |
| 9    | `left++`                   | shrink window         |
| 10   | return                     | final answer          |

---

# 🧪 DRY RUN (TABLE — easy revision)

### Input:

```text
nums = [2,3,1,2,4,3], target = 7
```

---

| Step | right | val | currSum | Action       | left | window  | length | minLen |
| ---- | ----- | --- | ------- | ------------ | ---- | ------- | ------ | ------ |
| 1    | 0     | 2   | 2       | expand       | 0    | [2]     | —      | ∞      |
| 2    | 1     | 3   | 5       | expand       | 0    | [2,3]   | —      | ∞      |
| 3    | 2     | 1   | 6       | expand       | 0    | [2,3,1] | —      | ∞      |
| 4    | 3     | 2   | 8       | shrink       | 1    | [3,1,2] | 4→3    | 3      |
| 5    | 4     | 4   | 10      | shrink twice | 3    | [2,4]   | 4→3→2  | 2      |
| 6    | 5     | 3   | 9       | shrink       | 4    | [4,3]   | 3→2    | 2      |

---

# 🚨 CRITICAL STEP (understand this or you're done)

At Step 5:

```text
sum = 10
```

Shrink:

```text
remove 3 → sum = 7 ✅  
remove 1 → sum = 6 ❌
```

👉 That’s why **2 shrinks happen**

---

# 🧠 FINAL ANSWER

```text
minLen = 2
subarray = [4,3]
```

---

# ⏱ TIME & SPACE COMPLEXITY

### ⏱ Time: O(n)

* Each element added once
* Removed once

---

### 📦 Space: O(1)

* No extra data structures

---

# 💀 COMMON MISTAKES (EXAM TRAPS)

❌ Using `currSum` instead of length
❌ Using `if` instead of `while`
❌ Returning inside loop
❌ Forgetting `+1` in window size

---

# ⚡ FINAL TEMPLATE (memorize this)

```java id="s0xkjc"
for (right):
    add element

    while (condition true):
        update answer
        remove left
        left++
```

---

# 🧠 ONE-LINE INTUITION

> “Reach the target → then squeeze the window to smallest possible.”

---
