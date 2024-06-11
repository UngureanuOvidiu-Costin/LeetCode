
Beats 99% of other users xD

```Java
class Solution {
    public String destCity(List<List<String>> paths) {
        HashMap<String, String> routes = new HashMap<>();

        for(List<String> innerList : paths){
            if(!routes.containsKey(innerList.get(0))){
                routes.put(innerList.get(0), innerList.get(1));
            }
        }

        String toSearch = paths.get(0).get(0);
        while(routes.containsKey(toSearch)){
            toSearch = routes.get(toSearch);
        }

        return toSearch;
    }
}
```
