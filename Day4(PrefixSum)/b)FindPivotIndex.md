
---

# 🧩 PROBLEM: Find Pivot Index

---

# 🧠 APPROACH (how to think)

👉 At any index `i`:

```text
left sum = sum of elements before i  
right sum = sum of elements after i
```

We want:

```text
left sum == right sum
```

---

# ⚡ Smart Trick (no prefix array needed)

Instead of recalculating:

```text
rightSum = totalSum - leftSum - nums[i]
```

👉 Why?

* totalSum = whole array
* subtract left part
* subtract current element

→ what’s left = right side

---

# 💡 FINAL APPROACH

```text
1. Find total sum  
2. Keep leftSum = 0  
3. For each index:
      rightSum = total - left - current
      if equal → return index
      else → update leftSum
```

---

# 💻 FULL CODE

```java
class Solution {
    public int pivotIndex(int[] nums) {
        int totalSum = 0;

        // Step 1: total sum
        for (int num : nums) {
            totalSum += num;
        }

        int leftSum = 0;

        // Step 2: check each index
        for (int i = 0; i < nums.length; i++) {
            int rightSum = totalSum - leftSum - nums[i];

            if (leftSum == rightSum) {
                return i;
            }

            leftSum += nums[i];
        }

        return -1;
    }
}
```

---

# 🔍 LINE BY LINE

---

## `int totalSum = 0;`

👉 stores total array sum

---

## `for (int num : nums)`

👉 loop to calculate total

---

## `int leftSum = 0;`

👉 nothing on left initially

---

## `for (int i = 0; i < nums.length; i++)`

👉 check each index

---

## `rightSum = totalSum - leftSum - nums[i];`

👉 removes left + current → gives right

---

## `if (leftSum == rightSum)`

👉 pivot found

---

## `leftSum += nums[i];`

👉 update for next index

---

## `return -1`

👉 no pivot found

---

# 🧪 DRY RUN (TABLE — easy revision)

### Input:

```text
nums = [1, 7, 3, 6, 5, 6]
```

Total sum = 28

---

| i | nums[i] | leftSum | rightSum = total-left-num[i] | Match? |
| - | ------- | ------- | ---------------------------- | ------ |
| 0 | 1       | 0       | 28-0-1 = 27                  | ❌      |
| 1 | 7       | 1       | 28-1-7 = 20                  | ❌      |
| 2 | 3       | 8       | 28-8-3 = 17                  | ❌      |
| 3 | 6       | 11      | 28-11-6 = 11                 | ✅ ✅    |

---

# 🏁 ANSWER

```text
Pivot Index = 3
```

---

# ⏱ TIME & SPACE (short)

* Time → **O(n)** (2 loops)
* Space → **O(1)** (no extra array)

---

# 🧠 ONE-LINE MEMORY

> “Left grows, right is calculated — compare both.”

---

# 💀 COMMON MISTAKE

❌ Forgetting to subtract `nums[i]`
❌ Updating `leftSum` before checking

---

# 🔥 FINAL INTUITION

> “At every index, check balance using total — don’t recalculate sums.”

---

If you want next:

* **Subarray Sum = K (MOST IMPORTANT prefix problem 🔥)**
* or I can give you a **1-page sheet of all patterns (sliding + prefix)**
