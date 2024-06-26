# Intuition

The problem is to determine if two strings word1 and word2 are "almost equivalent." Two strings are considered almost equivalent if the absolute difference in the frequency of each character between the two strings is at most 3 for all characters.

## Approach

1. **Frequency Count:** Create two frequency arrays, `w1Frequency` and `w2Frequency`, to store the frequency of each character ('a' to 'z') in `word1` and `word2`, respectively.
2. **Count Frequencies:** Traverse each string and update the respective frequency array.
3. **Compare Frequencies:** Iterate over the frequency arrays and check if the absolute difference in frequencies for each character is more than 3. If any character has a difference greater than 3, return `false`.
4. **Return Result:** If all characters pass the check, return `true`.

## Complexity

- Time complexity:
**Counting Frequencies:** The first two loops each iterate over the length of the strings, `N` and `M` respectively. Thus, counting frequencies has a time complexity of `𝑂(N + M)`, where `N` is the length of `word1` and `M` is the length of `word2`.
**Comparing Frequencies:** The final loop runs 26 times (constant, as there are 26 letters in the alphabet), which is `O(1)`.
So, the overall complexity is: `O(N + M)`

- Space complexity:
**Frequency Arrays:** Two arrays of size 26 are used, which is `O(26)=O(1)`.
**Other Variables:** Only a few integer variables are used, which is `O(1)`.
So, the overall complexity is: `O(1)`

## Code

```Java
class Solution {
    public boolean checkAlmostEquivalent(String word1, String word2) {
        int[] w1Frequency = new int[26];
        int[] w2Frequency = new int[26];
        int i;
        
        for(i = 0; i < word1.length(); i = i + 1) {
            w1Frequency[word1.charAt(i) - 'a']++; 
        }

        for(i = 0; i < word2.length(); i = i + 1) {
            w2Frequency[word2.charAt(i) - 'a']++; 
        }

        
        for(i = 0; i < 26; i = i + 1) {
            if(Math.abs(w1Frequency[i] - w2Frequency[i]) > 3) {
                return false;
            }
        }

        return true;
    }
}
```
