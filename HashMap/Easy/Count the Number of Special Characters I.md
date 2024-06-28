# Intuition

The problem is to count the number of "special characters" in a string. A "special character" is defined as a character that appears in both lowercase and uppercase forms in the string. To solve this problem, we can use frequency arrays to count occurrences of each character in both lowercase and uppercase forms, and then check for characters that have both forms present.

## Approach

1. **Frequency Arrays:** Use two arrays, `lower` and `upper`, to store the frequency of lowercase and uppercase characters, respectively.
2. **Count Frequencies:** Traverse the input string and update the respective frequency array based on whether the character is lowercase or uppercase.
3. **Count Special Characters:** Iterate over the frequency arrays to count how many characters appear in both lowercase and uppercase forms.
4. **Return Result:** The count of such special characters is returned as the result.

## Complexity

- Time complexity: O(n)
**Counting Frequencies:** The first loop iterates over the string of length `n`, which takes O(n) time.
**Checking Special Characters:** The second loop iterates 26 times (once for each letter of the alphabet), which takes O(1) time.

- Space complexity: O(1)
**Frequency Arrays:** Two arrays of size 26 are used, which takes O(26)=O(1) space.
**Other Variables:** Only a few integer variables (i and result) are used, which is O(1) space.

## Code

```Java
class Solution {
    public int numberOfSpecialChars(String word) {
        int[]lower = new int[26];
        int[]upper = new int[26];
        int i, result = 0;

        for(i = 0; i < word.length(); i = i + 1) {
            if(Character.isLowerCase(word.charAt(i))) {
                lower[word.charAt(i) - 'a']++;
            }else{
                upper[word.charAt(i) - 'A']++;
            }
        }

        for(i = 0;i < 26; i = i + 1) {
            if(lower[i] > 0 && upper[i] > 0) {
                result++;
            }
        }

        return result;
    }
}
```
