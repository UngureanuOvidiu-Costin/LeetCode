# Solution

## Intuition

!!! Disclaimer: This solution has the space complexity of O(1) !!! Many solutions on the internet will say that is has O(N^2), which is wrong!!!
I'm gonna be honest, I had to google math formula but then I thought that we can write `a + b + c = d` as `a + b = d - c`.

## Approach

## Complexity

### Time complexity

    -   We note nums.length with N
    -   First loop takes O(N -2) which is O(N) as it goes from 1 to N
    -   Second and third loops take a total of almost N iterations in worst case because we start from 0 to i and from i+2 to N which is N - 2 ( 0 to N without i and i + 1).
    -   The result is the O(N) * O(N) = O(N^2) worst case.

### Space complexity

    -   As i, j, dMinusC, counter use constant space, they lead to O(1)
    -   From constrainst we know that the numbers are in the interval 1 <= nums[i] <= 100, this is why we make an array of lenght 201. The array will contain all possible sums of thow numbers in this interval. Even if N ~= Infinite, the size of this array will remain the same due to the constraints. This means that this is also O(1).
    -   Total space complexity: O(1) + O(1) = O(1).

```Java
class Solution {
    public int countQuadruplets(int[] nums) {
        int []aAndBSum = new int[201];
        int i, j, k, dMinusC, counter = 0;

        for(i = 1; i < nums.length - 2; i = i + 1) {

            for(j = 0; j < i; j = j + 1) {
                aAndBSum[nums[i] + nums[j]] = aAndBSum[nums[i] + nums[j]] + 1;
            }

            for(j = i + 2; j < nums.length; j = j + 1) {
                dMinusC =nums[j] - nums[i + 1];
                if(dMinusC >= 0) {
                    counter = counter + aAndBSum[dMinusC];
                }
            }
        }
        return counter;
    }
}
```
