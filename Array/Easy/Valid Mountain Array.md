# Intuition

A valid mountain array must start with a strictly increasing sequence, reach a peak, and then be followed by a strictly decreasing sequence. The array must have at least three elements.

## Approach

1. **Initial Check**: If the array has fewer than three elements, it cannot form a mountain, so return `false`.

2. **First Iteration**: Traverse the array to find the peak:
   - If any adjacent elements are equal, return `false` since the sequence must be strictly increasing or decreasing.
   - If we find a peak (an element greater than the next one), mark it and break out of the loop.

3. **Peak Check**: Ensure the peak is neither the first nor the last element of the array.

4. **Second Iteration**: Continue from the peak to the end of the array:
   - If any element is not part of a strictly decreasing sequence, return `false`.

5. **Final Check**: If we successfully traverse to the end while meeting all conditions, return `true`. Otherwise, return `false`.

## Complexity

- **Time complexity**: O(n), where n is the length of the array. We traverse the array at most twice.

- **Space complexity**: O(1), since we use a constant amount of extra space.

## Code

```Java
class Solution {
    public boolean validMountainArray(int[] arr) {
        if(arr.length < 3) {
            return false;
        }

        int i, j;
        boolean upside = false;

        for(i = 0; i < arr.length - 1; i = i + 1) {
            if(arr[i] == arr[i + 1]) {
                return false;
            }

            if(arr[i] > arr[i + 1]){
                upside = true;
                break;
            }
        }

        if(i == arr.length - 1 || i == 0) {
            return false;
        }

        for(j = i; j < arr.length - 1; j = j + 1) {

            if(arr[j] < arr[j + 1] || arr[j] == arr[j + 1]) {
                return false;
            }
        }

        if(j == arr.length - 1){
            return true & upside;
        }

        return false;
    }
}
```
