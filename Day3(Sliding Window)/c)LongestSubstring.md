
---

# 🧠 FIRST: How to THINK (not memorize)

### Ask yourself 3 questions:

### 1. Is it **contiguous**?

👉 Substring = YES
So brute force (all substrings) = O(n²) ❌ too slow

---

### 2. Are we asked **max/min length**?

👉 Longest substring → sounds like “expand window” problem

---

### 3. Any **condition inside window**?

👉 “No repeating characters” = constraint

---

💡 Boom → this is **Sliding Window (variable size)**

---

# ⚡ Core Idea (burn this in your brain)

* Expand window → move `right`
* If valid → update answer
* If invalid (duplicate) → shrink window → move `left`

---

# 🔥 Code (clean + correct version)

```java
public int lengthOfLongestSubstring(String s) {
    int n = s.length();
    int maxLength = 0;
    int left = 0;

    HashSet<Character> set = new HashSet<>();

    for (int right = 0; right < n; right++) {

        // If duplicate found → shrink window
        while (set.contains(s.charAt(right))) {
            set.remove(s.charAt(left));
            left++;
        }

        // Add current char
        set.add(s.charAt(right));

        // Update max length
        maxLength = Math.max(maxLength, right - left + 1);
    }

    return maxLength;
}
```

---

# 🧩 LINE BY LINE (no confusion allowed)

### `int left = 0;`

👉 Start of window

---

### `for (int right = 0; right < n; right++)`

👉 Expanding window from left → right

---

### `while (set.contains(s.charAt(right)))`

👉 If duplicate found ❌
Window is invalid → FIX IT

---

### `set.remove(s.charAt(left));`

👉 Remove left character

---

### `left++;`

👉 Shrink window from left

---

💡 This loop runs until duplicate is gone

---

### `set.add(s.charAt(right));`

👉 Now safe → add new character

---

### `maxLength = Math.max(maxLength, right - left + 1);`

👉 Current window size = `right - left + 1`

---

# 🚀 DRY RUN (this is where it clicks)
# 🧪 String: `"abcabcbb"`

```
Index:   0 1 2 3 4 5 6 7
Char:    a b c a b c b b
```

---

# 📊 FULL DRY RUN TABLE

| Step | right | char | Action (while loop) | set after | left | window | length | max |
| ---- | ----- | ---- | ------------------- | --------- | ---- | ------ | ------ | --- |
| 1    | 0     | a    | —                   | {a}       | 0    | a      | 1      | 1   |
| 2    | 1     | b    | —                   | {a,b}     | 0    | ab     | 2      | 2   |
| 3    | 2     | c    | —                   | {a,b,c}   | 0    | abc    | 3      | 3   |
| 4    | 3     | a    | remove a            | {b,c,a}   | 1    | bca    | 3      | 3   |
| 5    | 4     | b    | remove b            | {c,a,b}   | 2    | cab    | 3      | 3   |
| 6    | 5     | c    | remove c            | {a,b,c}   | 3    | abc    | 3      | 3   |
| 7    | 6     | b    | remove a, remove b  | {c,b}     | 5    | cb     | 2      | 3   |
| 8    | 7     | b    | remove c, remove b  | {b}       | 7    | b      | 1      | 3   |

---

# 🧠 HOW TO READ THIS FAST

### Column meanings:

* **right** → expanding pointer
* **char** → current character
* **Action** → what got removed (important!)
* **set** → current window unique chars
* **left** → start of window
* **window** → current substring
* **length** → `right - left + 1`
* **max** → answer so far

---

# 🔥 MOST IMPORTANT ROWS (focus here)

### ⚠️ Step 7 (right = 6, b)

```
duplicate → remove a, remove b
window shrinks BIG
```

---

### ⚠️ Step 8 (right = 7, b)

```
duplicate again → remove c, remove b
window becomes tiny
```

---

# 💡 Pattern you should notice

* First 3 steps → smooth expansion
* Middle → stable size (3)
* Last → aggressive shrinking

---

# 🧠 One-glance memory trick

```
abc → bca → cab → abc → cb → b
```

Max always stayed **3**

---

# ⚡ Ultra-short template (revise before exam)

```
for right:
    while duplicate:
        remove left
        left++

    add current
    update max
```

---



---

# 🧠 REAL INTUITION (remember this)

Think like this:

> “I will keep expanding my window until I break the rule.
> The moment I break it, I will shrink from left until it becomes valid again.”

That’s it. That’s the whole pattern.

---

# ⚡ Time & Space Complexity

* Time → **O(n)** (each char added + removed once)
* Space → **O(k)** (unique chars in set)

---

# 💀 Common Mistake (don’t do this)

❌ Using `if` instead of `while`
👉 That fails when multiple duplicates exist

---

# 🚀 Final Mental Template

Whenever you see:

* substring
* longest / smallest
* condition

👉 Instantly think:

> **Sliding Window + Expand + Shrink**

---

