```Java
class Solution {
    public int findLucky(int[] arr) {
        HashMap<Integer, Integer> frequency = new HashMap<>();
        int i;
        for(i = 0; i < arr.length; i = i + 1){
            frequency.put(arr[i], frequency.getOrDefault(arr[i], 0) + 1);
        }

        int result = -1;
        for(Integer nr: frequency.keySet()){
            if(Objects.equals(frequency.get(nr), nr)){
                if(nr > result){
                    result = nr;
                }
            }
        }

        return result;
    }
}
```
