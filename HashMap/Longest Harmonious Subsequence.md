# LeetCode Problem Writeup

## Problem Title: [Longest Harmonious Subsequence](https://leetcode.com/problems/longest-harmonious-subsequence/description/)

### Problem Description:

*We define a harmonious array as an array where the difference between its maximum value and its minimum value is exactly 1.
Given an integer array nums, return the length of its longest harmonious subsequence among all its possible subsequences.
A subsequence of array is a sequence that can be derived from the array by deleting some or no elements without changing the order of the remaining elements.*

### Approach:

**Frequency Counting:**<br />
Count the frequency of each element using a HashMap.<br />
**Calculate Harmonious Subsequence Length:**<br />
For each unique element in the array, check if the element with a difference of 1 exists in the HashMap.
If it exists, calculate the length of the harmonious subsequence by adding the frequencies of the current element and its adjacent element.
**Update Maximum Length:**<br />
Keep track of the maximum length encountered during the iterations.<br />
**Return Result:**<br />
After iterating through all possible pairs, return the maximum length as the result.

### Pseudocode:

```plaintext
function findLHS(nums):
    occurence = createHashMap()

    maxLen = 0

    // Step 1: Frequency Counting
    for i from 0 to length of nums - 1:
        occurence[nums[i]] = occurence.getOrDefault(nums[i], 0) + 1

    // Step 2: Check Harmonious Subsequences
    for key in keys of occurence:
        if occurence.containsKey(key + 1):
            // Step 3: Calculate Length of Harmonious Subsequence
            len = occurence[key] + occurence[key + 1]

            // Step 4: Update Maximum Length
            maxLen = max(maxLen, len)

    // Step 5: Return Result
    return maxLen
```

## Code Implementation:
```
class Solution {
    public int findLHS(int[] nums) {
        HashMap<Integer, Integer> occurence = new HashMap<>();


        int i, maxLen = 0, len;
        for(i = 0; i < nums.length; i = i + 1){
            occurence.put(nums[i], occurence.getOrDefault(nums[i], 0) + 1);
        }

        for(int key : occurence.keySet()){
            if(occurence.containsKey(key+1)){
                len = occurence.get(key) + occurence.get(key + 1);
                maxLen = Math.max(maxLen, len);
            }
        }

        return maxLen;
    }
}
```

## Complexity Analysis:

**Time Complexity:** <br />
Frequency Counting (First Loop):
The first loop iterates through each element of the nums array, and for each element, it updates the frequency in the occurence HashMap.
The time complexity of this loop is O(n), where n is the length of the nums array.
Check Harmonious Subsequences (Second Loop):
The second loop iterates through the keys of the occurence HashMap.
In the worst case, each key is examined once, and the check for the existence of key + 1 is constant time.
Therefore, the time complexity of this loop is O(m), where m is the number of unique elements in the nums array.

**Space Complexity:** <br />
HashMap (occurence):<br />
The space complexity is driven by the space required for the occurence HashMap.
In the worst case, all elements of the nums array are unique, and the HashMap stores each element with its frequency.
Therefore, the space complexity is O(n), where n is the length of the nums array.<br />

**Other Variables:** <br />
The algorithm uses a constant amount of additional space for variables like i, maxLen, len, and key.
These variables do not depend on the input size, so they don't contribute to the overall space complexity.
Overall, the space complexity is O(n) due to the HashMap.
