```Java
class Solution {
    public List<String> commonChars(String[] words) {
        List<String> result = new ArrayList<>();
        HashMap<Character, Integer> commonCharsCount = new HashMap<>();

        for (char c : words[0].toCharArray()) {
            commonCharsCount.put(c, commonCharsCount.getOrDefault(c, 0) + 1);
        }

        for (int i = 1; i < words.length; i++) {
            HashMap<Character, Integer> wordCharsCount = new HashMap<>();
            for (char c : words[i].toCharArray()) {
                wordCharsCount.put(c, wordCharsCount.getOrDefault(c, 0) + 1);
            }

            for (char c : commonCharsCount.keySet()) {
                int countInCurrentWord = wordCharsCount.getOrDefault(c, 0);
                commonCharsCount.put(c, Math.min(commonCharsCount.get(c), countInCurrentWord));
            }
        }

        for (char c : commonCharsCount.keySet()) {
            int count = commonCharsCount.get(c);
            for (int i = 0; i < count; i++) {
                result.add(String.valueOf(c));
            }
        }

        return result;
    }
}

```
