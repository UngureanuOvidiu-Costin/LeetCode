```Java
class Solution {
    public int countCharacters(String[] words, String chars) {
        int result = 0;
        Map<Character, Integer> charCount = new HashMap<>();
        
        for (char ch : chars.toCharArray()) {
            charCount.put(ch, charCount.getOrDefault(ch, 0) + 1);
        }
        
        for (String word : words) {
            Map<Character, Integer> wordCharCount = new HashMap<>(charCount);
            boolean canFormWord = true;
            
            for (char ch : word.toCharArray()) {
                if (!wordCharCount.containsKey(ch) || wordCharCount.get(ch) == 0) {
                    canFormWord = false;
                    break;
                }
                wordCharCount.put(ch, wordCharCount.get(ch) - 1);
            }
            
            if (canFormWord) {
                result += word.length();
            }
        }
        
        return result;
    }
}
```
