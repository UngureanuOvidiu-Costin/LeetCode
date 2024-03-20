```Java
class Solution {
    public int[] fairCandySwap(int[] aliceSizes, int[] bobSizes) {
        HashMap<Integer, Integer> hashMap_1 = new HashMap<>();
        HashMap<Integer, Integer> hashMap_2 = new HashMap<>();

        int i, aliceSum = 0, bobSum = 0;
        for(i = 0; i < aliceSizes.length; i++){
            hashMap_1.put(aliceSizes[i], hashMap_1.getOrDefault(aliceSizes[i], 0) + 1);
            aliceSum+=aliceSizes[i];
        }

        for(i = 0; i < bobSizes.length; i++){
            hashMap_2.put(bobSizes[i], hashMap_2.getOrDefault(bobSizes[i], 0) + 1);
            bobSum+=bobSizes[i];
        }

        int diff = (aliceSum - bobSum) / 2;
        for (int candy : aliceSizes) {
            int target = candy - diff;
            if (hashMap_2.containsKey(target)) {
                return new int[]{candy, target};
            }
        }

        return null;
    }
}
```
