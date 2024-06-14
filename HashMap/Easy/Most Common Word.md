```Java
class Solution {
    public String mostCommonWord(String paragraph, String[] banned) {
        String[] paragraphWords = paragraph.toLowerCase().split("[\\s,.!?;']+");

        HashMap<String, Integer> occurence = new HashMap<>();
        List<String> listBanned = Arrays.asList(banned);

        
        for (String word: paragraphWords){
            if(!listBanned.contains(word)) {
                occurence.put(word, occurence.getOrDefault(word, 0) + 1);
            }
        }

        String keyWithMaxValue = Collections.max(occurence.entrySet(), Map.Entry.comparingByValue()).getKey();
        return keyWithMaxValue;
    }
}
```
