
---

# 1️⃣ Question

**26. Remove Duplicates from Sorted Array**

You are given a **sorted integer array `nums`**.

Your task:

* Remove duplicates **in-place** (do not create another array).
* Each unique element should appear **only once**.
* Keep the **same order** of elements.

Return:

* `k` = **number of unique elements**.

Important rule:

* The **first `k` elements** of `nums` must contain the unique numbers.
* Elements after index `k-1` can be ignored.

Example:

```
Input: nums = [1,1,2]

Output: 2
Array becomes: [1,2,_]
```

`_` means ignore remaining elements.

---

# 2️⃣ Complete Java Code

```java
class Solution {
    public int removeDuplicates(int[] nums) {

        int j = 1; // writer pointer

        for (int i = 1; i < nums.length; i++) { // scout pointer

            if (nums[i] != nums[j - 1]) { // check if new unique number

                nums[j] = nums[i]; // place unique number
                j++;               // move writer forward
            }
        }

        return j; // number of unique elements
    }
}
```

---

# 3️⃣ Line-by-Line Explanation

### Function definition

```java
public int removeDuplicates(int[] nums)
```

* Function takes **array nums**
* Returns **number of unique elements**

---

### Writer pointer

```java
int j = 1;
```

`j` is the **writer pointer**.

It tells **where to place the next unique element**.

We start from `1` because:

* `nums[0]` is always unique.

Example:

```
[1,1,2]
 ↑
first unique element
```

---

### Loop

```java
for (int i = 1; i < nums.length; i++)
```

`i` is the **scout pointer**.

It scans the whole array looking for new numbers.

---

### Check condition

```java
if (nums[i] != nums[j - 1])
```

Compare:

```
current number
vs
last unique number
```

If they are different → we found a **new unique value**.

---

### Write new value

```java
nums[j] = nums[i];
```

Put the new unique value in the next position.

---

### Move writer

```java
j++;
```

Move writer pointer forward.

Now it waits for the next unique number.

---

### Return result

```java
return j;
```

`j` = **total number of unique elements**.

Only first `j` elements are valid.

---

# 4️⃣ Dry Run Example

Input:

```
nums = [1,1,2]
```

Initial state

```
i = scout
j = writer
```

---

# Dry Run Table

| Step  | i | nums[i] | j | nums[j-1] | Condition     | Action         | Array   |
| ----- | - | ------- | - | --------- | ------------- | -------------- | ------- |
| Start | - | -       | 1 | 1         | -             | initialize     | [1,1,2] |
| 1     | 1 | 1       | 1 | 1         | 1 ≠ 1 → False | skip           | [1,1,2] |
| 2     | 2 | 2       | 1 | 1         | 2 ≠ 1 → True  | nums[1]=2, j++ | [1,2,2] |

Loop ends.

---

# 5️⃣ Final Result

Array becomes:

```
[1,2,2]
```

Return value:

```
j = 2
```

Meaning:

```
First 2 elements are unique
```

Valid result:

```
[1,2]
```

Ignore the rest.

---

# 6️⃣ Visual Pointer Movement

Start

```
[1 1 2]
 i
 j
```

Duplicate found → skip

```
[1 1 2]
   i
 j
```

New number found

```
[1 2 2]
     i
   j
```

---

# 7️⃣ Time Complexity

```
O(n)
```

Because we scan the array **once**.

---

# 8️⃣ One-line Interview Answer

> Use two pointers: one scans the array and the other writes unique values at the front, modifying the array in-place in **O(n)** time.

---

