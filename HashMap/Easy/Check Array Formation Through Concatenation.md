# Solution

```Java
import java.util.HashMap;

class Solution {
    public boolean canFormArray(int[] arr, int[][] pieces) {
        HashMap<Integer, int[]> piecesMap = new HashMap<>();
        for(int[] piece: pieces){
            piecesMap.put(piece[0], piece);
        }

        int i, j;
        for(i = 0; i < arr.length;){
            if(!piecesMap.containsKey(arr[i])){
                return false;
            }

            for (int val : piecesMap.get(arr[i])) {
                if (arr[i++] != val) {
                    return false;
                }
            }
        }

        return true;
    }
}
```
