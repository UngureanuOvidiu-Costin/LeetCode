```Java
class Solution {
    public int findMaxLength(int[] nums) {
        int maxLen = 0;
        int count = 0;
        int i;
        HashMap<Integer, Integer> hashMap = new HashMap<>();
        hashMap.put(0, -1);

        for(i = 0; i < nums.length; i = i + 1){
            if(nums[i] == 0){
                count = count - 1;
            }else{
                count = count + 1;
            }
            if(!hashMap.containsKey(count)){
                hashMap.put(count, i);
            }else{
                maxLen = Math.max(maxLen, i - hashMap.get(count));
            }
        }

        return maxLen;
    }
}
```
