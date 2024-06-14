

# LeetCode Problem Writeup

## Problem Title: [Number of Good Pairs](https://leetcode.com/problems/number-of-good-pairs/description/)

### Problem Description:

*Given an array of integers nums, return the number of good pairs.
A pair (i, j) is called good if nums[i] == nums[j] and i < j.*


### Pseudocode:

```plaintext
function numIdenticalPairs(nums):
    countMap = createEmptyHashMap
    goodPairsCount = 0
    
    for num in nums:
        count = getCountFromHashMap(countMap, num)
        goodPairsCount += count
        incrementCountInHashMap(countMap, num)

    return goodPairsCount

function getCountFromHashMap(map, key):
    if key is in map:
        return map[key]
    else:
        return 0

function incrementCountInHashMap(map, key):
    count = getCountFromHashMap(map, key)
    map[key] = count + 1
```

## Code Implementation:
```
class Solution {
    public int numIdenticalPairs(int[] nums) {
        HashMap<Integer, Integer> countMap = new HashMap<>();
        int goodPairsCount = 0;

        for (int num : nums) {
            int count = countMap.getOrDefault(num, 0);
            goodPairsCount += count;
            countMap.put(num, count + 1);
        }

        return goodPairsCount;
    }
}
```

## Complexity Analysis:
![image](https://github.com/UngureanuOvidiu-Costin/LeetCode/assets/102877918/e8c88a32-692e-43c3-b4ce-bbd611840d73)

**Time Complexity:** <br>
**For Loop:** The main loop iterates through each element in the nums array once. Therefore, the time complexity of the loop is O(n), where n is the length of the array.<br>
**Space Complexity:** <br>
**HashMap (countMap):** The space complexity is influenced by the HashMap used to store the counts of each number in the array. In the worst case, all distinct elements in the array will be stored in the HashMap. Therefore, the space complexity is O(n), where n is the number of elements in the array.
