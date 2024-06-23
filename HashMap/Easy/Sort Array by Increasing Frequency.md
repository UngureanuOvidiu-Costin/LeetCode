# Solution

```Java
import java.util.*;

class Solution {
    public int[] frequencySort(int[] nums) {
        int i;
        int []result = new int[nums.length];
        List<Integer> numsList = new ArrayList<>();
        int []positiveMap = new int[201];
        int temp;

        for(i = 0; i < nums.length; i = i + 1){
            temp = nums[i] + 100;
            positiveMap[temp] = positiveMap[temp] + 1;
            numsList.add(temp);
        }

        numsList.sort(new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                if (positiveMap[o1] == positiveMap[o2]) {
                    return (o1 - o2) * (-1);
                } else {
                    return positiveMap[o1] - positiveMap[o2];
                }
            }
        });
        
        i = 0;        
        for(int number: numsList){
            result[i++] = number - 100;
        }
        return result;
    }
}
```
