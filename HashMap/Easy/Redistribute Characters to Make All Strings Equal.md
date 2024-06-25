# Solution

```Java
class Solution {
    public boolean makeEqual(String[] words) {
        int i, j;
        HashMap<Character, Integer> charactersFrequency = new HashMap<>();
        
        for(i = 0; i < words.length; i = i + 1) {
            for(j = 0; j < words[i].length(); j = j + 1) {
                charactersFrequency.put(words[i].charAt(j), charactersFrequency.getOrDefault(words[i].charAt(j), 0) + 1);
            }
        }

        for(Character c: charactersFrequency.keySet()) {
            if(charactersFrequency.get(c) % words.length != 0) {
                return false;
            }
        }

        return true;
    }
}
```
