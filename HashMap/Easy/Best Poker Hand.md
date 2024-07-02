# Intuition

The problem requires determining the best possible poker hand from a given set of card ranks and suits. The possible hands in descending order of strength are: "Flush", "Three of a Kind", "Pair", and "High Card".

## Approach

1. **Frequency Counting**:
   - Use a `HashMap` to count the frequency of each suit (`cardsSuits`) and each rank (`cardsRanks`).
   - Traverse the arrays `ranks` and `suits` simultaneously to populate the frequency maps.

2. **Determine Best Hand**:
   - Check for "Flush":
     - If any suit appears 5 or more times in `cardsSuits`, return "Flush".
   - Check for "Three of a Kind" and "Pair":
     - Traverse `cardsRanks` to find the highest frequency of any rank.
     - If the highest frequency is 3 or more, return "Three of a Kind".
     - If the highest frequency is 2, return "Pair".
   - If none of the above conditions are met, return "High Card".

3. **Return**:
   - Return the best hand determined from the conditions above.

## Complexity

- **Time Complexity**: O(n), where n is the number of cards in the hand. This is because we traverse the list of cards a constant number of times.
- **Space Complexity**: O(1) for the suits (fixed at 4 unique suits) and O(k) for the ranks (where k is the number of unique ranks, typically at most 13 for a standard deck).

```Java
class Solution {
    public String bestHand(int[] ranks, char[] suits) {
        HashMap<Character, Integer> cardsSuits = new HashMap<>();
        HashMap<Integer, Integer> cardsRanks = new HashMap<>();

        for (int i = 0; i < ranks.length; i++) {
            cardsSuits.put(suits[i], cardsSuits.getOrDefault(suits[i], 0) + 1);
            cardsRanks.put(ranks[i], cardsRanks.getOrDefault(ranks[i], 0) + 1);
        }

        for (int count : cardsSuits.values()) {
            if (count >= 5) {
                return "Flush";
            }
        }

        int maxRankCount = 0;
        for (int count : cardsRanks.values()) {
            if (count > maxRankCount) {
                maxRankCount = count;
            }
        }

        if (maxRankCount >= 3) {
            return "Three of a Kind";
        } else if (maxRankCount == 2) {
            return "Pair";
        } else {
            return "High Card";
        }
    }
}
```
