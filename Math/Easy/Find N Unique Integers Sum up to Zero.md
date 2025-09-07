# Intuition
To generate `N` integers that sum to zero, we can use pairs of numbers `(a, -a)`, which cancel each other.
If `N` is odd, we also include `0` since it does not affect the sum.

# Approach
1. Allocate an array `result` of size `N`.
2. Use `i` to iterate from 0 to `N / 2`. We do this in order to gain CPU time.
3. Insert `i + 1` and `- (i + 1)`.
4. If `N` is odd, we also add `0` to the array.
5. Return the array.

# Complexity
- Time complexity:
    - Allocating the array is $O(N)$
    - To iterate from `[0, N / 2)` takes $O(N/2)$ which is $O(N)$
        - Inserting `a` and `-a` into the array is 2 * $O(1)$ = $O(1)$
    - Checking if N is odd or not in order to insert `0` is $O(1)$
    - Final result $O(N)$

- Space complexity:
    - Allocating the array takes $O(N)$
    - Index and remainder take $O(1)$
    - Final result $O(N)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```java []
class Solution {
    public int[] sumZero(int n) {
        int[] result = new int[n];
        int i;

        // Inserting the pair (a, -a)
        for(i = 0; i < n / 2; i = i + 1) {
            result[i] = i + 1;
            result[i + n / 2] = - (i + 1);
        }

        // If N is odd, add 0
        if(n % 2 != 0){
            result[n - 1] = 0;
        }

        return result;
    }
}
```
