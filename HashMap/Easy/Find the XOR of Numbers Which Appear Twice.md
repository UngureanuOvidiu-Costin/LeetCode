```Java
class Solution {
    public int duplicateNumbersXOR(int[] nums) {
        HashMap<Integer, Integer> numbersFrequency = new HashMap<>();
        int i;

        for(i = 0; i < nums.length; i = i + 1){
            numbersFrequency.put(nums[i], numbersFrequency.getOrDefault(nums[i], 0) + 1);
        }

        int result = 0;
        for(int key: numbersFrequency.keySet()){
            if(numbersFrequency.get(key) == 2){
                result = result ^ key;
            }
        }

        return result;
    }
}
```
