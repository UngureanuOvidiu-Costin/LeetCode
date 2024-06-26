# Solution

```Java
class Solution {
    public int countWords(String[] words1, String[] words2) {
        HashMap<String, Integer> w1Frequency = new HashMap<>();
        HashMap<String, Integer> w2Frequency = new HashMap<>();
        int i, counter = 0;

        for(i = 0; i < words1.length; i = i + 1) {
            w1Frequency.put(words1[i], w1Frequency.getOrDefault(words1[i], 0) + 1);
        }

        for(i = 0; i < words2.length; i = i + 1) {
            w2Frequency.put(words2[i], w2Frequency.getOrDefault(words2[i], 0) + 1);
        }

        for(String word: w1Frequency.keySet()) {
            if(w1Frequency.get(word) == 1) {
                if(w2Frequency.containsKey(word)){
                    if(w2Frequency.get(word) == 1){
                        counter++;
                    }
                }
            }
        }
        
        w1Frequency.clear();
        w2Frequency.clear();

        return counter;
    }
}
```
