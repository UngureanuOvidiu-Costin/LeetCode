```Java
class Solution {
    public int minimizedStringLength(String s) {
        HashMap<Character, Integer> hashMap = new HashMap<>();
        int result = 0;
        for(Character c: s.toCharArray()){
            hashMap.put(c, hashMap.getOrDefault(c, 0) + 1);
        }

        result = hashMap.keySet().size();
        
        return result;
    }
    
}
```
