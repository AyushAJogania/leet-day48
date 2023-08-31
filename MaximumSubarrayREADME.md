# leet-day48

# Maximum Subarray Problem

## Problem Statement

Given an integer array `nums`, you need to find the contiguous subarray with the largest sum and return the sum.

### Example 1:

Input: `nums = [-2,1,-3,4,-1,2,1,-5,4]`
Output: `6`
Explanation: The subarray `[4,-1,2,1]` has the largest sum 6.

## Approach

We can solve this problem using Kadane's algorithm, which is a dynamic programming approach. The key idea is to keep track of two variables: `currentSum` and `maxSum`.

1. Initialize both `currentSum` and `maxSum` with the value of the first element of the array.
2. Traverse through the array starting from the second element.
3. For each element, calculate the maximum of the current element and the sum of the current element and `currentSum`. Update `currentSum` with this value.
4. Update `maxSum` with the maximum value between the current `maxSum` and `currentSum`.
5. Continue this process for all elements in the array.
6. Finally, `maxSum` will hold the answer, which represents the maximum subarray sum.

## Code

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int n = nums.size();
        int maxSum = nums[0];  // Initialize maxSum with the first element of the array
        int currentSum = nums[0];  // Initialize currentSum with the first element
        
        for (int i = 1; i < n; ++i) {
            // Calculate the maximum between the current element and the sum of current element and previous sum
            currentSum = max(nums[i], currentSum + nums[i]);
            // Update maxSum if the currentSum is greater
            maxSum = max(maxSum, currentSum);
        }
        
        return maxSum;
    }
};
```

## Complexity Analysis

- Time Complexity: O(n)
  - We iterate through the input array once, performing constant time operations for each element.
- Space Complexity: O(1)
  - We use only a constant amount of extra space to store variables `currentSum` and `maxSum`.

## Conclusion

The Kadane's algorithm provides an efficient way to find the maximum subarray sum in a given array. By keeping track of the current sum and the maximum sum encountered so far, we can solve this problem in linear time complexity. This approach is widely used and is considered a standard algorithmic technique for solving such problems.
