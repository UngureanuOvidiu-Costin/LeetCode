```Java
class Solution {
    public int maxProfitAssignment(int[] difficulty, int[] profit, int[] worker) {
        List<int[]> jobs = new ArrayList<>();
        int jobsCount = difficulty.length;

        int i;
        for(i = 0; i < jobsCount; i = i + 1){
            jobs.add(new int[]{difficulty[i], profit[i]});
        }

        jobs.sort(Comparator.comparing(a -> a[0]));
        Arrays.sort(worker);

        int totalProfit = 0;
        int maxProfitPerWorker = 0;
        i = 0;
        for(int workerUnit: worker){
            while(i < jobsCount && jobs.get(i)[0] <= workerUnit){
                maxProfitPerWorker = Math.max(maxProfitPerWorker, jobs.get(i)[1]);
                i = i + 1;
            }
            totalProfit = totalProfit + maxProfitPerWorker;
        }
        return totalProfit;
    }
}
```