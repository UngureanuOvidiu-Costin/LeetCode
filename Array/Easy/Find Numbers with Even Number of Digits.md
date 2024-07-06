
```Java
class Solution {
    public int findNumbers(int[] nums) {
        int i, result = 0;
        for(i = 0; i < nums.length; i = i + 1){
            if((nums[i] >= 10 && nums[i] <= 99) ||
               (nums[i] >= 1000 && nums[i] <= 9999) ||
               (nums[i] >= 100000 && nums[i] <= 999999)){
                result = result + 1;
               }
        }

        return result;
    }
}
```
