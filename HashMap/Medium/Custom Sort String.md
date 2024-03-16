```Java
class Solution {
    public String customSortString(String order, String s) {
        HashMap<Character, Integer> hashMap2 = new HashMap<Character, Integer>();
        int i, j;
        char c;
        StringBuilder reconstructedString = new StringBuilder();
        char key;
        
        for(i = 0; i < s.length(); i = i + 1){
            c = s.charAt(i);
            if(!hashMap2.containsKey(c)){
                hashMap2.put(c, 1);
            }else{
                hashMap2.put(c, hashMap2.get(c) + 1);
            }
        }

        for(i = 0; i < order.length(); i++){
            key = order.charAt(i);
            if(hashMap2.containsKey(key)){
                
                if(hashMap2.get(key) == 1){
                    reconstructedString.append(key);
                }else{
                    for(j = 0; j < hashMap2.get(key); j = j + 1){
                        reconstructedString.append(key);
                    }
                }
                hashMap2.remove(key);
            }
        }


        for(Character keyCh: hashMap2.keySet()){
            for(j = 0; j < hashMap2.get(keyCh); j = j + 1){
                reconstructedString.append(keyCh);
            }
        }

        return reconstructedString.toString();
    }
}
```
