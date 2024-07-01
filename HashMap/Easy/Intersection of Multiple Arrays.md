# Intuition

The problem is to find the intersection of multiple arrays, the elements that are common to all the arrays. We can use a frequency map to count the occurrences of each element across all arrays, and then select the elements that appear in all arrays.

## Approach

1. **Frequency Map Construction:** Use a hash map to count the occurrences of each element across all arrays.
2. **Identify Common Elements:** Iterate over the frequency map and select the elements that appear in all arrays (the frequency is equal to the number of arrays).
3. **Sort and Return:** Sort the list of common elements and return it.

## Complexity

- Time complexity:
**Frequency Map Construction:** Building the frequency map involves iterating through all elements in the 2D array, which takes `O(n * m)` time, where n is the number of arrays and m is the average length of each array.
**Identify Common Elements:** Iterating over the frequency map takes `O(k)` time, where `k` is the number of unique elements across all arrays.
**Sorting:** Sorting the list of common elements takes `O(p * logp)` time, where `p` is the number of common elements.
**Total:** `O(n * m + p * logp)`

- Space complexity:
**Auxiliary Space:** The space required for the frequency map and the result list is `O(k)`, where `k` is the number of unique elements across all arrays.

## Code

```Java
class Solution {
    public List<Integer> intersection(int[][] nums) {
        HashMap<Integer, Integer> frequency = new HashMap<>();
        int i, j;

        for(i = 0; i < nums.length; i = i + 1) {
            for(j = 0; j < nums[i].length; j = j + 1) {
                frequency.put(nums[i][j], frequency.getOrDefault(nums[i][j], 0) + 1);
            }
        }

        List<Integer> commonNumbers = new ArrayList<>();
        for(Integer key: frequency.keySet()) {
            if(frequency.get(key) == nums.length){
                commonNumbers.add(key);
            }
        }

        Collections.sort(commonNumbers);

        return commonNumbers;
    }
}
```
