
---

# Two Pointer – Two Sum (Sorted Array)

## Full Code

```java
class Solution {

    public int[] twoSum(int[] numbers, int target) {

        int left = 0;                     // pointer at beginning
        int right = numbers.length - 1;   // pointer at end

        int[] res = new int[2];           // array to store answer

        while (left < right) {            // loop until pointers meet

            int sum = numbers[left] + numbers[right];   // calculate sum

            if (sum == target) {          // if correct pair found
                res[0] = left + 1;        // store first index (+1 for 1-based indexing)
                res[1] = right + 1;       // store second index
                return res;               // stop and return result
            }

            else if (sum < target) {      // sum too small
                left++;                   // move left pointer to bigger number
            }

            else {                        // sum too big
                right--;                  // move right pointer to smaller number
            }
        }

        return res;                       // return result if loop ends
    }
}
```

---

# Line-by-Line Explanation

### Function declaration

```java
public int[] twoSum(int[] numbers, int target)
```

* Function name: `twoSum`
* Input:

  * `numbers` → sorted array
  * `target` → required sum
* Output:

  * array of **two indices**

---

### Left pointer

```java
int left = 0;
```

Points to **first element**.

Example:

```
[2,7,11,15]
 ↑
left
```

---

### Right pointer

```java
int right = numbers.length - 1;
```

Points to **last element**.

```
[2,7,11,15]
        ↑
      right
```

---

### Result array

```java
int[] res = new int[2];
```

Create array of size **2** to store answer.

```
res = [ ?, ? ]
```

---

### While loop

```java
while (left < right)
```

Loop runs until pointers **meet or cross**.

---

### Calculate sum

```java
int sum = numbers[left] + numbers[right];
```

Add the two numbers.

---

### Case 1 — Pair found

```java
if (sum == target)
```

Store indices.

```java
res[0] = left + 1;
res[1] = right + 1;
```

`+1` because problem uses **1-based indexing**.

Example:

```
array index : 0 1 2 3
human index : 1 2 3 4
```

Return result:

```java
return res;
```

---

### Case 2 — Sum too small

```java
else if(sum < target)
```

Move left pointer.

```java
left++;
```

Because array is sorted, moving right would increase sum.

---

### Case 3 — Sum too big

```java
else
```

Move right pointer.

```java
right--;
```

Because we need smaller number.

---

### Final return

```java
return res;
```

Required by Java if no pair found.

---

# Example Dry Run

Input:

```
numbers = [2,7,11,15]
target = 18
```

---

## Step 1

```
left = 0 → 2
right = 3 → 15
```

```
sum = 2 + 15 = 17
```

```
17 < 18
```

Move left.

```
left++
```

---

## Step 2

```
left = 1 → 7
right = 3 → 15
```

```
sum = 7 + 15 = 22
```

```
22 > 18
```

Move right.

```
right--
```

---

## Step 3

```
left = 1 → 7
right = 2 → 11
```

```
sum = 7 + 11 = 18
```

Match found.

Store indices:

```
res[0] = 2
res[1] = 3
```

Return:

```
[2,3]
```

---

# Pointer Movement Visualization

Start

```
[2 7 11 15]
 L      R
```

Move left

```
[2 7 11 15]
   L    R
```

Move right

```
[2 7 11 15]
   L  R
```

Answer found.

---

# Time Complexity

```
O(n)
```

Because each element is visited **at most once**.

Brute force would be:

```
O(n²)
```

---

💡 **One exam/interview sentence to remember**

> Two Pointers is an algorithm technique where two indices traverse a sorted array from opposite ends to efficiently find pairs or satisfy conditions in linear time.

---

If you want, I can also show you **3 Two-Pointer problems that appear insanely often in coding interviews** (Palindrome, Remove Duplicates, Container With Most Water). They basically cover **90% of two-pointer questions.**
