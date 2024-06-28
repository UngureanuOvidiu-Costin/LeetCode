# Intuition

The problem is to count the number of pairs `(i, j)` such that `nums1[i]` is divisible by `nums2[j] * k`. This requires iterating through all possible pairs of elements from `nums1` and `nums2` and checking the given condition.

## Approach

1. **Brute Force:** Use a nested loop to iterate through all pairs `(i, j)` where `i` ranges over the length of `nums1` and `j` ranges over the length of `nums2`.
2. **Condition Check:** For each pair `(i, j)`, check if `nums1[i] % (nums2[j] * k) == 0`.
3. **Count Pairs:** Increment a counter for each pair that satisfies the condition.
4. **Return Result:** Return the counter as the final result.

## Complexity

- Time complexity:
**Nested Loops:** The outer loop runs `n` times and the inner loop runs `m` times, where `n` is the length of `nums1` and `m` is the length of `nums2`. This results in a time complexity of `O(n × m)`.
**Condition Check:** The condition check inside the inner loop is `O(1)`.

- Space complexity:
**Auxiliary Space:** Only a few integer variables `(result, i, j)` are used, which is `O(1)` space.

## Code

```Java
class Solution {
    public int numberOfPairs(int[] nums1, int[] nums2, int k) {
        int i, j, result = 0;

        for(i = 0; i < nums1.length; i = i + 1) {
            for(j = 0; j < nums2.length; j = j + 1) {
                if(nums1[i] % (nums2[j] * k) == 0){
                    result++;
                }
            }
        }

        return result;
    }
}
```
