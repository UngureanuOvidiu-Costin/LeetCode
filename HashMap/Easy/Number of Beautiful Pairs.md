# Intuition

A pair of numbers is beautiful if the GCD of the first digit of one number and the last digit of another number is 1. This requires iterating through all pairs and computing their first and last digits and then checking their GCD.

## Approach

1. **Initialize Count**:
   - Use a variable `count` to keep track of the number of beautiful pairs.

2. **Iterate Through Pairs**:
   - Use a nested loop to iterate through all pairs `(i, j)` where `i < j`.
   - For each number `nums[i]`, determine its first digit using a helper function `getFirstDigit`.
   - For each number `nums[j]`, determine its last digit by computing `nums[j] % 10`.

3. **Check GCD**:
   - Use a helper function `gcd` to check if the GCD of the first digit of `nums[i]` and the last digit of `nums[j]` is 1.
   - If the GCD is 1, increment the `count`.

4. **Return Result**:
   - Return the count of beautiful pairs.

## Complexity

- **Time Complexity**: O(n^2), where `n` is the number of elements in `nums`. This is due to the nested loop iterating through all pairs.

- **Space Complexity**: O(1), as only a fixed amount of extra space is used.

## Code

```Java
class Solution {
    public int countBeautifulPairs(int[] nums) {
        int n = nums.length;
        int count = 0;

        for (int i = 0; i < n; i++) {
            int firstDigit = getFirstDigit(nums[i]);
            for (int j = i + 1; j < n; j++) {
                int lastDigit = nums[j] % 10;
                if (gcd(firstDigit, lastDigit) == 1) {
                    count++;
                }
            }
        }

        return count;
    }

    int gcd(int a, int b) {
        if (b == 0) {
            return a;
        }
        return gcd(b, a % b);
    }

    int getFirstDigit(int num) {
        while (num >= 10) {
            num /= 10;
        }
        return num;
    }
}
```
