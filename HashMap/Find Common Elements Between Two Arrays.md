```Java
class Solution {
    public int[] findIntersectionValues(int[] nums1, int[] nums2) {
        int[] result = new int[2];
        result[0] = 0;
        result[1] = 0;
        HashMap<Integer, Integer> hashMap1 = new HashMap<>();
        HashMap<Integer, Integer> hashMap2 = new HashMap<>();

        int i;
        for(i = 0; i < nums1.length; i = i + 1){
            hashMap1.put(nums1[i], hashMap1.getOrDefault(nums1[i], 0) + 1);
        }

        for(i = 0; i < nums2.length; i = i + 1){
            hashMap2.put(nums2[i], hashMap2.getOrDefault(nums2[i], 0) + 1);
        }

        for(Integer nr: hashMap1.keySet()){
            if(hashMap2.containsKey(nr)){
                result[0] = result[0] + hashMap1.get(nr);
            }
        }
        
        for(Integer nr: hashMap2.keySet()){
            if(hashMap1.containsKey(nr)){
                result[1] = result[1] + hashMap2.get(nr);
            }
        }
        
        return result;
    }
}
```
