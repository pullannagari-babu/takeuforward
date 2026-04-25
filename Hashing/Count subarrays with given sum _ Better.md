Intuition

If we carefully observe, we can notice that to get the sum of the current subarray, the only need is to add the current element (i.e., arr[j]) to the sum of the previous subarray, arr[i…j-1]. Assume the previous subarray is arr[i…j-1] and the current subarray is arr[i…j]. The sum of arr[i…j] can be calculated as:

Sum of arr[i…j] = (sum of arr[i…j-1]) + arr[j]

This way, eliminate the third loop, and while moving the j pointer, continuously calculate the sum.

Approach

First, run a loop (i) that will select every possible starting index of the subarray. The starting indices can range from index 0 to index n-1 (where n is the array size).
Inside this loop, run another loop (j) that will signify the ending index as well as the current element of the subarray. For every subarray starting from index i, the possible ending indices can range from index i to n-1 (where n is the array size).
Within the j loop, add the current element to the sum of the previous subarray, i.e., sum = sum + arr[j].
After calculating the sum, check if the sum is equal to the given k. If it is, increment the count.


C++:

#include <bits/stdc++.h>
using namespace std;

class Solution
{
public:
    int subarraySum(vector<int> &nums, int k)
    {
        int n = nums.size(); 
        // Number of subarrays
        int count = 0;

        // starting index
        for (int startIndex = 0; startIndex < n; startIndex++) { 
            int currentSum = 0;
            // ending index
            for (int endIndex = startIndex; endIndex < n; endIndex++) { 
                // calculate the sum of subarray [startIndex...endIndex]
                // sum of [startIndex..endIndex-1] + nums[endIndex]
                currentSum += nums[endIndex];

                // Increase the count if currentSum == k:
                if (currentSum == k)
                    count++;
            }
        }
        return count;
    }
};

int main() {
    Solution solution;
    vector<int> nums = {3, 1, 2, 4};
    int k = 6;
    // Function call to find the result
    int count = solution.subarraySum(nums, k);
    cout << "The number of subarrays is: " << count << "\n";
    return 0;
}

Java:


import java.util.*;

class Solution {
    public int subarraySum(int[] nums, int k) {
        int n = nums.length;
        // Number of subarrays
        int count = 0;

        // starting index
        for (int startIndex = 0; startIndex < n; startIndex++) {
            int currentSum = 0;
            // ending index
            for (int endIndex = startIndex; endIndex < n; endIndex++) {
                // calculate the sum of subarray [startIndex...endIndex]
                // sum of [startIndex..endIndex-1] + nums[endIndex]
                currentSum += nums[endIndex];

                // Increase the count if currentSum == k:
                if (currentSum == k)
                    count++;
            }
        }
        return count;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        int[] nums = {3, 1, 2, 4};
        int k = 6;
        // Function call to find the result
        int count = solution.subarraySum(nums, k);
        System.out.println("The number of subarrays is: " + count);
    }
}

Python:


class Solution:
    def subarraySum(self, nums, k):
        n = len(nums)
        # Number of subarrays
        count = 0

        # starting index
        for startIndex in range(n):
            currentSum = 0
            # ending index
            for endIndex in range(startIndex, n):
                # calculate the sum of subarray [startIndex...endIndex]
                # sum of [startIndex..endIndex-1] + nums[endIndex]
                currentSum += nums[endIndex]

                # Increase the count if currentSum == k:
                if currentSum == k:
                    count += 1
        return count

if __name__ == "__main__":
    solution = Solution()
    nums = [3, 1, 2, 4]
    k = 6
    # Function call to find the result
    count = solution.subarraySum(nums, k)
    print("The number of subarrays is:", count)

JavaScript:


class Solution {
    subarraySum(nums, k) {
        let n = nums.length;
        // Number of subarrays
        let count = 0;

        // starting index
        for (let startIndex = 0; startIndex < n; startIndex++) {
            let currentSum = 0;
            // ending index
            for (let endIndex = startIndex; endIndex < n; endIndex++) {
                // calculate the sum of subarray [startIndex...endIndex]
                // sum of [startIndex..endIndex-1] + nums[endIndex]
                currentSum += nums[endIndex];

                // Increase the count if currentSum == k:
                if (currentSum == k)
                    count++;
            }
        }
        return count;
    }
}

const solution = new Solution();
const nums = [3, 1, 2, 4];
const k = 6;
// Function call to find the result
const count = solution.subarraySum(nums, k);
console.log("The number of subarrays is:", count);

C#:

using System;

public class Solution
{
    public int SubarraySum(int[] nums, int k)
    {
        int n = nums.Length;
        // Number of subarrays
        int count = 0;

        // starting index
        for (int startIndex = 0; startIndex < n; startIndex++)
        {
            int currentSum = 0;
            // ending index
            for (int endIndex = startIndex; endIndex < n; endIndex++)
            {
                // calculate the sum of subarray [startIndex...endIndex]
                // sum of [startIndex..endIndex-1] + nums[endIndex]
                currentSum += nums[endIndex];

                // Increase the count if currentSum == k:
                if (currentSum == k)
                    count++;
            }
        }
        return count;
    }

public static void Main(string[] args)
    {
        Solution solution = new Solution();
        int[] nums = { 3, 1, 2, 4 };
        int k = 6;
        // Function call to find the result
        int count = solution.SubarraySum(nums, k);
        Console.WriteLine("The number of subarrays is: " + count);
    }
}

Go:

package main

import (
	"fmt"
)

// Function to count the number of subarrays whose sum is equal to k
func subarraySum(nums []int, k int) int {
	n := len(nums)
	// Number of subarrays
	count := 0

	// starting index
	for startIndex := 0; startIndex < n; startIndex++ {
		currentSum := 0
		// ending index
		for endIndex := startIndex; endIndex < n; endIndex++ {
			// calculate the sum of subarray [startIndex...endIndex]
			// sum of [startIndex..endIndex-1] + nums[endIndex]
			currentSum += nums[endIndex]

			// Increase the count if currentSum == k
			if currentSum == k {
				count++
			}
		}
	}
	return count
}

func main() {
	nums := []int{3, 1, 2, 4}
	k := 6

	// Function call to find the result
	count := subarraySum(nums, k)
	fmt.Printf("The number of subarrays is: %d\n", count)
}

Complexity Analysis 

Time Complexity: O(N2), where N is the size of the array. We are using two nested loops here, each running for approximately N times. Therefore, the time complexity will be approximately O(N2).

Space Complexity: O(1), as we are not using any extra space to solve this problem.
