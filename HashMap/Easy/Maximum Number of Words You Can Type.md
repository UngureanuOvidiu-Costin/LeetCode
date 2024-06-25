# Solution

```Java
class Solution {
    public int canBeTypedWords(String text, String brokenLetters) {
        String[] words = text.split(" ");
        int counter = 0, check;

        for(String word: words) {
            check = 1;
            for(Character c: word.toCharArray()) {
                if(brokenLetters.indexOf(c) != -1) {
                    check = 0;
                    break;
                }
            }

            if(check == 1){
                counter++;
            }
        }

        return counter;
    }
}
```
