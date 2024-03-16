```Java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int[] answer = new int[nums.length];
        int i;
        
        answer[0] = 1;
        for(i = 1; i < nums.length; i = i + 1){
            answer[i] = answer[i - 1] * nums[i - 1];
        }
        
        int right = 1;
        for(i = nums.length - 1; i >= 0; i = i - 1){
            answer[i] = answer[i] * right;
            right = right * nums[i];
        }
        return answer;
    }
}
```
