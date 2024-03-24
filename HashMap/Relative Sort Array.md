```Java
class Solution {
    public int[] relativeSortArray(int[] arr1, int[] arr2) {
        HashMap<Integer, Integer> hashMap1 = new HashMap<>();
        int[] result = new int[arr1.length];
        int i;
        for(i = 0; i < arr1.length; i = i + 1){
            hashMap1.put(arr1[i], hashMap1.getOrDefault(arr1[i], 0) + 1);
        }

        int j = 0, index, count;
        for(i = 0; i < arr2.length; i = i + 1){
            count = hashMap1.get(arr2[i]);

            for(index = 0; index < count; index++){
                result[j] = arr2[i];
                j = j + 1;
            }

            hashMap1.remove(arr2[i]);
        }

        List<Integer> sortedRemain = new ArrayList<>(hashMap1.keySet());
        Collections.sort(sortedRemain);
        for(Integer nr: sortedRemain){
            count = hashMap1.get(nr);

            for(index = 0; index < count; index++){
                result[j] = nr;
                j = j + 1;
            }

            hashMap1.remove(nr);
        }

        return result;
    }
}
```
