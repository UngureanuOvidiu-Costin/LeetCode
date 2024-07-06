# Intuition

The problem is to remove all occurrences of `val` from the array `nums` and return the new length of the array. This should be done in-place, meaning no additional array should be used for storing elements. The goal is to shift elements that are not equal to `val` to the front of the array.

## Approach

1. **Initialize a Pointer**:
   - Use a pointer `k` initialized to 0. This pointer will indicate the position to place the next element that is not equal to `val`.

2. **Iterate Over the Array**:
   - Loop through the elements of the array `nums`.
   - For each element, if it is not equal to `val`, place it in the position indicated by `k` and increment `k`.

3. **Return the Result**:
   - After the loop, `k` will be the count of elements that are not equal to `val` and will also represent the new length of the array.

## Complexity

- **Time Complexity**: O(n), where n is the length of the array. We are making a single pass over the array.

- **Space Complexity**: O(1), as we are using a constant amount of extra space.

## Code

```Java
class Solution {
    public int removeElement(int[] nums, int val) {
        int i;
        int k = 0;

        if(nums.length == 1){
            if(nums[0] == val){
                return 0;
            }else{
                return 1;
            }
        }
        
        for(i = 0; i < nums.length; i = i + 1) {
            if(nums[i] != val) {
                nums[k] = nums[i];
                k++;
            }
        }
        return k;
    }
}
```
