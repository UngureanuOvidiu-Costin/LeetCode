# Two Sum Problem - Java Solution
Problem Statement:
Given an array of integers nums and an integer target, the task is to find and return the indices of two numbers in the array such that their sum equals the target. 
It is assumed that each input has exactly one solution, and the same element cannot be used twice.

## Approach:
To solve this problem efficiently, we can use a HashMap to store the elements of the array along with their indices. 
The idea is to iterate through the array and, for each element, check if its complement (the difference between the target and the current element) exists in the HashMap. 
If it does, we have found the pair, and we can return their indices. If not, we add the current element and its index to the HashMap for future reference.

```ruby
class Solution {
    public static int[] twoSum(int[] nums, int target) {
        // Create a HashMap to store the indices of numbers
        HashMap<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];

            // Check if the complement exists in the map
            if (map.containsKey(complement)) {
                // Return the indices of the two numbers
                return new int[]{map.get(complement), i};
            }

            // Add the current number and its index to the map
            map.put(nums[i], i);
        }

        // No solution found, return an empty array
        return new int[]{};
    }
}
```
# Explanation:
1.The twoSum method takes an array of integers (nums) and an integer (target) as input.

2.It uses a HashMap (map) to store the elements of the array and their corresponding indices.

3.The method iterates through the array, calculating the complement for each element.

4.If the complement exists in the HashMap, the method returns the indices of the two numbers.

5.If the complement is not found, the current element and its index are added to the HashMap.


# Time Complexity:
The time complexity of the solution is O(n), where 'n' is the number of elements in the input array nums.

The for loop iterates through each element in the array exactly once, and each iteration involves constant-time operations.
The HashMap operations, such as containsKey and put, have an average time complexity of O(1) under normal circumstances. In the worst case, it can be O(n), but this is unlikely to happen frequently.
As a result, the overall time complexity is dominated by the single pass through the array, making it **O(n)**.

# Space Complexity:
The space complexity of the solution is O(n), where 'n' is the number of elements in the input array nums.

The HashMap (map) can potentially store all 'n' elements of the array in the worst case, where each element is unique.
In addition to the HashMap, the solution uses a constant amount of extra space for variables like complement, i, and result array.

