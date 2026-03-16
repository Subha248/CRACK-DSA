## 1️⃣ Question

**Container With Most Water**

You are given an integer array `height` where each element represents the **height of a vertical line** on the x-axis.

Find **two lines** that together with the x-axis form a container such that the container holds the **maximum amount of water**.

**Return the maximum area of water a container can store.**

### Example

Input
`height = [1,8,6,2,5,4,8,3,7]`

Output
`49`

---

# 2️⃣ Full Java Code

```java
public int maxArea(int[] height) {

    int left = 0;
    int right = height.length - 1;

    int maxArea = 0;

    while (left < right) {

        int currentArea = Math.min(height[left], height[right]) * (right - left);

        maxArea = Math.max(maxArea, currentArea);

        if (height[left] < height[right]) {
            left++;
        } 
        else {
            right--;
        }
    }

    return maxArea;
}
```

---

# 3️⃣ Line-by-Line Explanation

### Line 1

```java
public int maxArea(int[] height)
```

* Method that returns the **maximum water area**
* `height[]` = array containing heights of vertical bars

---

### Line 3

```java
int left = 0;
```

* Pointer starting from **beginning of array**

Example
`height[left] = first bar`

---

### Line 4

```java
int right = height.length - 1;
```

* Pointer starting from **last index**

So initially we take the **widest container possible**

---

### Line 6

```java
int maxArea = 0;
```

* Variable to store the **largest area found so far**

---

### Line 8

```java
while (left < right)
```

Loop runs **until pointers meet**

Because once they meet, no container exists.

---

### Line 10

```java
int currentArea = Math.min(height[left], height[right]) * (right - left);
```

Water container area formula:

A = \min(h_l, h_r) \times (r - l)

Where

* `min(height[left], height[right])` → **height of container**
* `(right - left)` → **width between lines**

We use **minimum height** because water spills from the shorter bar.

---

### Line 12

```java
maxArea = Math.max(maxArea, currentArea);
```

Compare

```
previous max area
vs
current area
```

Store the **larger value**.

---

### Line 14-20

```java
if (height[left] < height[right]) {
    left++;
} else {
    right--;
}
```

Move the pointer pointing to the **smaller height**.

Reason:

If we move the taller bar
➡ width decreases
➡ height still limited by shorter bar
➡ area cannot increase.

So we search for a **taller bar by moving the smaller side**.

---

### Line 23

```java
return maxArea;
```

Return the **largest water container area** found.

---

# 4️⃣ Dry Run (Step-by-Step Table)

Example

```
height = [1,8,6,2,5,4,8,3,7]
```

| Step | left | right | height[left] | height[right] | width | min height | area | maxArea |
| ---- | ---- | ----- | ------------ | ------------- | ----- | ---------- | ---- | ------- |
| 1    | 0    | 8     | 1            | 7             | 8     | 1          | 8    | 8       |
| 2    | 1    | 8     | 8            | 7             | 7     | 7          | 49   | 49      |
| 3    | 1    | 7     | 8            | 3             | 6     | 3          | 18   | 49      |
| 4    | 1    | 6     | 8            | 8             | 5     | 8          | 40   | 49      |
| 5    | 1    | 5     | 8            | 4             | 4     | 4          | 16   | 49      |
| 6    | 1    | 4     | 8            | 5             | 3     | 5          | 15   | 49      |
| 7    | 1    | 3     | 8            | 2             | 2     | 2          | 4    | 49      |
| 8    | 1    | 2     | 8            | 6             | 1     | 6          | 6    | 49      |

Pointers meet → loop stops.

✅ **Maximum Area = 49**

---

# 5️⃣ Time & Space Complexity

**Time Complexity**

```
O(n)
```

Only one pass through the array.

**Space Complexity**

```
O(1)
```

No extra memory used.

---

✅ **Key Interview Trick**

Always remember:

```
Move the pointer with smaller height
```

Not random. Not both. Only **smaller one**.

---

