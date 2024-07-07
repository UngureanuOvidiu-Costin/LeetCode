# Intuition

The problem requires finding all numbers in the range from 1 to n that do not appear in the input array. Using a set to track the numbers that are present in the array allows for an efficient lookup of the missing numbers.

## Approach

- **Initialization:**
  - Create a list result to store the missing numbers.
  - Use a Set to keep track of numbers that are present in the array.
  - Record Present Numbers:
  - Iterate through the array and add each element to the set.

- **Find Missing Numbers:**
  - Iterate through the numbers from 1 to n (inclusive) and check if each number is in the set.
  - If a number is not in the set, add it to the result list.

- **Return:**
  - Return the result list containing all the missing numbers.

## Complexity

- **Time complexity:** O(n), where n is the length of the array. We iterate through the array twice (once to populate the set and once to find missing numbers).

- **Space complexity:** O(n), where n is the length of the array. This is due to the space needed to store the elements in the set and the result list.

## Code

```Java
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        List<Integer> result = new ArrayList<>();
        Set<Integer> present = new HashSet<>();
        int i;

        for(i = 0; i < nums.length; i = i + 1) {
            present.add(nums[i]);
        }

        for(i = 1 ; i <= nums.length; i = i + 1) {
            if(!present.contains(i)) {
                result.add(i);
            }
        }

        return result;
    }
}
```
