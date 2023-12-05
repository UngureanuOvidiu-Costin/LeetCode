# LeetCode Problem Writeup

## Problem Title: [Distribute Candies](https://leetcode.com/problems/distribute-candies/description/)

### Problem Description:

*You have a set of integers s, which originally contains all the numbers from 1 to n. Unfortunately, due to some error, one of the numbers in s got duplicated to another number in the set, which results in repetition of one number and loss of another number.
You are given an integer array nums representing the data status of this set after the error.
Find the number that occurs twice and the number that is missing and return them in the form of an array.*

### Approach:

**Frequency Map Initialization:**
Create a data structure to record the frequency or occurrence of elements.

**Finding the Duplicate:**
Iterate through the given data.
Update the frequency map.
Identify the first element with a frequency exceeding the expected count as the duplicate.

**Finding the Missing Element:**
Iterate through the frequency map.
Identify the first element with a frequency of 0 as the missing element.

**Result Generation:**
Create a container to hold the identified duplicate and missing elements.
Populate the container with the identified values.

**Return Result:**
Return the container or array containing the duplicate and missing elements.


### Pseudocode:

```
function findDuplicateAndMissing(data, dataSize, returnSize):
    // Initialize a data structure to track element frequencies
    frequencyMap = createEmptyMap()

    // Initialize variables for duplicate and missing elements
    duplicateElement = null
    missingElement = null

    // Iterate through the given data
    for i from 0 to dataSize - 1:
        // Update the frequency map
        frequencyMap[data[i]] = frequencyMap[data[i]] + 1

        // Identify duplicate element
        if frequencyMap[data[i]] == 2:
            duplicateElement = data[i]

    // Iterate through the frequency map
    for key in frequencyMap:
        // Identify missing element
        if frequencyMap[key] == 0:
            missingElement = key

    // Create a container for the result
    resultContainer = createEmptyContainer()

    // Store the duplicate and missing elements in the container
    resultContainer.add(duplicateElement)
    resultContainer.add(missingElement)

    // Update the returnSize variable
    returnSize = resultContainer.size()

    // Return the result container
    return resultContainer
```

## Code Implementation:

```
int* findErrorNums(int* nums, int numsSize, int* returnSize) {
    int* map = (int*)malloc(numsSize * sizeof(int));
    memset(map, 0, numsSize * sizeof(int));

    int dup = -1, missing = -1, i;

    for (i = 0; i < numsSize; i = i + 1) {
        map[nums[i] - 1] = map[nums[i] - 1] + 1;
        if (map[nums[i] - 1] == 2) {
            dup = nums[i];
        }
    }

    for (i = 0; i < numsSize; i = i + 1) {
        if (map[i] == 0) {
            missing = i + 1;
        }
    }

    int* result = (int*)malloc(2 * sizeof(int));
    result[0] = dup;
    result[1] = missing;

    *returnSize = 2;
    return result;
}
```

## Complexity Analysis:

### Time complexity Analysis:
The code iterates through the array once to build the frequency map (for loop).
It then iterates through the frequency map, which has at most numsSize elements (for loop).
Both iterations are separate, so the time complexity is O(numsSize) = O(n).

### Space Complexity Analysis:
The code uses additional space for the frequency map (map array) of size numsSize.
It also allocates space for the result array (result) of size 2.
Therefore, the space complexity is O(numsSize) for the frequency map and O(1) for the result array.
