# LeetCode Problem Writeup

## Problem Title: [Find the Pivot Integer](https://leetcode.com/problems/find-the-pivot-integer/description/)

### Problem Description:

*Given a positive integer `n`, find the **pivot integer** `x` such that:*

 - *The sum of all elements between `1` and `x` inclusively equals the sum of all elements between `x` and `n` inclusively.*

*Return the pivot integer `x`. If no such integer exists, return `-1`. It is guaranteed that there will be at most one pivot index for the given input.*

### Approach:

*To solve this problem, we can calculate the sum of all integers from `1` to `n` using the formula for the **sum of an arithmetic series**. After that, we iterate through each integer from 1 to n and calculate the prefix sum from 1 to i (inclusive) and the suffix sum from i to n (inclusive). We store these prefix and suffix sums in two separate `HashMaps`. Finally, we iterate through these HashMaps to find an integer `i` for which the prefix sum equals the suffix sum.*

### Pseudocode:
```Python
pivotInteger(n):
    sum = (1 + n) * n / 2  // Calculate the total sum of integers from 1 to n
    
    rightSum = {}  // Initialize a HashMap to store prefix sums from 1 to i
    leftSum = {}  // Initialize a HashMap to store suffix sums from i to n
    
    prefixSum = 0  // Initialize prefix sum to 0
    
    // Calculate prefix and suffix sums
    for i = 1 to n:
        prefixSum = prefixSum + i
        rightSum[i] = prefixSum
        leftSum[i] = sum - prefixSum + i
    
    // Iterate through the prefix and suffix sums to find the pivot integer
    for i = 1 to n:
        if rightSum[i] == leftSum[i]:
            return i  // Return pivot integer if found
            
    return -1  // Return -1 if no pivot integer exists
```

## Code Implementation:
```Java
class Solution {
    public int pivotInteger(int n) {
        HashMap<Integer, Integer> rightSum = new HashMap<>();
        HashMap<Integer, Integer> leftSum = new HashMap<>();

        int sum = (1 + n) * n / 2;
        int i, prefixSum = 0;
        for(i = 1; i <= n; i = i + 1){
            prefixSum = prefixSum + i;
            rightSum.put(i, prefixSum);
            leftSum.put(i, sum - prefixSum + i);
        }

        for(i = 1; i <= n; i = i + 1){
            if(Objects.equals(rightSum.get(i), leftSum.get(i))){
                return i;
            }
        }

        return -1;
    }
}
```

## Complexity Analysis:

### Time Complexity: O(n)
- The time complexity of this solution is O(n) since we iterate through the integers from 1 to n twice, and the operations inside the loops are constant time, resulting in 2 * O(n) + O(1) = O(n)
  
### Space Complexity: O(n)
- The space complexity of this solution is O(n) as we use two HashMaps to store prefix and suffix sums, resulting in 2 * O(n) + O(1) for constant variables like i, prefixSum, sum -> O(n).
