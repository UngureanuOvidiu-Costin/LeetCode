# Solution

```Java
class Solution {
    public int countBalls(int lowLimit, int highLimit) {
        HashMap<Integer, Integer> frequency = new HashMap<Integer, Integer>();
        int ball, tempSum, max = 0, result = 0;
        for(ball = lowLimit; ball <= highLimit; ball = ball + 1){
            tempSum = sumOfDigits(ball);
            frequency.put(tempSum, frequency.getOrDefault(tempSum, 0) + 1);
            if(max < frequency.get(tempSum)){
                max = frequency.get(tempSum);
            }
        }

        return max;
    }

    int sumOfDigits(int number)  {
        int sum = 0;  
        
        while (number != 0)  {
            sum = sum + number % 10;  
            number = number/10;  
        }
        return sum;  
    }  
}
```
