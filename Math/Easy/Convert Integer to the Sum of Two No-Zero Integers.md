# Intuition
The problem asks us to split a given integer `n` into two positive integers `a` and `b` such that:
1. `a + b = n`
2. Neither `a` nor `b` contains the digit `0`.

A SIMPLE way to SOLVE this is to try pairs of numbers `(a, b)` where `a` increases from `1` upwards and `b = n - a`. By checking each pair, we can quickly find a valid combination since the search space is limited.

---

# Approach
1. **Initialize a result array** of size 2, which will store `a` and `b`.
2. **Iterate `i` from `1` to `n/2`** (since beyond `n/2` we would just repeat earlier pairs but swapped).
   - For each `i`, let:
     - `a = i`
     - `b = n - i`
3. **Check validity**: For each candidate pair `(a, b)`:
   - Ensure both `a` and `b` do not contain the digit `0`.
   - This is done by repeatedly checking each digit of the number.
4. **Return the result** once a valid pair is found.

Since the problem guarantees a solution, we will always return before finishing the loop.

---

# Complexity
- **Time Complexity**:
  - Iterating through up to `n/2` pairs costs `O(n)`.
  - Checking digits of `a` and `b` is at most `O(log₁₀(n))`, but since $n <= 10^⁴$, this is effectively constant.
  - **Overall: `O(n)`**

- **Space Complexity**:
  - We only use a fixed array of size 2 and a few integer variables, which means constant space.
  - **Overall: `O(1)`**

---

# Code
```java
class Solution {
    public int[] getNoZeroIntegers(int n) {
        int[] result = new int[2];

        for (int i = 1; i <= n / 2; i++) {
            int a = i;
            int b = n - i;
            if (isNoZeroInteger(a) && isNoZeroInteger(b)) {
                result[0] = a;
                result[1] = b;
                return result;
            }
        }

        return result;
    }

    private boolean isNoZeroInteger(int n) {
        while (n > 0) { 
            if (n % 10 == 0) {
                return false;
            }
            n /= 10;
        }
        return true;
    }
}
