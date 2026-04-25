
---

# 🎯 PROBLEM (say this first in interview)

👉 “Find the **maximum sum** of a subarray of size `k`
such that **all elements are distinct**.”

---

# 🧠 WHY SLIDING WINDOW (quick + sharp)

👉 Because:

* subarray = contiguous ✅
* size = fixed (k) ✅
* need max sum ✅

💥 So instead of O(n²), we use **Sliding Window → O(n)**

---

# 💻 CODE (we’ll run THIS line-by-line)

```java
public long maximumSubarraySum(int[] nums, int k) {
    HashSet<Integer> set = new HashSet<>();
    long currentSum = 0;
    long maxSum = 0;
    int left = 0;

    for (int right = 0; right < nums.length; right++) {

        while (set.contains(nums[right]) || set.size() == k) {
            set.remove(nums[left]);
            currentSum -= nums[left];
            left++;
        }

        currentSum += nums[right];
        set.add(nums[right]);

        if (set.size() == k) {
            maxSum = Math.max(maxSum, currentSum);
        }
    }
    return maxSum;
}
```

---

# 🔥 DRY RUN (CODE + THINKING TOGETHER)

### INPUT:

```java
nums = [1, 2, 1, 3, 4]
k = 3
```

---

## 🔄 STEP 1 → `right = 0`

```java
nums[right] = 1
```

### while:

```java
set.contains(1)? ❌
set.size == k? ❌
```

👉 no problem → don’t shrink

### add:

```java
currentSum = 0 + 1 = 1
set = {1}
```

### check:

```java
size = 1 ≠ k → ignore
```

---

## 🔄 STEP 2 → `right = 1`

```java
nums[right] = 2
```

### while:

```java
duplicate? ❌
size full? ❌
```

👉 safe

### add:

```java
currentSum = 1 + 2 = 3
set = {1,2}
```

### check:

```java
size = 2 ≠ k
```

---

## 🔄 STEP 3 → `right = 2`

```java
nums[right] = 1
```

### 🚨 while:

```java
set.contains(1)? ✅ DUPLICATE
```

👉 PROBLEM → shrink window

---

### 🔻 remove left

```java
nums[left] = 1
```

```java
set.remove(1)
currentSum = 3 - 1 = 2
left = 1
```

👉 now:

```java
set = {2}
```

---

### while again:

```java
duplicate? ❌
size full? ❌
```

👉 stop shrinking

---

### add new:

```java
currentSum = 2 + 1 = 3
set = {2,1}
```

### check:

```java
size = 2 ≠ k
```

---

## 🔄 STEP 4 → `right = 3`

```java
nums[right] = 3
```

### while:

```java
duplicate? ❌
size full? ❌
```

👉 safe

---

### add:

```java
currentSum = 3 + 3 = 6
set = {2,1,3}
```

---

### check:

```java
size == k ✅
```

```java
maxSum = max(0, 6) = 6
```

---

## 🔄 STEP 5 → `right = 4`

```java
nums[right] = 4
```

### 🚨 while:

```java
size == k? ✅ WINDOW FULL
```

👉 must remove before adding

---

### 🔻 remove left

```java
nums[left] = 2
```

```java
set.remove(2)
currentSum = 6 - 2 = 4
left = 2
```

👉 now:

```java
set = {1,3}
```

---

### while again:

```java
duplicate? ❌
size full? ❌
```

👉 stop

---

### add:

```java
currentSum = 4 + 4 = 8
set = {1,3,4}
```

---

### check:

```java
size == k ✅
```

```java
maxSum = max(6, 8) = 8
```

---

# 🏁 FINAL

```java
return 8
```

---

# 🧠 WHAT YOU SHOULD SAY OUT LOUD IN INTERVIEW

👉 “I expand the window using `right` pointer.”
👉 “If duplicate or size exceeds, I shrink using `left`.”
👉 “I maintain sum incrementally instead of recomputing.”
👉 “When window size becomes k, I update max sum.”

---

# ⚡ TIME & SPACE (SHORT + STRONG)

### ⏱ Time = O(n)

👉 each element added once, removed once

---

### 📦 Space = O(k)

👉 set stores at most k elements

---

# 🔥 FINAL MENTAL IMAGE

```text
expand → problem? → shrink → add → check → repeat
```

---

