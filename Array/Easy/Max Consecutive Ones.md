# Intuition

The problem requires finding the maximum streak of consecutive `1`s in a binary array. A straightforward approach involves iterating through the array while counting the consecutive `1`s and keeping track of the maximum count observed.

## Approach

1. **Initialize Variables**:
   - `nr` to count the current number of consecutive `1`s.
   - `max` to store the maximum number of consecutive `1`s encountered.

2. **Iterate Through the Array**:
   - Use a loop to traverse the array.
   - Increment `nr` if the current element is `1`.
   - Reset `nr` to `0` if the current element is `0`.
   - After updating `nr`, update `max` if `nr` exceeds the current `max`.

3. **Return Result**:
   - Return the value of `max` which represents the maximum number of consecutive `1`s.

## Complexity

- **Time Complexity**: O(n), where `n` is the length of the array `nums`. The array is traversed once.

- **Space Complexity**: O(1), as only a fixed amount of extra space is used.

## Code

```Java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int nr = 0, max = 0;
        int i;

        for(i = 0; i < nums.length; i = i + 1) {
            if(nums[i] == 1){
                nr++;
            }else {
                nr = 0;
            }
            
            if(nr > max){
                max = nr;
            }
        }

        return max;
    }
}
```
