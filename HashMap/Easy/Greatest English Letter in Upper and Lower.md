# Intuition

The problem requires us to find the greatest letter that appears both as a lowercase and an uppercase letter in the given string `s`.

## Approach

1. **Frequency Counting**:
   - We maintain two arrays `lowerLetters` and `upperLetters` of size 26 to count occurrences of each letter (lowercase and uppercase respectively).
   - Traverse through each character in the string `s`:
     - If the character is lowercase (`a` to `z`), increment the corresponding index in `lowerLetters`.
     - If the character is uppercase (`A` to `Z`), increment the corresponding index in `upperLetters`.

2. **Finding the Greatest Letter**:
   - Iterate from 'z' to 'a' (from index 25 to 0 in the arrays):
     - Check if both `lowerLetters[i]` and `upperLetters[i]` are greater than 0.
     - If true, convert the index `i` to the corresponding uppercase letter and return it.

3. **Edge Case**:
   - If no such letter exists (no letter is both lowercase and uppercase), return an empty string `""`.

## Complexity

- **Time Complexity**: `O(n)`, where `n` is the length of the string `s`. We traverse the string once to build the frequency arrays.

- **Space Complexity**: `O(1)` since the arrays `lowerLetters` and `upperLetters` are of constant size (26) regardless of the input size.

## Code

```Java
class Solution {
    public String greatestLetter(String s) {
        int[] lowerLetters = new int[26];
        int[] upperLetters = new int[26];

        for (char ch : s.toCharArray()) {
            if (Character.isLowerCase(ch)) {
                lowerLetters[ch - 'a']++;
            } else {
                upperLetters[ch - 'A']++;
            }
        }

        for (int i = 25; i >= 0; i--) {
            if (lowerLetters[i] > 0 && upperLetters[i] > 0) {
                return Character.toString((char) (i + 'A'));
            }
        }

        return "";
    }
}
```
