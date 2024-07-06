# Intuition

The problem requires removing duplicates from a sorted array in-place such that each unique element appears only once. This means we need to shift the elements to the left whenever a duplicate is found.

## Approach

1. **Initialization**: Check if the array is empty. If so, return 0.

2. **Index `k`**: Start with an index `k` at 1, which will track the position for the next unique element.

3. **Traversal**: Iterate through the array starting from the second element.

4. **Comparison**: For each element, compare it with the previous one.
   - If it is different from the previous element, place it at the position indicated by `k` and increment `k`.

5. **Return**: After processing all elements, `k` will be the length of the array with unique elements.

## Complexity

- **Time complexity**: O(n), where n is the length of the array. This is because we are traversing the array once.

- **Space complexity**: O(1), since we are not using any extra space proportional to the input size.

## Code

```Java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 0) 
            return 0;

        int k = 1;

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] != nums[i - 1]) {
                nums[k] = nums[i];
                k++;
            }
        }

        return k;
    }
}
```
