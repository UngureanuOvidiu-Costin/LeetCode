```Java
import java.util.HashMap;

class Solution {
    public boolean canBeEqual(int[] target, int[] arr) {
        HashMap<Integer, Integer> targetHashMap = new HashMap<>();
        HashMap<Integer, Integer> arrHashMap = new HashMap<>();

        int i;
        int min = Math.min(target.length, arr.length);
        int max = Math.max(target.length, arr.length);
        
        for(i = 0; i < max; i = i + 1){
            targetHashMap.put(target[i], targetHashMap.getOrDefault(target[i], 0) + 1);
            arrHashMap.put(arr[i], arrHashMap.getOrDefault(arr[i], 0) + 1);
        }


        if(targetHashMap.keySet().size() != arrHashMap.keySet().size()){
            return false;
        }


        for(int key : targetHashMap.keySet()){
            if(!arrHashMap.containsKey(key)){
                return false;
            }
            if(arrHashMap.get(key) != targetHashMap.get(key)){
                return false;
            }
        }

        for(int key : arrHashMap.keySet()){
            if(!targetHashMap.containsKey(key)){
                return false;
            }
            if(arrHashMap.get(key) != targetHashMap.get(key)){
                return false;
            }
        }
        
        return true;
    }
}
```
