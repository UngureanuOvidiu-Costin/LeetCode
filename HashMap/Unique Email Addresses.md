```Java
class Solution {
    public int numUniqueEmails(String[] emails) {
        String temp = "";
        int i;
        HashMap<String, Integer> hashMap = new HashMap<>();

        for(i = 0; i < emails.length; i = i + 1){
            temp = emails[i].replaceAll("\\.(?=[^@]*@)", "").replaceAll("\\+.+@", "@");
            hashMap.put(temp, hashMap.getOrDefault(temp, 0) + 1);
            System.out.println(temp);
        }

        return hashMap.keySet().size();
    }
}
```
