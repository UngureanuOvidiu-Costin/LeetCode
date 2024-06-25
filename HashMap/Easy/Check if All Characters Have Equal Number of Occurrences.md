# Solution

```Java
class Solution {
    public boolean areOccurrencesEqual(String s) {
        HashMap<Character, Integer> charFrequency = new HashMap<>();
        Set<Integer> frequencies = new HashSet<>();
        int i;

        for(i = 0; i < s.length(); i = i + 1) {
            charFrequency.put(s.charAt(i), charFrequency.getOrDefault(s.charAt(i), 0) + 1);
        }

        for(Integer frequency: charFrequency.values()) {
            frequencies.add(frequency);
        }

        if(frequencies.size() > 1) {
            return false;
        }

        return true;
    }
}
```
