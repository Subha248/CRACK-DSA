

---

# 📘 **Sliding Window Pattern — IMPORTANT POINTS**

---

### 🔹 **Definition**

* Used for **contiguous subarrays / substrings**
* Uses **two pointers (start, end)** to form a **window**
* Window **slides forward**
* Instead of recalculating → **add new element + remove old element**
* Can be:

  * **Fixed size**
  * **Variable size**

---

### 🔹 **Where to Apply**

* Problems with **subarrays / substrings (continuous)**
* Need to find:

  * **sum / max / min**
  * **count / frequency**
* When range **moves step-by-step**

---

### 🔹 **Types**

#### ✅ **1. Fixed Size Window**

* Window size = **k**
* Steps:

  * Add new element
  * Remove left element
  * Update answer

---

#### ✅ **2. Variable Size Window**

* Window **expands + shrinks**
* Used when condition like:

  * **sum ≥ target**
  * **unique elements**
* Expand → check → **shrink if needed**

---

### 🔹 **How to Identify (VERY IMPORTANT)**

👉 If you see:

* **subarray / substring**
* **contiguous / continuous**
* **max / min / longest / shortest**
* Large constraints (**n ≈ 10⁵**)
* Brute force = **O(n²)** ❌

💥 Then → **Sliding Window**

---

### 🔹 **Benefits**

* ⏱ **O(n)** time (instead of O(n²))
* 🧠 Efficient (no recomputation)
* 🔄 Works for both types
* 📊 Good for real-time/stream data

---

# ⚡ **1-LINE MEMORY**

```text
Contiguous + optimize → Sliding Window
```

---



# 🧠 SLIDING WINDOW (WITH COMPLEXITY)

👉 **Sliding Window is a technique used to process contiguous subarrays or substrings by maintaining a window using two pointers (left and right), and updating the result efficiently by adding the new element and removing the old one as the window moves.**

---

# ⚡ TIME COMPLEXITY

👉 **O(n)**

### Why?

* Each element is:

  * added **once** (when right moves)
  * removed **once** (when left moves)

👉 No nested loops → just one pass

---

# 📦 SPACE COMPLEXITY

👉 **O(1) or O(k) or O(n)** (depends on problem)

### Why?

* If no extra structure → **O(1)**
* If using set/map for window → **O(k)** or **O(n)**

---

# 🔥 ULTRA SHORT (INTERVIEW MIC DROP)

👉 **“Sliding window uses two pointers to maintain a contiguous window, updating results in O(n) time by adding and removing elements instead of recomputing.”**

---

