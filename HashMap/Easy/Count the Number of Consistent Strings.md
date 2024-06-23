# Solution

```Java
class Solution {
    public int countConsistentStrings(String allowed, String[] words) {
        Set<Character> uniqueCharsAllowed = new HashSet<>();
        
        for(Character c: allowed.toCharArray()){
            uniqueCharsAllowed.add(c);
        }
        
        int i, result = 0;
        boolean check = true;
        for(i = 0; i < words.length; i = i + 1){
            for(Character c: words[i].toCharArray()){
                if(!uniqueCharsAllowed.contains(c)){
                    check = false;
                }
            }
            if(check == true){
                result = result + 1;
            }else {
                check = true;
            }
        }
        return result;
    }
}
```
