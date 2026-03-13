## 1️⃣ Problem

**LeetCode 125 – Valid Palindrome**

Given a string `s`, return **true** if it is a palindrome after:

* converting all letters to **lowercase**
* removing all **non-alphanumeric characters** (anything that is not a letter or number)

Otherwise return **false**.

Example

```
Input: "A man, a plan, a canal: Panama"
Output: true
```

---

# 2️⃣ Full Java Code

```java
class Solution {
    public boolean isPalindrome(String s) {

        s = s.toLowerCase();
        s = s.replaceAll("[^a-z0-9]", "");

        int i = 0;
        int j = s.length() - 1;

        while (i < j) {
            if (s.charAt(i) != s.charAt(j)) {
                return false;
            }
            i++;
            j--;
        }

        return true;
    }
}
```

---

# 3️⃣ Line-by-Line Explanation

### Function definition

```java
public boolean isPalindrome(String s)
```

Function takes a **string `s`** and returns **true or false**.

---

### Convert to lowercase

```java
s = s.toLowerCase();
```

Example

```
"A Man" → "a man"
```

This ensures uppercase and lowercase letters are treated the same.

---

### Remove non-alphanumeric characters

```java
s = s.replaceAll("[^a-z0-9]", "");
```

`[^a-z0-9]` means:

```
remove everything except
letters a-z
numbers 0-9
```

Example

```
"A man, a plan!" → "amanaplan"
```

---

### Left pointer

```java
int i = 0;
```

`i` starts at the **first character**.

---

### Right pointer

```java
int j = s.length() - 1;
```

`j` starts at the **last character**.

Example

```
amanaplanacanalpanama
↑                   ↑
i                   j
```

---

### Two-pointer loop

```java
while (i < j)
```

Loop continues until pointers **meet in the middle**.

---

### Compare characters

```java
if (s.charAt(i) != s.charAt(j))
```

Check if characters from both ends match.

If not equal → not a palindrome.

---

### Return false if mismatch

```java
return false;
```

Stops the program immediately.

---

### Move pointers

```java
i++;
j--;
```

Move toward the center.

```
i moves right
j moves left
```

---

### Final return

```java
return true;
```

If no mismatches were found, the string is a **palindrome**.

---

# 4️⃣ Dry Run (Step-by-Step)

### Input

```
s = "A man, a plan, a canal: Panama"
```

After cleaning:

```
amanaplanacanalpanama
```

---

# Dry Run Table

| Step  | i | j  | s[i] | s[j] | Comparison | Action        |
| ----- | - | -- | ---- | ---- | ---------- | ------------- |
| Start | 0 | 20 | a    | a    | match      | move pointers |
| 1     | 1 | 19 | m    | m    | match      | move pointers |
| 2     | 2 | 18 | a    | a    | match      | move pointers |
| 3     | 3 | 17 | n    | n    | match      | move pointers |
| 4     | 4 | 16 | a    | a    | match      | move pointers |
| 5     | 5 | 15 | p    | p    | match      | move pointers |
| 6     | 6 | 14 | l    | l    | match      | move pointers |
| 7     | 7 | 13 | a    | a    | match      | move pointers |
| 8     | 8 | 12 | n    | n    | match      | move pointers |
| 9     | 9 | 11 | a    | a    | match      | move pointers |

Pointers meet → palindrome.

---

# 5️⃣ Pointer Movement Visualization

Start

```
a m a n a p l a n a c a n a l p a n a m a
↑                                       ↑
i                                       j
```

After several steps

```
a m a n a p l a n a c a n a l p a n a m a
        ↑                       ↑
```

Eventually

```
a m a n a p l a n a c a n a l p a n a m a
              ↑           ↑
```

Pointers meet → **palindrome**.

---

# 6️⃣ Time Complexity

```
O(n)
```

We scan the string **once**.

---

# 7️⃣ Pattern Used

**Two Pointers Pattern**

One pointer from the start and one from the end comparing characters.

---

