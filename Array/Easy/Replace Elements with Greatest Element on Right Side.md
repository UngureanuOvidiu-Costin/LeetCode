# Intuition

The problem requires replacing each element in the array with the greatest element among the elements to its right, and the last element with `-1`. This can be efficiently done with a nested loop approach.

## Approach

1. **Edge Case**: If the array has only one element, return `[-1]`.

2. **Outer Loop**: Traverse each element in the array except the last one.
   - Initialize `max` to `-1` for each element.

3. **Inner Loop**: For each element, traverse all elements to its right to find the maximum.
   - Update `max` if a larger element is found.
   - Assign this `max` value to the current element.

4. **Final Step**: Set the last element of the array to `-1`.

5. **Return**: Return the modified array.

## Complexity

- **Time complexity**: O(n^2), where n is the length of the array. The nested loops result in quadratic time complexity.

- **Space complexity**: O(1), since we are modifying the array in-place and using a constant amount of extra space.

## Code

```Java
class Solution {
    public int[] replaceElements(int[] arr) {
        if(arr.length == 1){
            return new int[]{-1};
        }

        int i, j, max;
        for(i = 0; i < arr.length - 1; i = i + 1){
            max = -1;
            for(j = i + 1; j < arr.length; j = j + 1) {
                if(arr[j] > max) {
                    max = arr[j];
                }
            }

            arr[i] = max;
        }

        arr[arr.length - 1] = -1;
        return arr;
    }
}
```
