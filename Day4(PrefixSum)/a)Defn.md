
---

# 🧠 PREFIX SUM — FINAL REVISION SHEET

---

# ✅ 1. DEFINITION (write this in exam)

> **Prefix Sum is a technique where we store cumulative sums from the beginning of the array up to each index.**

```text
prefix[i] = arr[0] + arr[1] + ... + arr[i]
```

---

# ⚡ 2. WHY WE USE IT

👉 To calculate subarray sum **quickly**

### Without prefix sum:

```text
O(n) per query ❌
```

### With prefix sum:

```text
O(1) per query ✅
```
$O(n)$ is a loop; $O(1)$ is a shortcut.

* $O(n)$ (Counting): You count every item one by one. More items = more time.
* $O(1)$ (Lookup): You jump straight to the answer. More items = same time.

Bottom line: $O(n)$ works harder; $O(1)$ works smarter.
Want to see the one-line code that makes $O(1)$ happen?


---

# 🔥 3. MAIN FORMULA (MOST IMPORTANT)

```text
sum(i, j) = prefix[j] - prefix[i-1]   (i > 0)
sum(0, j) = prefix[j]
```

---

# 💻 4. HOW TO BUILD PREFIX ARRAY

```java
int[] prefix = new int[n];
prefix[0] = arr[0];

for (int i = 1; i < n; i++) {
    prefix[i] = prefix[i - 1] + arr[i];
}
```

---

# 🧠 5. HOW TO IDENTIFY IN EXAM

If question says:

👉 “sum of subarray / range”
👉 “multiple sum queries”
👉 “count subarrays with sum = k”
👉 “cumulative / prefix-based condition”

🚨 → Use **Prefix Sum**

---

# 📌 6. WHERE IT IS USED

* Range sum queries
* Subarray sum problems
* Count subarrays = k
* 2D matrix sums
* Histogram / frequency problems

---

# ⚡ 7. BENEFITS

* Avoid repeated calculation
* Makes problems faster
* Converts **O(n²) → O(n)**
* Simple logic using precomputed sums

---

# 🧠 FINAL MEMORY TRICK (THIS WILL STICK)

> “Prefix sum = store past → answer future instantly”

---

# 💀 COMMON MISTAKES

❌ Forgetting `i-1`
❌ Wrong index handling
❌ Not handling `i = 0`

---

# 🔥 ONE-LINE APPROACH (write in exam)

> Build prefix array → use prefix formula to answer subarray sum queries efficiently.

---


* I’ll give you **Subarray Sum = K (MOST IMPORTANT prefix problem 🔥)**
* or a **comparison: Prefix vs Sliding Window (exam gold)**
