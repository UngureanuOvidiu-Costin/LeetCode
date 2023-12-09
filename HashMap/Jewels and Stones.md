# LeetCode Problem Writeup

## Problem Title: [Jewels and Stones](https://leetcode.com/problems/jewels-and-stones/description/)

### Problem Description:

You're given strings jewels representing the types of stones that are jewels, and stones representing the stones you have. Each character in stones is a type of stone you have. You want to know how many of the stones you have are also jewels.
<br>
Letters are case sensitive, so "a" is considered a different type of stone from "A".*

### Approach:

1. Create a set of jewels to store the unique types of jewels.
2. Iterate through each stone and check if it is present in the set of jewels.
3. Maintain a count of the stones that are also jewels.

### Pseudocode:

```plaintext
FUNCTION countJewelsInStones(jewels, stones)
    jewelSet = CREATE_SET_FROM(jewels)  # Create a set for efficient lookup

    jewelCount = 0  # Initialize a variable to count the number of jewels

    FOR EACH stone IN stones  # Iterate through each stone
        IF stone IN jewelSet THEN  # Check if the stone is a jewel
            jewelCount = jewelCount + 1  # Increment the count

    RETURN jewelCount  # Return the final count of jewels in stones
END FUNCTION
```

## Code Implementation:

```
class Solution {
    public int numJewelsInStones(String jewels, String stones) {
        HashMap<Character, Integer> hashJewels = new HashMap<>();
        int i, jewelsCount = 0;
        char currentChar;
        for (i = 0; i < jewels.length(); i++) {
            currentChar = jewels.charAt(i);
            hashJewels.put(currentChar, 1);
        }

        for(i = 0; i < stones.length(); i = i + 1){
            currentChar = stones.charAt(i);
            if (hashJewels.containsKey(currentChar)) {
                jewelsCount++;
            }
        }

        return jewelsCount;
    }
}
```

## Complexity Analysis:
![image](https://github.com/UngureanuOvidiu-Costin/LeetCode/assets/102877918/475f1618-2119-4ceb-99a6-21c90aa9599f)


**Time Complexity:** <br>
The time complexity of the algorithm is O(len(jewels) + len(stones)), where len(jewels) is the length of the string representing the types of jewels, and len(stones) is the length of the string representing the stones.


**Space Complexity:** <br>
The space complexity of the algorithm is O(len(jewels)), as the primary space-consuming structure is the set created from the types of jewels. In the worst case, the set might need to store each unique type of jewel.
<br>
Therefore, the overall space complexity is O(len(jewels)).
