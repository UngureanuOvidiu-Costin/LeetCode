# Intuition

To find the maximum product of three numbers in an array, consider both the largest and the smallest numbers. The maximum product can either be the product of the three largest numbers or the product of the two smallest (most negative) numbers and the largest number.

## Approach

1. **Initialization**:
   - Initialize variables to store the three largest numbers (`maxA`, `maxB`, `maxC`) and the two smallest numbers (`minA`, `minB`).

2. **Traversal**:
   - Traverse through the array to update the largest and smallest values:
     - For each number, update the three largest values.
     - Similarly, update the two smallest values.

3. **Calculate Result**:
   - The maximum product can be either the product of the three largest numbers or the product of the two smallest numbers and the largest number.

4. **Return**:
   - Return the maximum of the two calculated products.

## Complexity

- **Time complexity**: O(n), where n is the length of the array. We traverse the array once.

- **Space complexity**: O(1), as we are using a constant amount of extra space.

## Code

```Java
class Solution {
    public int maximumProduct(int[] nums) {
        int maxA = Integer.MIN_VALUE, maxB = Integer.MIN_VALUE, maxC = Integer.MIN_VALUE;
        int minA = Integer.MAX_VALUE, minB = Integer.MAX_VALUE, minC = Integer.MIN_VALUE;
        int i;

        for (i = 0; i < nums.length; i = i + 1) {
            if (nums[i] > maxA) {
                maxC = maxB;
                maxB = maxA;
                maxA = nums[i];
            } else if (nums[i] > maxB) {
                maxC = maxB;
                maxB = nums[i];
            } else if (nums[i] > maxC)
                maxC = nums[i];

            if (nums[i] < minA)
            {
                minB = minA;
                minA = nums[i];
            } else if(nums[i] < minB)
                minB = nums[i];
            }

        return Math.max(minA * minB * maxA,
                maxA * maxB * maxC);

    }
}
```
