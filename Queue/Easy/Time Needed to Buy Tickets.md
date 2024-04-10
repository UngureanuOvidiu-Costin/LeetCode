```Java
class Solution {
    public int timeRequiredToBuy(int[] tickets, int k) {
        int stop = 0;
        int i;
        while(tickets[k] != 0) {
            for (i = 0; i < tickets.length; i = i + 1) {
                if(tickets[i]!=0){
                    tickets[i]--;
                    stop++;
                }
                if(tickets[k] ==0){
                    break;
                }
            }
        }
        return stop;
    }
}
```
