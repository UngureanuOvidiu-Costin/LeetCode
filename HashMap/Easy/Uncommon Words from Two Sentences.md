```Java
class Solution {
    public String[] uncommonFromSentences(String s1, String s2) {
        HashMap<String, Integer> hashOccurence = new HashMap<>();
        List<String> result = new ArrayList<>();

        String[] s1Array = s1.split(" ");
        String[] s2Array = s2.split(" ");

        for(String s: s1Array){
            hashOccurence.put(s, hashOccurence.getOrDefault(s, 0) + 1);
        }

        for(String s: s2Array){
            hashOccurence.put(s, hashOccurence.getOrDefault(s, 0) + 1);
        }
        
        for(String s: hashOccurence.keySet()){
            if(hashOccurence.get(s) == 1){
                result.add(s);
            }
        }
        
        return result.toArray(new String[0]);
    }
}
```
