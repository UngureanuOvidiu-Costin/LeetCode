# Intuition

The problem involves calculating the average waiting time for customers at a restaurant. Each customer has a specific arrival time and time needed for their order to be completed. The goal is to find the total waiting time and compute the average.

## Approach

1. **Initialization**:
   - Initialize a variable `sumOfTime` to accumulate the total waiting time.
   - Set `previousTime` to the time when the first customer finishes.
   - Add the waiting time for the first customer to `sumOfTime`.

2. **Iteration**:
   - Loop through the remaining customers.
   - For each customer, check if the previous customer's finish time is greater than the current customer's arrival time.
     - If so, the current customer has to wait until the previous customer is finished.
     - Add the waiting time (difference between previous finish time and current arrival time plus current order time) to `sumOfTime`.
     - Update `previousTime` to include the current order time.
   - If the previous customer's finish time is less than or equal to the current customer's arrival time:
     - The current customer can start immediately.
     - Add the current order time to `sumOfTime`.
     - Update `previousTime` to the current customer's finish time.

3. **Return**:
   - Return the average waiting time by dividing `sumOfTime` by the number of customers.

## Complexity

- **Time complexity**: O(n), where n is the number of customers. We traverse the list of customers once.

- **Space complexity**: O(1), as we are using a constant amount of extra space.

## Code

```Java
class Solution {
    public double averageWaitingTime(int[][] customers) {
        double sumOfTime = 0;
        int i, previousTime = customers[0][0] + customers[0][1];
        sumOfTime = customers[0][1];

        for(i = 1; i < customers.length; i = i + 1) {
            if(previousTime > customers[i][0]) {
                sumOfTime = sumOfTime + (previousTime - customers[i][0] +customers[i][1]); 
                previousTime = previousTime + customers[i][1];
            } else {
                sumOfTime += customers[i][1];
                previousTime = customers[i][0] + customers[i][1];
            }
        }

        return sumOfTime / customers.length;
    }
}
```
