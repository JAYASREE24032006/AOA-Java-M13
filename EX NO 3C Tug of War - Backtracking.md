
# EX 3C Tug of War problem - Backtracking.
## DATE: 08.10.25
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm
1. Start the program and read the number of elements n, then input n integers into the array nums.
2. Calculate the total sum of all elements in the array.
3. If the total sum is odd, print false (since it cannot be divided equally).
4. Set the target as half of the total sum and create a boolean array dp to track possible subset sums.
5. Use dynamic programming to fill the dp array and finally print true if a subset with the target sum exists, else false.

## Program:
```
/*
Program to implement Reverse a String
Developed by: JAYASREE R
Register Number: 212223040074
*/

import java.util.Scanner;
public class Solution {
    public boolean canPartition(int[] nums) {
        if (nums.length == 0)
            return false;
        int totalSum = 0;
        for (int num : nums) {
            totalSum += num;
        }
        if (totalSum % 2 != 0)
            return false;
        int subSetSum = totalSum / 2;
        boolean[] dp = new boolean[subSetSum + 1];
        dp[0] = true;
        for (int curr : nums) {
            for (int j = subSetSum; j >= curr; j--) {
                dp[j] |= dp[j - curr];
            }
        }
        return dp[subSetSum];
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        boolean canBePartitioned = sol.canPartition(nums);
        System.out.println(canBePartitioned);
    }
}

```

## Output:

<img width="398" height="227" alt="image" src="https://github.com/user-attachments/assets/4dd4fb7a-ac78-4bd8-85b9-080b08f4778f" />

## Result:
The program successfully implemented and the expected output is verified.
