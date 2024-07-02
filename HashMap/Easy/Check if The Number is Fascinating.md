# Intuition

To determine if a number is fascinating, we need to concatenate the number with its multiples (2 and 3) and then check if this concatenated string contains all digits from 1 to 9 exactly once, without any zeroes or repeated digits.

## Approach

1. **Concatenate Numbers**:
   - Convert `n`, `2n`, and `3n` to strings and concatenate them to form a single string.

2. **Check Digits**:
   - Use a boolean array `check` of size 10 to keep track of digits from 0 to 9.
   - Iterate through the concatenated string:
     - Convert each character to its corresponding digit.
     - If the digit is 0 or has already been seen, return `false`.
     - Mark the digit as seen in the `check` array.

3. **Verify All Digits**:
   - Iterate through the boolean array from index 1 to 9 to ensure each digit has been seen exactly once.

4. **Return Result**:
   - Return `true` if all conditions are met, otherwise return `false`.

## Complexity

- **Time Complexity**: O(1). The length of the concatenated string is always fixed (up to 9 digits), so the operations are constant time.

- **Space Complexity**: O(1). The space used by the boolean array is constant.

## Code

```Java
class Solution {
    public boolean isFascinating(int n) {
        boolean []check = new boolean[10];
        String temp = String.valueOf(n) + String.valueOf(2 * n) + String.valueOf(3 * n);
        int i;

        for (i = 0; i < temp.length(); i++) {
            int digit = temp.charAt(i) - '0';
            if (digit == 0 || check[digit]) {
                return false;
            }
            check[digit] = true;
        }

        for (i = 1; i <= 9; i++) {
            if (!check[i]) {
                return false;
            }
        }

        return true;
    }
}
```
