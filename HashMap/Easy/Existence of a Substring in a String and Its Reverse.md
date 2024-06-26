# Solution

```Java
class Solution {
    public boolean isSubstringPresent(String s) {
        StringBuilder input1 = new StringBuilder();
        input1.append(s);
        input1.reverse();
        int i;
        Set<String> substrings = new HashSet<>();
        
        for(i = 0; i < s.length() - 1; i = i + 1) {
            substrings.add(s.substring(i, i + 2));
        }

        for(String substr: substrings) {
            if(input1.indexOf(substr) != -1) {
                return true;
            }
        }

        return false;
    }
}
```
