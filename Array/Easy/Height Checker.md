# Intuition

The problem requires counting the number of indices where the elements in the given array `heights` do not match the elements in a sorted version of the array. This can be done by comparing the original array to its sorted version.

## Approach

1. **Initialization**:
   - Create a copy of the `heights` array and sort it.

2. **Comparison**:
   - Iterate through the original and the sorted arrays simultaneously.
   - Count the number of indices where the elements differ.

3. **Return**:
   - The count of differing indices, which represents the number of students not standing in their correct positions.

## Complexity

- **Time complexity**: O(n log n), where n is the length of the array. This is due to the sorting step.

- **Space complexity**: O(n), where n is the length of the array. This is due to the space needed to store the sorted copy of the array.

```Java
class Solution {
    public int heightChecker(int[] heights) {
        int i, result = 0;
        
        int[] sortedHeights = Arrays.copyOf(heights, heights.length);
        Arrays.sort(sortedHeights);
    
        for(i = 0; i < heights.length; i = i + 1) {
            if(heights[i] != sortedHeights[i]) {
                result = result + 1;
            }
        }
        
        return result;
    }
}
