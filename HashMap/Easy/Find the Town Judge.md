```Java
class Solution {
    public int findJudge(int n, int[][] trust) {
        HashMap<Integer, Integer> trustCount = new HashMap<>();
        HashSet<Integer> possibleJudges = new HashSet<>();

        if(trust.length == 0 && n == 1){
            return 1;
        }

        if(trust.length == 0 && n == 2){
            return -1;
        }

        for (int[] relation : trust) {
            trustCount.put(relation[1], trustCount.getOrDefault(relation[1], 0) + 1);
            possibleJudges.add(relation[0]);
        }

        for (int person : trustCount.keySet()) {
            if (trustCount.get(person) == n - 1 && !possibleJudges.contains(person)) {
                return person;
            }
        }

        return -1;
    }
}
```
