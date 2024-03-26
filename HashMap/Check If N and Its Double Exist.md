```Java
class Solution {
    public boolean checkIfExist(int[] arr) {
        HashMap<Integer, Integer> presence = new HashMap<>();
        int i;
        for(i = 0; i < arr.length; i = i + 1){
            if(presence.containsKey(arr[i] * 2)){
                return true;
            }else if(presence.containsKey(arr[i] / 2) && arr[i] % 2 == 0){
                return true;
            }
            presence.put(arr[i], i);
        }

        return false;
    }
}
```
