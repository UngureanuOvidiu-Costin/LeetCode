# Solution

```Java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        HashMap<Integer, Integer> hashMap1 = new HashMap<>();
        HashMap<Integer, Integer> hashMap2 = new HashMap<>();

        for (int num : nums1) {
            if (hashMap1.containsKey(num)) {
                int occurrences = hashMap1.get(num);
                hashMap1.put(num, occurrences + 1);
            } else {
                hashMap1.put(num, 1);
            }
        }

        for (int num : nums2) {
            if (hashMap2.containsKey(num)) {
                int occurrences = hashMap2.get(num);
                hashMap2.put(num, occurrences + 1);
            } else {
                hashMap2.put(num, 1);
            }
        }


        Set<Integer> commonKeys = hashMap1.keySet();
        commonKeys.retainAll(hashMap2.keySet());

        List<Integer> res = new ArrayList<>();
        for(int i: commonKeys){
            int min;
            if(hashMap1.get(i) > hashMap2.get(i)){
                min = hashMap2.get(i);
            }else{
                min = hashMap1.get(i);
            }
            List<Integer> valuesToAdd = Collections.nCopies(min, i);
            res.addAll(valuesToAdd);
        }

        return res.stream().mapToInt(Integer::intValue).toArray();
    }
}
```
