Intuition

In this approach, we will use the concept of prefix sums to solve the problem. The prefix sum of a subarray ending at index i is simply the sum of all the elements up to that index.

Observation:
https://static.takeuforward.org/premium/Hashing/FAQs/Count%20subarrays%20with%20given%20sum-dup/illustration-CpkDDYoy
Assume the prefix sum of a subarray ending at index 𝑖 is 𝑥. Within this subarray, we look for another subarray ending at 𝑖 whose sum is 𝑘. If such a subarray exists, the prefix sum of the remaining part must be 𝑥−𝑘. For a subarray ending at index 𝑖 with a prefix sum 𝑥, removing the segment with a prefix sum of 𝑥−𝑘 leaves a segment whose sum is 𝑘. The number of subarrays with sum 𝑘 is equal to the number of subarrays with a prefix sum of 𝑥−𝑘.

CountSubarray

Instead of directly searching for subarrays with sum 𝑘, we track the occurrence of each prefix sum using a map. The map stores each prefix sum along with its frequency. At each index 𝑖, we check the map to find how many times subarrays with the prefix sum 𝑥−𝑘 have occurred and add this number to our answer. This process is applied for all indices from 0 to 𝑛−1, where 𝑛 is the size of the array.

Approach

First, declare a map to store the prefix sums and their counts. Initially, set the value of 0 to 1 in the map to handle cases where a subarray equals the target sum k.
Now, run a loop from index 0 to n-1 (where n is the size of the array). For each index i, we will add the current element arr[i] to the prefix sum, calculate the required prefix sum x-k, add the occurrence of the prefix sum x-k (i.e., map[x-k]) to our answer, and store the current prefix sum in the map, increasing its count by 1.
Setting the initial value of 0 to 1 in the map is crucial for handling edge cases. For example, if the array is [3, -3, 1, 1, 1] and k is 3, at index 0, the prefix sum is 3, which equals k. The prefix sum of the part to be removed should be x-k = 3-3 = 0.
Without setting the value of 0 beforehand, the map would return 0 for the key 0, meaning we wouldn't count the subarray starting from the beginning correctly. By setting the initial value of 0 to 1, ensure that such subarrays are correctly counted from the start. This adjustment ensures that any subarray starting at the beginning of the array and equalling k is not overlooked.
Dry Run
https://static.takeuforward.org/premium/Hashing/FAQs/Count%20subarrays%20with%20given%20sum-dup/e1.png-A8cWgvBj
https://static.takeuforward.org/premium/Hashing/FAQs/Count%20subarrays%20with%20given%20sum-dup/e2.png-wPdb3qTl
https://static.takeuforward.org/premium/Hashing/FAQs/Count%20subarrays%20with%20given%20sum-dup/e3.png-dRJkivEh
https://static.takeuforward.org/premium/Hashing/FAQs/Count%20subarrays%20with%20given%20sum-dup/e4.png-1QOGEJaQ

1/4

Please refer to the video for complete dry-run.


C++

#include <bits/stdc++.h>
using namespace std;

class Solution
{
public:
    int subarraySum(vector<int> &nums, int k)
    {
        int n = nums.size(); 
        unordered_map<int, int> prefixSumMap;
        int currentPrefixSum = 0, subarrayCount = 0;

       // Setting 0 in the map.
        prefixSumMap[0] = 1; 
        for (int i = 0; i < n; i++) {
            // Add current element to the prefix sum:
            currentPrefixSum += nums[i];

            /*Calculate the value to 
            remove (currentPrefixSum - k)*/
            int sumToRemove = currentPrefixSum - k;

            /* Add the number of subarrays
             with the sum to be removed*/
            subarrayCount += prefixSumMap[sumToRemove];

            /* Update the count of current
            prefix sum in the map*/
            prefixSumMap[currentPrefixSum] += 1;
        }
        return subarrayCount;
    }
};

int main()
{
    // Create an instance of solution class
    Solution solution;
    vector<int> nums = {3, 1, 2, 4};
    int k = 6;
    // Function call to get the result
    int subarrayCount = solution.subarraySum(nums, k);
    cout << "The number of subarrays is: " << subarrayCount << "\n";
    return 0;
}

Java


import java.util.HashMap;

class Solution {
    public int subarraySum(int[] nums, int k) {
        int n = nums.length;
        HashMap<Integer, Integer> prefixSumMap = new HashMap<>();
        int currentPrefixSum = 0, subarrayCount = 0;

        // Setting 0 in the map.
        prefixSumMap.put(0, 1);
        for (int i = 0; i < n; i++) {
            // Add current element to the prefix sum:
            currentPrefixSum += nums[i];

            /* Calculate the value to remove
            (currentPrefixSum - k)*/
            int sumToRemove = currentPrefixSum - k;

            /* Add the number of subarrays 
            with the sum to be removed*/
            subarrayCount += prefixSumMap.getOrDefault(sumToRemove, 0);

            /*Update the count of current
            prefix sum in the map*/
            prefixSumMap.put(currentPrefixSum, prefixSumMap.getOrDefault(currentPrefixSum, 0) + 1);
        }
        return subarrayCount;
    }

    public static void main(String[] args) {
        // Create an instance of the Solution class
        Solution solution = new Solution();
        int[] nums = {3, 1, 2, 4};
        int k = 6;
        // Function call to get the result
        int subarrayCount = solution.subarraySum(nums, k);
        System.out.println("The number of subarrays is: " + subarrayCount);
    }
}

Python:


class Solution:
    def subarraySum(self, nums, k):
        n = len(nums)
        prefix_sum_map = {0: 1}
        current_prefix_sum = 0
        subarray_count = 0

        for i in range(n):
            # Add current element to the prefix sum:
            current_prefix_sum += nums[i]

            """Calculate the value to remove
           (current_prefix_sum - k)"""
            sum_to_remove = current_prefix_sum - k

            """ Add the number of subarrays 
            with the sum to be removed"""
            subarray_count += prefix_sum_map.get(sum_to_remove, 0)

            """ Update the count of  current
            prefix sum in the map"""
            prefix_sum_map[current_prefix_sum] = prefix_sum_map.get(current_prefix_sum, 0) + 1

        return subarray_count

if __name__ == "__main__":
    # Create an instance of the Solution class
    solution = Solution()
    nums = [3, 1, 2, 4]
    k = 6
    # Function call to get the result
    subarray_count = solution.subarraySum(nums, k)
    print("The number of subarrays is:", subarray_count)

JavaScript:


class Solution {
    subarraySum(nums, k) {
        let n = nums.length;
        let prefixSumMap = new Map();
        let currentPrefixSum = 0, subarrayCount = 0;

        // Setting 0 in the map.
        prefixSumMap.set(0, 1);
        for (let i = 0; i < n; i++) {
            // Add current element to prefix sum:
            currentPrefixSum += nums[i];

            /* Calculate the value to remove
            (currentPrefixSum - k)*/
            let sumToRemove = currentPrefixSum - k;

            /* Add the number of subarrays 
            with the sum to be removed*/
            subarrayCount += prefixSumMap.get(sumToRemove) || 0;

            /* Update the count of current 
            prefix sum in the map*/
            prefixSumMap.set(currentPrefixSum, (prefixSumMap.get(currentPrefixSum) || 0) + 1);
        }
        return subarrayCount;
    }
}

const solution = new Solution();
const nums = [3, 1, 2, 4];
const k = 6;
// Function call to get the result
const subarrayCount = solution.subarraySum(nums, k);
console.log("The number of subarrays is:", subarrayCount);

C#

using System;
using System.Collections.Generic;

class Solution
{
    public int SubarraySum(int[] nums, int k)
    {
        int n = nums.Length;
        var prefixSumMap = new Dictionary<int, int>();
        int currentPrefixSum = 0, subarrayCount = 0;

        // Setting 0 in the map.
        prefixSumMap[0] = 1;
        for (int i = 0; i < n; i++)
        {
            // Add current element to prefix sum:
            currentPrefixSum += nums[i];

            /* Calculate the value to remove
            (currentPrefixSum - k)*/
            int sumToRemove = currentPrefixSum - k;

            /* Add the number of subarrays 
            with the sum to be removed*/
            if (prefixSumMap.TryGetValue(sumToRemove, out int count))
            {
                subarrayCount += count;
            }

            /* Update the count of current 
            prefix sum in the map*/
            prefixSumMap.TryGetValue(currentPrefixSum, out int currentCount);
            prefixSumMap[currentPrefixSum] = currentCount + 1;
        }
        return subarrayCount;
    }

public static void Main(string[] args)
    {
        Solution solution = new Solution();
        int[] nums = { 3, 1, 2, 4 };
        int k = 6;
        // Function call to get the result
        int subarrayCount = solution.SubarraySum(nums, k);
        Console.WriteLine("The number of subarrays is: " + subarrayCount);
    }
}

Go

package main

import (
	"fmt"
)

// Function to count the number of subarrays with sum equal to k
func subarraySum(nums []int, k int) int {
	n := len(nums)
	prefixSumMap := make(map[int]int)
	currentPrefixSum := 0
	subarrayCount := 0

	// Setting 0 in the map to handle subarrays starting from index 0
	prefixSumMap[0] = 1

	for i := 0; i < n; i++ {
		// Add current element to the prefix sum
		currentPrefixSum += nums[i]

		// Calculate the value to remove (currentPrefixSum - k)
		sumToRemove := currentPrefixSum - k

		// Add the number of subarrays with the sum to be removed
		if val, exists := prefixSumMap[sumToRemove]; exists {
			subarrayCount += val
		}

		// Update the count of current prefix sum in the map
		prefixSumMap[currentPrefixSum]++
	}

	return subarrayCount
}

func main() {
	nums := []int{3, 1, 2, 4}
	k := 6

	// Function call to get the result
	subarrayCount := subarraySum(nums, k)
	fmt.Printf("The number of subarrays is: %d\n", subarrayCount)
}

Complexity Analysis 

Time Complexity: O(N) or O(NxlogN) depending on the map data structure used, where N is the size of the array. For example, if we use an unordered_map in C++, the time complexity will be O(N), but if we use a map, the time complexity will be O(NxlogN). The minimum complexity is O(N) as we are using a single loop to traverse the array.

Space Complexity: O(N) as we are using a map data structure.
