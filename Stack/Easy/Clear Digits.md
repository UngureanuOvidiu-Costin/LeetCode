```Java
class Solution {
    public String clearDigits(String s) {
        Stack<Character> stack = new Stack<>();
        int i;
        for(i = 0; i < s.length(); i = i + 1){
            if(!Character.isDigit(s.charAt(i))){
                stack.push(s.charAt(i));
            }else{
                if(!stack.isEmpty()){
                    stack.pop();
                }
            }
        }

        StringBuilder result = new StringBuilder();
        for(char c: stack){
            result.append(c);
        }

        return result.toString();
    }
}
```
