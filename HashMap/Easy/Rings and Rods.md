# Intuition

The problem is to count how many rods have all three colors of rings (Red, Green, and Blue) on them given a string `rings` that represents rings of different colors being placed on different rods. The string is formatted such that every two characters represent a ring and the rod it is placed on.

## Approach

1. **Store Rings on Rods:** Use a hash map where the key is the rod number (0-9) and the value is a set of characters representing the colors of rings on that rod.
2. **Populate the Map:** Iterate through the `rings` string in steps of 2 to extract the color and the rod number, then add the color to the corresponding set in the map.
3. **Count Complete Rods:** Iterate through the values in the hash map and count how many sets contain all three colors 'R', 'G', and 'B'.

## Complexity

- Time complexity:
**Population of Map:** Iterating through the rings string and populating the map takes `O(n)` time, where `n` is the length of the string rings.
**Counting Complete Rods:** Iterating through the values in the hash map to count complete rods takes `O(1)` time, as there are at most 10 rods.

- Space complexity:
Auxiliary Space: The space required for the hash map and the sets is `O(1)` in terms of the number of rods (since there are at most 10 rods) and `O(k)` in terms of the number of `ring` placements, where `k` is the total number of characters in the input string divided by `2` (as each ring placement is represented by 2 characters).

## Code

```Java
class Solution {
    public int countPoints(String rings) {
        HashMap<Integer, HashSet<Character>> rods = new HashMap<>();
        
        for (int i = 0; i < rings.length(); i += 2) {
            char color = rings.charAt(i);
            int rod = rings.charAt(i + 1) - '0';
            
            rods.putIfAbsent(rod, new HashSet<>());
            rods.get(rod).add(color);
        }
        
        int result = 0;
        for (HashSet<Character> colors : rods.values()) {
            if (colors.contains('R') && colors.contains('G') && colors.contains('B')) {
                result++;
            }
        }
        
        return result;
    }
}
```
