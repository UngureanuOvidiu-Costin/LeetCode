# Solution

```Java
class Solution {
    public List<List<Integer>> mergeSimilarItems(int[][] items1, int[][] items2) {
        HashMap<Integer, Integer> hashItems1 = new HashMap<>();
        int i;

        for(i = 0; i < items1.length; i = i + 1) {
            hashItems1.put(items1[i][0], items1[i][1]);
        }

        for(i = 0; i < items2.length; i = i + 1) {
            hashItems1.put(items2[i][0], hashItems1.getOrDefault(items2[i][0], 0) + items2[i][1]);
        }

        List<Integer> keysList = new ArrayList<>(hashItems1.keySet());
        Collections.sort(keysList);

        List<List<Integer>> result = new ArrayList<>();

        i = 0;
        for(Integer key: keysList) {
            List<Integer> temp = new ArrayList<>();
            temp.add(key);
            temp.add(hashItems1.get(key));
            result.add(temp);
        }

        return result;
    }
}
```
