# Intuition

The problem requires sorting an array such that all even numbers come before all odd numbers. This can be efficiently achieved using two pointers to place even and odd numbers in their respective positions in a new array.

## Approach

1. **Initialization**: Create a new array `result` of the same length as the input array.

2. **Pointers**: Use two pointers, `evenIndex` starting from the beginning and `oddIndex` starting from the end of the `result` array.

3. **Traversal**: Iterate through the input array:
   - If the current number is even, place it at the position indicated by `evenIndex` and increment `evenIndex`.
   - If the current number is odd, place it at the position indicated by `oddIndex` and decrement `oddIndex`.

4. **Return**: After the traversal, return the `result` array.

## Complexity

- **Time complexity**: O(n), where n is the length of the array. We traverse the array once.

- **Space complexity**: O(n), since we are using an additional array of the same length as the input array.

## Code

```Java
class Solution {
    public int[] sortArrayByParity(int[] nums) {
        int[] result = new int[nums.length];
        int evenIndex = 0;
        int oddIndex = nums.length - 1;
        
        for (int num : nums) {
            if (num % 2 == 0) {
                result[evenIndex++] = num;
            } else {
                result[oddIndex--] = num;
            }
        }
        
        return result;
    }
}
```
