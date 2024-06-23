# Solution

```Java
class Solution {
    public String longestNiceSubstring(String s) {
        int n = s.length(), i, j;
        String result = "";
        String temp;
        for(i = 0; i < n; i = i + 1){
            for(j = i + 1; j <= n; j = j + 1){
                temp = s.substring(i, j);
                if(isNice(temp) && temp.length() > result.length()){
                    result = temp;
                }
            }
        }
        return result;
    }

    private boolean isNice(String s){
        boolean []lowerCase = new boolean[26];
        boolean []upperCase = new boolean[26];

        for(char c: s.toCharArray()){
            if(Character.isLowerCase(c)){
                lowerCase[c - 'a'] = true;
            }else {
                upperCase[c - 'A'] = true;
            }
        }
        int i;
        for(i = 0; i < 26; i = i + 1){
            if(lowerCase[i] != upperCase[i]){
                return false;
            }
        }

        return true;
    }
} 
```
