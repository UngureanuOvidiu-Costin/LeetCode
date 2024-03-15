```Java
class OrderedStream {

    private HashMap<Integer, String> hasMapStream;
    private int ptr;
    private int max;

    public OrderedStream(int n) {
        this.hasMapStream = new HashMap<>();
        this.ptr = 1;
        this.max = 0;
    }

    public List<String> insert(int idKey, String value) {
        hasMapStream.put(idKey, value);
        if(idKey > max){
            max = idKey;
        } 

        List<String> result = new ArrayList<>();
        if(idKey == ptr){
            while (ptr <= max){
                if(hasMapStream.containsKey(ptr)){
                    result.add(hasMapStream.get(ptr));
                    ptr = ptr + 1;    
                }else {
                    break;
                }
            }
        }
        return result;
    }
}

/**
 * Your OrderedStream object will be instantiated and called as such:
 * OrderedStream obj = new OrderedStream(n);
 * List<String> param_1 = obj.insert(idKey,value);
 */
```
