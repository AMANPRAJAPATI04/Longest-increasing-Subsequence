# Longest-increasing-Subsequence
The Longest Increasing Subsequence (LIS) problem is a classic problem in computer science. The goal is to find the length of the longest subsequence of a given sequence such that all elements of the subsequence are sorted in increasing order.
# Longest Increasing Subsequence (LIS)

This repository contains a C++ implementation of the Longest Increasing Subsequence (LIS) problem. The goal of the LIS problem is to find the length of the longest subsequence of a given sequence such that all elements of the subsequence are sorted in increasing order.

## Problem Statement

Given an array of integers, the task is to find the length of the longest increasing subsequence.

### Input
- An array of integers.

### Output
- The length of the longest increasing subsequence.

## Code Explanation

The implementation uses a dynamic programming approach to solve the problem. The main steps are as follows:

1. **Initialization**: A `dp` array is created where `dp[i]` represents the length of the longest increasing subsequence that ends with the element at index `i`.

2. **DP Table Construction**:
   - Iterate through each element in the array.
   - For each element, check all previous elements to see if they can form an increasing subsequence.
   - If `arr[j] < arr[i]`, update `dp[i]` as `dp[i] = max(dp[i], dp[j] + 1)`.

3. **Result**: The length of the longest increasing subsequence is found by taking the maximum value from the `dp` array.

## Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

// Function to find the length of the Longest Increasing Subsequence
int longestIncreasingSubsequence(const vector<int>& arr) {
    int n = arr.size();
    if (n == 0) return 0;

    // Create a DP array initialized to 1
    vector<int> dp(n, 1);

    // Fill the DP array
    for (int i = 1; i < n; i++) {
        for (int j = 0; j < i; j++) {
            if (arr[j] < arr[i]) {
                dp[i] = max(dp[i], dp[j] + 1);
            }
        }
    }

    // The length of the longest increasing subsequence is the maximum value in dp
    return *max_element(dp.begin(), dp.end());
}

int main() {
    vector<int> arr = {10, 22, 9, 33, 21, 50, 41, 60, 80};
    
    int length = longestIncreasingSubsequence(arr);
    cout << "Length of Longest Increasing Subsequence: " << length << endl;

    return 0;
}
