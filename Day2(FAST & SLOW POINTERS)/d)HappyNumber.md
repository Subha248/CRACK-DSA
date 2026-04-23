
https://leetcode.com/problems/happy-number/   

#202 leetoce
---

# 1️⃣ Question

**Happy Number Problem**

A number is called **happy** if:

1. Take the number
2. Replace it with the **sum of the squares of its digits**
3. Repeat the process
4. If the number eventually becomes **1 → Happy Number**
5. If the numbers start repeating in a **cycle → Not Happy**

Example:

```
7 → 49 → 97 → 130 → 10 → 1
```

Since it reaches **1**, **7 is a happy number**.

---

# 2️⃣ Full Code

```java
class Solution {

    public int square(int num){
        int ans = 0;

        while(num > 0){
            int digit = num % 10;
            ans += digit * digit;
            num = num / 10;
        }

        return ans;
    }

    public boolean isHappy(int n){

        int slow = n;
        int fast = n;

        do{
            slow = square(slow);
            fast = square(square(fast));
        }
        while(slow != fast);

        return slow == 1;
    }
}
```

---

# 3️⃣ Line-by-Line Explanation

### Function 1

```
public int square(int num)
```

Creates a function that **returns the sum of squares of digits**.

Example:

```
square(49)
```

Result:

```
4² + 9² = 97
```

---

```
int ans = 0;
```

Variable to **store the total sum**.

Example start:

```
ans = 0
```

---

```
while(num > 0)
```

Loop until all digits are processed.

Example:

```
num = 49
```

---

```
int digit = num % 10;
```

Gets the **last digit**.

Example:

```
49 % 10 = 9
```

---

```
ans += digit * digit;
```

Squares the digit and **adds it to ans**.

Example:

```
ans = 0 + 9²
ans = 81
```

---

```
num = num / 10;
```

Removes the **last digit**.

Example:

```
49 / 10 = 4
```

Now number becomes **4**.

---

```
return ans;
```

Returns the total.

Example:

```
square(49) = 97
```

---

# Main Function

```
public boolean isHappy(int n)
```

Checks whether the number is **happy or not**.

---

```
int slow = n;
int fast = n;
```

Two pointers start at the same number.

Example:

```
n = 7

slow = 7
fast = 7
```

---

```
do{
```

Start loop.

The loop will **repeat until slow and fast meet**.

---

```
slow = square(slow);
```

Slow pointer moves **one step**.

Example:

```
7 → 49
```

---

```
fast = square(square(fast));
```

Fast pointer moves **two steps**.

Example:

```
7 → 49 → 97
```

---

```
while(slow != fast);
```

Keep repeating until both numbers become the same.

---

```
return slow == 1;
```

If the meeting point is **1 → Happy number**.

Otherwise **not happy**.

---

# 4️⃣ Dry Run (Example: n = 7)

Initial values

| Step  | slow | fast |
| ----- | ---- | ---- |
| Start | 7    | 7    |

---

## Iteration 1

Slow moves one step

```
slow = square(7)
7² = 49
```

Fast moves two steps

```
square(7) = 49
square(49) = 97
```

| Step | slow | fast |
| ---- | ---- | ---- |
| 1    | 49   | 97   |

---

## Iteration 2

Slow

```
square(49)
4² + 9² = 97
```

Fast

```
square(97) = 130
square(130) = 10
```

| Step | slow | fast |
| ---- | ---- | ---- |
| 2    | 97   | 10   |

---

## Iteration 3

Slow

```
square(97)
9² + 7² = 130
```

Fast

```
square(10) = 1
square(1) = 1
```

| Step | slow | fast |
| ---- | ---- | ---- |
| 3    | 130  | 1    |

---

## Iteration 4

Slow

```
square(130)
1² + 3² + 0² = 10
```

Fast

```
square(1) = 1
square(1) = 1
```

| Step | slow | fast |
| ---- | ---- | ---- |
| 4    | 10   | 1    |

---

## Iteration 5

Slow

```
square(10)
1² + 0² = 1
```

Fast

```
square(1) = 1
square(1) = 1
```

| Step | slow | fast |
| ---- | ---- | ---- |
| 5    | 1    | 1    |

Now

```
slow == fast
```

Loop stops.

---

# Final check

```
return slow == 1
```

```
1 == 1 → true
```

So

```
7 is a happy number
```

---

