# LeetCode Problem Writeup

## Problem Title: [Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/description/)

### Problem Description:

*The next greater element of some element x in an array is the first greater element that is to the right of x in the same array.
You are given two distinct 0-indexed integer arrays nums1 and nums2, where nums1 is a subset of nums2.
For each 0 <= i < nums1.length, find the index j such that nums1[i] == nums2[j] and determine the next greater element of nums2[j] in nums2. If there is no next greater element, then the answer for this query is -1.
Return an array ans of length nums1.length such that ans[i] is the next greater element as described above.*

### Approach:

*The problem involves finding the next greater element for each element in nums1 within the context of nums2. We can efficiently solve this problem using a stack to keep track of potential next greater elements and a hashmap to store the associations between elements and their next greater elements.*

### Pseudocode:

```Python3
function nextGreaterElement(nums1, nums2):
    // Step 1
    stack = empty stack
    nextGreater = empty hashmap
    
    // Step 2
    for num in nums2:
        while stack is not empty and num > stack.top():
            nextGreater[stack.pop()] = num
        stack.push(num)
    
    // Step 3
    while stack is not empty:
        nextGreater[stack.pop()] = -1
    
    // Step 4
    result = []
    for num1 in nums1:
        result.push(nextGreater[num1])
    
    // Step 5
    return result
```

## Code Implementation:

```Java
class Solution {
    public static int[] nextGreaterElement(int[] nums1, int[] nums2) {
        Map<Integer, Integer> nextGreater = new HashMap<>();
        Deque<Integer> stack = new ArrayDeque<>();
        int[] result = new int[nums1.length];

        // Traverse nums2 to find the next greater element for each element
        for (int num : nums2) {
            while (!stack.isEmpty() && stack.peek() < num) {
                nextGreater.put(stack.pop(), num);
            }
            stack.push(num);
        }

        // For elements without a next greater element, set the value to -1
        while (!stack.isEmpty()) {
            nextGreater.put(stack.pop(), -1);
        }

        // Build the result array using the map
        for (int i = 0; i < nums1.length; i++) {
            result[i] = nextGreater.get(nums1[i]);
        }

        return result;
    }
}
```

## Complexity Analysis:
### Time Complexity:
Traversing nums2: The algorithm iterates through each element in nums2 once. Let's denote the length of nums2 as n.

This part contributes O(n) to the time complexity.
While loop inside the traversal: In the worst case, each element is pushed and popped from the stack once. Each operation takes O(1) time.

This contributes O(n) to the time complexity.
Traversing nums1 to build the result array: This involves iterating through each element in nums1. Let's denote the length of nums1 as m.

This contributes O(m) to the time complexity.
The overall time complexity is O(n + n + m), which simplifies to O(n + m).

### Space Complexity:
Stack: The space required for the stack is at most O(n) in the worst case, where n is the length of nums2.

HashMap (nextGreater): The space required for the hashmap is at most O(n), considering each element in nums2 is associated with its next greater element.

Result Array: The space required for the result array is O(m), where m is the length of nums1.

*The overall space complexity is O(n + n + m), which simplifies to O(n + m).*
