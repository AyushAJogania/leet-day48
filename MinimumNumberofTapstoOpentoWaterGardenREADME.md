# leet-day48

# Minimum Number of Taps to Water the Garden

## Problem Description

You are given a 0-indexed integer array `ranges` of length `n + 1` where `ranges[i]` (0-indexed) means the i-th tap can water the area `[i - ranges[i], i + ranges[i]]` if it was open. The goal is to determine the minimum number of taps that should be open to water the entire garden. If the garden cannot be watered, return -1.

## Example

**Input:**
```
n = 5
ranges = [3,4,1,1,0,0]
```

**Output:**
```
1
```

**Explanation:**
The tap at point 1 can cover the interval [-3,5], which is the entire garden. Therefore, only one tap needs to be open to water the entire garden.

## Approach

1. **Interval Representation:** We represent each tap as an interval `[left, right]` where `left = i - ranges[i]` and `right = i + ranges[i]`.

2. **Sorting Intervals:** We sort the intervals based on their left ends to help process them sequentially.

3. **Greedy Selection:** Starting from the leftmost interval, we select the tap that covers the farthest right end. This maximizes the coverage with the minimum number of taps.

4. **Checking Gaps:** While processing intervals, if we find a gap between intervals that cannot be covered, we return -1 as it's not possible to cover the entire garden.

5. **Counting Taps:** We keep track of the number of taps used and update the current end to the chosen tap's right end. We repeat this process until we cover the entire garden.

## Detailed Steps

1. Create a vector of pairs, `intervals`, where each pair contains the left end `i - ranges[i]` and the right end `i + ranges[i]` of the interval.

2. Sort the `intervals` vector in ascending order based on the left end.

3. Initialize `ans` to track the minimum number of taps required and `currEnd` to track the current end that is covered.

4. Initialize a variable `nextEnd` to track the right end of the interval that can be chosen next.

5. Iterate through the sorted intervals using a pointer `i`.
   - While `i` is within the valid range and the left end of the interval is less than or equal to `currEnd`, update `nextEnd` with the maximum of the current interval's right end and `nextEnd`. Increment `i` to move to the next interval.
   - If `currEnd` becomes equal to `nextEnd`, return -1 as it means there's a gap that cannot be covered.

6. Update `currEnd` with `nextEnd` and increment `ans`.

7. Repeat step 5 and 6 until either we cover the entire garden or `i` goes out of bounds.

8. If `currEnd` is greater than or equal to `n`, return `ans`. Otherwise, return -1 as there are gaps that cannot be covered.

## Complexity Analysis

- Time complexity: O(n * log(n)) due to the sorting operation.
- Space complexity: O(n) for the intervals array and other variables.

