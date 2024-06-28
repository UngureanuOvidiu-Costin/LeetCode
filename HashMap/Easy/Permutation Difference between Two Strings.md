# Intuition

The problem is to find the sum of the absolute differences of the positions of characters that appear in both strings `s` and `t`. This means for each character that appears in both strings, we need to calculate the difference in their positions and sum these differences.

## Approach

1. **Position Mapping:** Use two hash maps to store the positions of each character in strings `s` and `t`.
2. **Populate Maps:** Traverse each string and populate the hash maps with the positions of each character.
3. **Calculate Differences:** Iterate over the characters in the hash map for `s` and check if they also exist in the hash map for `t`. If they do, calculate the absolute difference in their positions and add this to the result.
4. **Return Result:** Return the sum of these absolute differences

## Complexity

- Time complexity:
**Populating Maps:** The first and second loops each iterate over the length of the strings `s` and `t` respectively, resulting in O(n) time, where `n` is the length of the strings.
**Calculating Differences:** The third loop iterates over the characters in `positionsS`. In the worst case, this is also O(26) = O(1), because there are 26 characters in English alphabet.

- Space complexity:
**HashMaps:** The space used by the two hash maps depends on the number of unique characters in the strings. In the worst case, this is O(26) = O(1) for each hash map because there are at most 26 keys(letters of English alphabet).
**Other Variables:** Only a few integer variables are used, which is O(1) space.

## Code

```Java
class Solution {
    public int findPermutationDifference(String s, String t) {
        int result = 0, i;

        HashMap<Character, Integer> positionsS = new HashMap<>();
        HashMap<Character, Integer> positionsT = new HashMap<>();
    
        for(i = 0; i < s.length(); i = i + 1) {
            positionsS.put(s.charAt(i), i);
        }

        for(i = 0; i < t.length(); i = i + 1) {
            positionsT.put(t.charAt(i), i);
        }

        for(Character c: positionsS.keySet()) {
            if(positionsT.containsKey(c)) {
                result = result + Math.abs(positionsS.get(c) - positionsT.get(c));
            }
        }

        return result;
    }
}
```
