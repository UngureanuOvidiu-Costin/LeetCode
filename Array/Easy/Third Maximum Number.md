# Intuition

The problem requires finding the third maximum number in an array. If the third maximum does not exist, return the maximum number. Using a sorted data structure can help efficiently manage the unique elements and find the desired maximum.

## Approach

1. **Initialization**: Use a `SortedSet` to automatically sort and store unique elements from the array.

2. **Insertion**: Iterate through the array and insert each element into the `SortedSet`. This ensures all elements are unique and sorted.

3. **Check Size**: If the size of the set is less than 3, return the maximum element (the last element in the set).

4. **Find Third Maximum**: Otherwise, remove the largest element twice to get to the third maximum, then return the last remaining element in the set.

## Complexity

- **Time complexity**: O(n log n), where n is the length of the array. This is because each insertion into the `SortedSet` takes O(log n) time.

- **Space complexity**: O(n), where n is the length of the array. This is due to the space needed to store the elements in the set.

## Code

```Java
class Solution {
    public int thirdMax(int[] nums) {
        SortedSet<Integer> numsSet = new TreeSet<>();
        int i;

        for(i = 0; i < nums.length; i = i + 1) {
            numsSet.add(nums[i]);
        }

        if(numsSet.size() < 3){
            return numsSet.last();
        }

        numsSet.remove(numsSet.last());
        numsSet.remove(numsSet.last());
        return numsSet.last();
    }
}
```
