```Java
class MyHashMap {

    private final int[] hashMap;

    public MyHashMap() {
        this.hashMap = new int[1000001];
        Arrays.fill(hashMap, -1);
    }

    public void put(int key, int value) {
        this.hashMap[key] = value;
    }

    public int get(int key) {
        return this.hashMap[key];
    }

    public void remove(int key) {
        this.hashMap[key] = -1;
    }
}

/**
 * Your MyHashMap object will be instantiated and called as such:
 * MyHashMap obj = new MyHashMap();
 * obj.put(key,value);
 * int param_2 = obj.get(key);
 * obj.remove(key);
 */
```
