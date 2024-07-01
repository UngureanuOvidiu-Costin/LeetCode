# Intuition

The problem involves decoding a message using a substitution table derived from a given `key`. Characters in `key` are mapped to consecutive lowercase letters starting from 'a'. Non-alphabetic characters in `key` are ignored in the mapping.

## Approach

1. **Substitution Table Creation**:
   - Use a `HashMap` called `substitutionTable` to map characters from `key` to consecutive lowercase letters starting from 'a'.
   - Iterate through each character in `key`:
     - If the character is alphabetic and not already in `substitutionTable`, map it to `currentChar` (which starts from 'a' and increments).

2. **Message Decoding**:
   - Initialize an empty string `result` to store the decoded message.
   - Traverse each character in `message`:
     - If the character exists in `substitutionTable`, append its mapped value from `substitutionTable` to `result`.
     - If the character does not exist in `substitutionTable` (i.e., it's not in `key` or is a non-alphabetic character), append the character itself to `result`.

3. **Return**:
   - Return the decoded `result` string.

## Complexity

- **Time Complexity**: `O(n + m)`, where n is the length of `key` and m is the length of `message`. We iterate through `key` to build the `substitutionTable` and through `message` to decode it.

- **Space Complexity**: `O(1)` (or technically `O(26)` for the `substitutionTable`), as we use a fixed-size `HashMap` of 26 entries to store mappings for lowercase letters.

## Code

```Java
class Solution {
    public String decodeMessage(String key, String message) {
        HashMap<Character, Character> substitutionTable = new HashMap<>();
        int i;
        char currentChar = 'a';

        for(i = 0; i < key.length(); i = i + 1) {
            if(!substitutionTable.containsKey(key.charAt(i)) &&
                Character.isLetter(key.charAt(i))) {
                substitutionTable.put(key.charAt(i), currentChar);
                currentChar++;
            }
        }

        String result = "";
        for(i = 0; i < message.length(); i = i + 1) {
            if(substitutionTable.containsKey(message.charAt(i))){
                result = result + substitutionTable.get(message.charAt(i));
            }else{
                result = result + message.charAt(i);
            }
        }

        return result;
    }
}
```
