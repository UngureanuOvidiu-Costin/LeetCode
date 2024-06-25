# Solution

```Java
class Solution {
    public int numDifferentIntegers(String word) {
        int i;
        Set<String> uniqueNumbers = new HashSet<String>();
        String temp = "";
        for(i = 0; i < word.length(); i = i + 1) {
            while(Character.isDigit(word.charAt(i))) {
                temp = temp + word.charAt(i);
                i = i + 1;
                if(i >= word.length()){
                    break;
                }
            }
            if(!temp.isEmpty()) {
                uniqueNumbers.add(removeLeadingZeroes(temp));
            }
            temp = "";
        }

        return uniqueNumbers.size();
    }

    public String removeLeadingZeroes(String str) {
        int length = str.length();
        if (length == 1)
            return str;
        int start = 0;
        while (start < length - 1) {
            if (str.charAt(start) != '0')
                break;
            start++;
        }
        return str.substring(start);
    }
}
```
