# LeetCode Problem Writeup

## Problem Title: [Calculate Money in Leetcode Bank](https://leetcode.com/problems/calculate-money-in-leetcode-bank/description/)

### Problem Description:

*Hercy wants to save money for his first car. He puts money in the Leetcode bank every day.
He starts by putting in $1 on Monday, the first day. Every day from Tuesday to Sunday, he will put in $1 more than the day before. On every subsequent Monday, he will put in $1 more than the previous Monday.
Given n, return the total amount of money he will have in the Leetcode bank at the end of the nth day.*

### Approach:

Identify Weekly Pattern:
Recognize the repetitive weekly pattern in Hercy's contributions.

Calculate Full Weeks:
Determine the number of full weeks in the given time frame.
Use the fixed weekly contribution to calculate the total contribution for full weeks.

Calculate Remaining Days:
Determine any remaining days after accounting for full weeks.
Use a simple formula or method to calculate the contribution for these remaining days.

Combine Contributions:
Combine the contributions from full weeks and remaining days to obtain the overall total.

### Pseudocode:

```plaintext
function totalMoney(n):
    # Define the weekly contribution
    weekly_contribution = 28

    # Calculate the number of full weeks
    full_weeks = n / 7

    # Calculate the total contribution for full weeks
    total_full_weeks_contribution = full_weeks * weekly_contribution

    # Calculate the remaining days after accounting for full weeks
    remaining_days = n % 7

    # Calculate the contribution for the remaining days
    total_remaining_days_contribution = calculate_remaining_days_contribution(remaining_days)

    # Combine contributions from full weeks and remaining days
    total_contribution = total_full_weeks_contribution + total_remaining_days_contribution

    return total_contribution

function calculate_remaining_days_contribution(remaining_days):
    # Use a formula or loop to calculate the contribution for remaining days
    contribution = 0
    for day in 1 to remaining_days:
        contribution = contribution + day
    return contribution
```

## Code Implementation:

```
class Solution {
  public int totalMoney(int n) {
    int sevenSum = 28;
    int count = n / 7;
    int reminder = n % 7;

    int ssum = 0;
    if (count < 1) {
        int i;
        for (i = 1; i <= reminder; i++) {
            ssum = ssum + i;
        }
        return ssum;
    }
    
    int sum = count * (2 * 28 + (count - 1) * 7) / 2;
    int i;

    for (i = count+1; i <= count + reminder; i++) {
      sum = sum + i;
    }

    return sum;
  }
}
```

## Complexity Analysis:
![image](https://github.com/UngureanuOvidiu-Costin/LeetCode/assets/102877918/b08702d2-de18-40e7-bbca-8e16e97712e2)

**Time Complexity:**
Calculation of Full Weeks:

The calculation involves a simple division: full_weeks = n / 7.
Time Complexity: O(1) (constant time operation)
Calculation of Total Contribution for Full Weeks:
Multiplying the number of full weeks by the weekly contribution involves a simple multiplication: total_full_weeks_contribution = full_weeks * weekly_contribution.
Time Complexity: O(1) (constant time operation)

**Space Complexity:**

The space complexity is minimal as the pseudocode uses a constant amount of space to store variables, and there are no data structures with variable sizes.
Space Complexity: O(1) (constant space)
