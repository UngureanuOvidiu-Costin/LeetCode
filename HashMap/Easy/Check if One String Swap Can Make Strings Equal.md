# Solution

```Java
class Solution {
    public boolean areAlmostEqual(String s1, String s2) {

        int counter = 0;
        int firstPosition = -1; 
        int secondPosition = -1;
        int i;

        for(i = 0; i < s1.length(); i++){
            if(s1.charAt(i) != s2.charAt(i)){
                counter++;
                if(firstPosition == -1){
                    firstPosition = i;
                }else if(secondPosition == -1){
                    secondPosition = i;
                } else{
                    return false;
                }
            }
        }

        if(counter == 0){
            return true;
        }

        if(counter == 2){
            if(s1.charAt(firstPosition) != s2.charAt(secondPosition) ||
                s1.charAt(secondPosition) != s2.charAt(firstPosition)){
                return false;
            }else{
                return true;
            }
        }

        return false;
    }
}
```
