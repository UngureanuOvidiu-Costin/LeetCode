# Solution

```Java
class Solution {
    public int secondHighest(String s) {
        Set<Integer> digits = new HashSet<>();
        int i;
        for(i = 0; i < s.length(); i = i + 1){
            Character c = s.charAt(i);
            if(Character.isDigit(c)){
                digits.add(Character.getNumericValue(c));
            }
        }

        List<Integer> digitsSorted = new ArrayList<>(digits);
        Collections.reverse(digitsSorted);

        if(digitsSorted.size() <= 1){
            return -1;
        }else {
            return digitsSorted.get(1);
        }
    }
}
```
