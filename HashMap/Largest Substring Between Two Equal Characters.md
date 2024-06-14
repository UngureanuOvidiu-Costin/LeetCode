```Java
class Solution {
    public int maxLengthBetweenEqualCharacters(String s) {
        HashMap<Character, Integer> characterPosition = new HashMap<>();
        int max = 0;
        int i;

        for(i = 0; i < s.length(); i = i + 1){
            if(!characterPosition.containsKey(s.charAt(i))){
                characterPosition.put(s.charAt(i), i);
            }else{
                max = Math.max(max, i - characterPosition.get(s.charAt(i)));
            }
        }
        
        return max-1;
    }
}
```
