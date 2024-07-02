# Solution

```Java
class Solution {
    public static String oddString(String[] words) {
        Map<List<Integer>, List<String>> differenceMap = new HashMap<>();
        
        for (String word : words) {
            List<Integer> diffArray = new ArrayList<>();
            for (int i = 0; i < word.length() - 1; i++) {
                diffArray.add(word.charAt(i + 1) - word.charAt(i));
            }

            differenceMap.putIfAbsent(diffArray, new ArrayList<>());
            differenceMap.get(diffArray).add(word);
        }
        
        for (Map.Entry<List<Integer>, List<String>> entry : differenceMap.entrySet()) {
            if (entry.getValue().size() == 1) {
                return entry.getValue().get(0);
            }
        }
        
        return "";
    }
}
```
