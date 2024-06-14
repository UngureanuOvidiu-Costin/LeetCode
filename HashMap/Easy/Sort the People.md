```Java
class Solution {
    public String[] sortPeople(String[] names, int[] heights) {
        TreeMap<Integer, String> treeMap = new TreeMap<>(Collections.reverseOrder());
        for (int i = 0; i < heights.length; i++) {
            treeMap.put(heights[i], names[i]);
        }

        String[] result = new String[heights.length];

        int index = 0;
        for (Map.Entry<Integer, String> entry : treeMap.entrySet()) {
            result[index++] = entry.getValue();
        }

        return result;
    }
}
```
