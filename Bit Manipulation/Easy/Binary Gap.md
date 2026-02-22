# Intuition
The problem asks us to find **the longest distance between two adjacent 1's** in the binary representation of a number.  
We can solve this by iterating though the bits of the number, keeping track of the positions of 1's, and computing the distances between them.

# Approach

1. Initialize `result = 0` to store the maximum gap, `temp = 0` to count zeros, and `foundOne = false` to track if we have seen the first 1.
2. Iterate through each bit of `n` using a right shift `(n >>= 1)`:
- If the current bit is 1:
    - If we have already seen a `1`, update result with `max(result, temp + 1)`.
    - Reset `temp = 0` and set `foundOne = true`.
- If the current bit is `0` and `foundOne` is `true`, increment `temp`.
3. Return `result` after processing all bits.

# Complexity
- Time complexity:
    - `O(1)` because the number of bits in an integer is fixed (32 bits), so the loop executes a constant number of times.

- Space complexity:
    - `O(1)` as the solution is using only a few integer and boolean variables:`result`, `temp`, `foundOne`.

# Code
```java []
class Solution {

    public int binaryGap(int n) {
        if(Integer.bitCount(n) == 1){
            return 0;
        }

        int result = 0;
        int temp = 0;
        boolean foundOne = false;

        while(n > 0){
            if(n & 1 != 0){
                if(foundOne){
                    result = Math.max(result, temp + 1);
                }
                temp = 0;
                foundOne = true;
            } else {
                if(foundOne){
                    temp++;
                }
            }
            n = n >> 1;
        }

        return result;
    }
}
```
