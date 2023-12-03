# LeetCode Problem Writeup

## Problem Title: [Distribute Candies](https://leetcode.com/problems/distribute-candies/description/)

### Problem Description:

*Alice has n candies, where the ith candy is of type candyType[i]. Alice noticed that she started to gain weight, so she visited a doctor.
The doctor advised Alice to only eat n / 2 of the candies she has (n is always even). Alice likes her candies very much, and she wants to eat the maximum number of different types of candies while still following the doctor's advice.
Given the integer array candyType of length n, return the maximum number of different types of candies she can eat if she only eats n / 2 of them.*

### Approach:

*As we need to check how many types of candies are there, we can use a HashMap to add each type of candy of type "i" and after all count and compare with n / 2.*

### Pseudocode:

```plaintext
function distributeCandies(candyType: array of integers): integer
    candyOccurrence := empty HashMap<Integer, Integer>
    limit := length of candyType / 2

    for i from 0 to length of candyType - 1
        if size of candyOccurrence >= limit
            return limit

        if candyType[i] is not in candyOccurrence
            candyOccurrence[candyType[i]] := 1

    if length of candyType / 2 <= size of candyOccurrence
        return length of candyType / 2
    else
        return size of candyOccurrence
```

## Code Implementation:

```class Solution {
    public int distributeCandies(int[] candyType) {
        HashMap<Integer, Integer> candyOccurence = new HashMap<>();

        int i, limit = candyType.length / 2;
        for(i = 0; i < candyType.length; i = i + 1){

            if(candyOccurence.size() >= limit){
                return limit;
            }

            if(!candyOccurence.containsKey(candyType[i])){
                candyOccurence.put(candyType[i], 1);
            }
        }

        if((candyType.length/2) <= candyOccurence.size()){
            return candyType.length/2;
        }else{
            return candyOccurence.size();
        }
    }
}
```

## Complexity Analysis:

### Time complexity Analysis:
The time complexity of the algorithm is primarily determined by the for loop that iterates through the candyType array. Let's denote the length of the candyType array as n.
1.For Loop: The for loop runs for each element in the candyType array, and each iteration involves constant-time operations (such as HashMap operations). Therefore, the time complexity of the for loop is O(n).
2.HashMap Operations: The operations on the HashMap (put and containsKey) are generally considered to have an average time complexity of O(1). However, in the worst case, it could be O(n) if there are many hash collisions. In practice, with a good hash function, HashMap operations are efficient.

Therefore, the overall time complexity of the algorithm is O(n).

### Space Complexity Analysis:
The space complexity is determined by the additional space used by the algorithm, mainly the HashMap.

1.HashMap: In the worst case, where all elements are unique, the HashMap can have a size of up to n/2 (since it's checking for uniqueness for each candy). Therefore, the space complexity for the HashMap is O(n/2), which is equivalent to O(n).
2.Other Variables: There are a few other constant space variables (like limit, i), which do not depend on the input size. Thus, they contribute O(1) to the space complexity.
