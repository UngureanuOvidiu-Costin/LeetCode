# LeetCode Problem Writeup

## Problem Title: [How Many Numbers Are Smaller Than the Current Number](https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/description/)

### Problem Description:
Given the array nums, for each nums[i] find out how many numbers in the array are smaller than it. That is, for each nums[i] you have to count the number of valid j's such that j != i and nums[j] < nums[i].<br>
Return the answer in an array.

### Approach:
1. Create a HashMap to Store Counts:<br>
Start by creating a HashMap to store the count of each unique number in the array.
2. Clone and Sort the Array:<br>
Clone the original array to avoid modifying it. Sort the cloned array in ascending order. Sorting will help in determining the count of smaller numbers for each element efficiently.
3. Populate the CountMap:<br>
Iterate through the sorted array and populate the count of each unique number in the HashMap. The idea is to map each number to its count in the sorted array.
4. Create Result Array:<br>
Iterate through the original array, and for each element, look up its count in the HashMap. This count represents the number of elements smaller than the current element.


### Pseudocode:

```plaintext
function countSmallerNumbers(nums):
    // Step 1: Create a HashMap to store counts
    countMap = new HashMap()

    // Step 2: Clone and sort the array
    sortedNums = clone(nums)
    sort(sortedNums)

    // Step 3: Populate the countMap
    for i from 0 to length(sortedNums) - 1:
        countMap.putIfAbsent(sortedNums[i], i)

    // Step 4: Create result array
    result = new Array(length(nums))

    // Step 5: Populate result array
    for i from 0 to length(nums) - 1:
        result[i] = countMap.get(nums[i])

    // Step 6: Return the result array
    return result
```

## Code Implementation:

```
class Solution {
    public int[] smallerNumbersThanCurrent(int[] nums) {

        HashMap<Integer, Integer> countMap = new HashMap<>();        
        int[] clonedArray = nums.clone();
        Arrays.sort(clonedArray);

        for (int i = 0; i < clonedArray.length; i++) {
            countMap.putIfAbsent(clonedArray[i], i);
        }
        
        int[] result = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            result[i] = countMap.get(nums[i]);
        }
        
        return result;
    }
}
```

## Complexity Analysis:
![image](https://github.com/UngureanuOvidiu-Costin/LeetCode/assets/102877918/46d17d8a-bc0d-4e02-b8b1-49d1713c9ea0)

**Time Complexity:**<br>
1. Cloning the array (nums.clone()):<br>
Time Complexity: O(n), where n is the length of the array.<br>
2. Sorting the cloned array (Arrays.sort(clonedArray)):<br>
Time Complexity: O(n log n), where n is the length of the array. This is the time complexity of the sorting algorithm (usually quicksort in Java).<br>
3. Populating the countMap in the first loop:<br>
Time Complexity: O(n), where n is the length of the array. Each element is processed once.<br>
4. Populating the result array in the second loop:<br>
Time Complexity: O(n), where n is the length of the array. Each element is processed once.
The dominant factor is the sorting operation, so the overall time complexity is O(n log n).

**Space Complexity:**
1. HashMap (countMap):<br>
Space Complexity: O(n), where n is the number of unique elements in the array. In the worst case, all elements are unique, and the countMap stores each of them.
2. Cloned Array (clonedArray):<br>
Space Complexity: O(n), where n is the length of the array. The cloned array requires additional space.
3. Result Array (result):<br>
Space Complexity: O(n), where n is the length of the array. The result array stores the output.
