# Intuition

The problem involves maximizing the score by removing specific pairs of characters ("ab" and "ba") from a string. The score for removing each pair is given, and we should prioritize removing the pair with the higher score first to maximize the total score.

## Approach

1. **Determine Priority**:
   - Identify which pair has the higher score. We prioritize removing this pair first to maximize the total score.

2. **Remove High Priority Pairs**:
   - Use a helper function `removeSubstring` to remove occurrences of the high priority pair from the string and calculate the score for these removals.

3. **Remove Low Priority Pairs**:
   - Use the same helper function to remove occurrences of the low priority pair from the remaining string and calculate the additional score.

4. **Calculate Total Score**:
   - The total score is the sum of the scores obtained from removing both pairs of substrings.

## Complexity

- **Time complexity**: O(n), where n is the length of the string. Each character is processed a constant number of times.

- **Space complexity**: O(n), where n is the length of the string. The stack and StringBuilder used in the helper function can store up to all characters of the string in the worst case.

## Code

```Java
class Solution {
    public int maximumGain(String s, int x, int y) {
        int totalScore = 0;
        String highPriorityPair, lowPriorityPair;
        if (x > y) {
            highPriorityPair = "ab";
            lowPriorityPair = "ba";
        } else {
            highPriorityPair = "ba";
            lowPriorityPair = "ab";
        }

        String stage1 = removeSubstring(s, highPriorityPair);
        totalScore = (s.length() - stage1.length()) / 2 * Math.max(x, y);
        String stage2 = removeSubstring(stage1, lowPriorityPair);
        totalScore = totalScore + (stage1.length() - stage2.length()) / 2 * Math.min(x, y);

        return totalScore;
    }

    private String removeSubstring(String s, String pair) {
        Stack<Character> targetPair = new Stack<>();
        StringBuilder result = new StringBuilder();

        for (Character c : s.toCharArray()) {
            if (!targetPair.isEmpty() && c == pair.charAt(1) && targetPair.peek() == pair.charAt(0)) {
                targetPair.pop();
            } else {
                targetPair.push(c);
            }
        }

        for (char c : targetPair) {
            result.append(c);
        }

        return result.toString();
    }

}
```
