# Intuition

The problem requires checking if the distances between every pair of equal characters in a string match the specified distances provided in an array. A `HashMap` can help efficiently track the positions of characters in the string.

## Approach

1. **Track Character Positions**:
   - Use a `HashMap` called `positions` to store the last seen position of each character in the string `s`.
   - Iterate through the string `s`.

2. **Check Distances**:
   - For each character in the string:
     - If the character has been seen before (exists in the `positions` map):
       - Calculate the distance between the current position and the last seen position of the character.
       - Compare this calculated distance with the corresponding value in the `distance` array.
       - If the distances do not match, return `false`.
     - Update the position of the character in the `positions` map to the current index.

3. **Return**:
   - If all distances match, return `true`.

## Complexity

- **Time Complexity**: O(n), where n is the length of the string `s`. This is because we iterate through the string once.
- **Space Complexity**: O(1), since the `HashMap` stores at most 26 entries for each letter in the alphabet.

## Code

```Java
class Solution {
    public boolean checkDistances(String s, int[] distance) {
        HashMap<Character, Integer> positions = new HashMap<>();
        int i;

        for(i = 0; i < s.length(); i = i + 1) {
            if(positions.containsKey(s.charAt(i))){
                if(i - positions.get(s.charAt(i)) - 1 != distance[s.charAt(i) - 'a']){
                    return false;
                }else{
                    positions.put(s.charAt(i), i);
                }
            } else {
                positions.put(s.charAt(i), i);
            }
        }

        return true;
    }
}
```
