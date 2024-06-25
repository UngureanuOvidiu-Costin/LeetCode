# Solution

```Java
class Solution {
    public boolean checkIfPangram(String sentence) {
        boolean []letters = new boolean[26];
        int i;

        for(i = 0; i < sentence.length(); i = i + 1) {
            letters[sentence.charAt(i) - 'a'] = true;
        }

        for(i = 0; i < 26; i = i + 1){
            if(letters[i] != true){
                return false;
            }
        }
        return true;
    }
}
```
