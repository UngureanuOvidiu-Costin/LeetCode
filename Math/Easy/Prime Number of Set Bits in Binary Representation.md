# Intuition

A straightforward solution is to iterate through every number in the interval `[left, right]`, count the number of bits set to `1` in its binary representation, and check whether that count is a prime number.

Instead of checking if the number of set bits is prime repeatedly, we can optimize the solution by leveraging the problem constraints.

# Approach

## Observations

- Constraints:
  - `1 <= left <= right <= 10^6`
  - `0 <= right - left <= 10^4`

- The maximum value of `right` is `10^6`.
- The number of bits required to represent `10^6` in binary is:

  ```
  floor(log2(10^6)) + 1 ≈ 20
  ```

- Therefore, the number of set bits (`1`s) for any number in this range is:

  ```
  0 <= setBits <= 20
  ```

- The prime numbers within this interval are:

  ```
  2, 3, 5, 7, 11, 13, 17, 19
  ```

Since this set is small and fixed, we can store these values in a `Set` for constant-time lookup.

## Algorithm Steps

1. Initialize a variable to store the result:
   ```java
   int result = 0;
   ```

2. Store the possible prime bit counts:
   ```java
   Set<Integer> primeBits = Set.of(2, 3, 5, 7, 11, 13, 17, 19);
   ```

3. Iterate from `left` to `right`.

4. For each number:
   - Count the number of set bits:
     ```java
     int count = Integer.bitCount(x);
     ```
   - If `count` exists in `primeBits`, increment `result`.

5. Return `result`.

# Complexity

## Time Complexity

- Total time complexity is: `O(right - left + 1)` multiplied with `O(log number)`
- We iterate through `right - left + 1` numbers which results in `O(right - left)`.
- Counting bits takes `O(log number)`, but since integers are bounded (at most 20 bits here), it is effectively `O(1)`.

Final time complexity:

```
O(right - left)
```

## Space Complexity

- `primeBits` contains a constant number of elements → `O(1)`
- Other variables (`primeBits`, `result`, `x`) use constant space → `O(1)`

Final space complexity:

```
O(1)
```

# Code

```java
class Solution {

    private static final Set<Integer> primeBits =
        Set.of(2, 3, 5, 7, 11, 13, 17, 19);

    public int countPrimeSetBits(int left, int right) {
        int result = 0;
        int x;
        for (x = left; x <= right; x++) {
            if (primeBits.contains(Integer.bitCount(x))) {
                result++;
            }
        }

        return result;
    }
}
```
