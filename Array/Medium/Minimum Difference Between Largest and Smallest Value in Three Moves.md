# Intuition

When we need to minimize the difference between the maximum and minimum values after removing three elements, we can think about the sorted order of the elements. Removing the smallest three or the largest three might give the most significant reduction in the difference.

## Approach

1. **Edge Case**: If the length of `nums` is less than or equal to 3, we can remove all elements, and the result is 0.

2. **Sort the Array**: Sorting the array allows us to easily consider the possible elements to remove that would minimize the difference.

3. **Calculate Possible Cases**:
   - `case1`: Remove the first three elements, and calculate the difference between the maximum and minimum of the remaining elements.
   - `case2`: Remove the smallest two elements and the largest element.
   - `case3`: Remove the smallest element and the largest two elements.
   - `case4`: Remove the largest three elements.

4. **Find Minimum Difference**:
   - Compute the difference for each case.
   - Return the minimum of these differences.

## Complexity

- **Time Complexity**: O(n log n), where `n` is the number of elements in `nums`, due to sorting the array.

- **Space Complexity**: O(1), as the additional space used is constant.

## Code

```Java
class Solution {
    public int minDifference(int[] nums) {
        int case1, case2, case3, case4, n = nums.length;

        if(n <= 3){
            return 0;
        }

        Arrays.sort(nums);
        case1 = nums[n - 1] - nums[3];
        case2 = nums[n - 2] - nums[2];
        case3 = nums[n - 3] - nums[1];
        case4 = nums[n - 4] - nums[0];

        return Math.min(Math.min(case1, case2), Math.min(case3, case4));
    }
}
```
