# Solution

```Java
class Solution {
    public int maximumLengthSubstring(String s) {
        HashMap<Character, Integer> frequencyMap = new HashMap<>();
        int left = 0, maxLength = 0;

        for (int right = 0; right < s.length(); right++) {
            char rightChar = s.charAt(right);
            frequencyMap.put(rightChar, frequencyMap.getOrDefault(rightChar, 0) + 1);

            while (frequencyMap.get(rightChar) > 2) {
                char leftChar = s.charAt(left);
                frequencyMap.put(leftChar, frequencyMap.get(leftChar) - 1);
                left++;
            }

            maxLength = Math.max(maxLength, right - left + 1);
        }

        return maxLength;
    }
}
```
