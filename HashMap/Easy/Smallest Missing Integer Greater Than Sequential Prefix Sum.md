```Java
import java.util.*;

class Solution {
    public int missingInteger(int[] nums) {
        HashMap<Integer, Integer> occurence = new HashMap<>();

        int i;
        for(i = 0; i < nums.length; i = i + 1){
            occurence.put(nums[i], occurence.getOrDefault(nums[i], 0) + 1);
        }

        int sum = 0;
        for(i = 0; i < nums.length; i = i + 1){
            if(i ==0 || nums[i] == nums[i-1] + 1){
                sum = sum + nums[i];
            }else{
                break;
            }
        }

        if(!occurence.containsKey(sum)){
            return sum;
        }

        for(i = sum + 1; ; i = i + 1){
            if(!occurence.containsKey(i)){
                return i;
            }
        }
    }
}
```
