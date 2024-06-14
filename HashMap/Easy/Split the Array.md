```Java
import java.util.HashMap;

class Solution {
    public boolean isPossibleToSplit(int[] nums) {
        int len = nums.length / 2;
        if(len * 2 != nums.length){
            return false;
        }

        int i;
        HashMap<Integer, Integer> occurence = new HashMap<>();
        for(i = 0; i < nums.length; i = i + 1){
            occurence.put(nums[i], occurence.getOrDefault(nums[i], 0) + 1);
        }
        
        for(Integer nr: occurence.keySet()){
            if(occurence.get(nr) > 2){
                return false;
            }
        }
        
        return true;
    }
}
```
