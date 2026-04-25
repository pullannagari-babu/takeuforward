Intuition

To find the longest subarray with a sum of 𝑘, we'll check the sum of every possible subarray. We use two loops to pick all possible starting and ending indices, and another loop to calculate the sum of each subarray. If a subarray's sum is 𝑘, we compare its length to the longest one we've found so far. This way, we make sure to find the longest subarray with the sum of 𝑘.

Approach

First, we run a loop i to select every possible starting index of the subarray. These starting indices range from index 0 to n-1 (where n is the size of the array).
Inside this loop, we run another loop j to select the ending index of the subarray. For every subarray starting at index i, the ending index j can range from i to n-1.
Next, for each subarray starting from index i and ending at index j (i.e., arr[i...j]), we run an additional loop to calculate the sum of all the elements in that subarray.
If the sum equals k, we consider its length, which is (j-i+1). Among all such subarrays, we keep track of the maximum length by comparing all the lengths.
Dry Run

Image 1

1/5

Solution

C++:

#include <bits/stdc++.h>
using namespace std;

class Solution
{
public:
    int longestSubarray(vector<int> &nums, int k)
    {
        int n = nums.size(); 
        int maxLength = 0;

        // starting index
        for (int startIndex = 0; startIndex < n; startIndex++) { 
            // ending index
            for (int endIndex = startIndex; endIndex < n; endIndex++) { 
                /* add all the elements of 
                   subarray = nums[startIndex...endIndex]  */
                int currentSum = 0;
                for (int i = startIndex; i <= endIndex; i++) {
                    currentSum += nums[i];
                }

                if (currentSum == k)
                    maxLength = max(maxLength, endIndex - startIndex + 1);
            }
        }
        return maxLength;
    }
};

int main()
{
    vector<int> a = { -1, 1, 1 };
    int k = 1;

    // Create an instance of the Solution class
    Solution solution;
    // Function call to get the result
    int len = solution.longestSubarray(a, k);
    
    cout << "The length of the longest subarray is: " << len << "\n";
    return 0;
}


Java:

import java.util.*;

class Solution {
    public int longestSubarray(int[] nums, int k) {
        int n = nums.length; 
        int maxLength = 0;

        // starting index
        for (int startIndex = 0; startIndex < n; startIndex++) { 
            // ending index
            for (int endIndex = startIndex; endIndex < n; endIndex++) { 
                /* add all the elements of 
                   subarray = nums[startIndex...endIndex]  */
                int currentSum = 0;
                for (int i = startIndex; i <= endIndex; i++) {
                    currentSum += nums[i];
                }

                if (currentSum == k) {
                    maxLength = Math.max(maxLength, endIndex - startIndex + 1);
                }
            }
        }
        return maxLength;
    }

    public static void main(String[] args) {
        int[] nums = { -1, 1, 1 };
        int k = 1;

        // Create an instance of the Solution class
        Solution solution = new Solution();
        // Function call to get the result
        int len = solution.longestSubarray(nums, k);
        
        System.out.println("The length of the longest subarray is: " + len);
    }
}

Python:

class Solution:
    def longestSubarray(self, nums, k):
        n = len(nums) 
        maxLength = 0

        # starting index
        for startIndex in range(n):
            # ending index
            for endIndex in range(startIndex, n):
                # add all the elements of 
                # subarray = nums[startIndex...endIndex]
                currentSum = 0
                for i in range(startIndex, endIndex + 1):
                    currentSum += nums[i]

                if currentSum == k:
                    maxLength = max(maxLength, endIndex - startIndex + 1)

        return maxLength

if __name__ == "__main__":
    nums = [-1, 1, 1]
    k = 1

    # Create an instance of the Solution class
    solution = Solution()
    # Function call to get the result
    length = solution.longestSubarray(nums, k)
    
    print("The length of the longest subarray is:", length)

JavaScript:

class Solution {
    longestSubarray(nums, k) {
        const n = nums.length;
        let maxLength = 0;

        // starting index
        for (let startIndex = 0; startIndex < n; startIndex++) {
            // ending index
            for (let endIndex = startIndex; endIndex < n; endIndex++) {
                /* add all the elements of 
                   subarray = nums[startIndex...endIndex] */
                let currentSum = 0;
                for (let i = startIndex; i <= endIndex; i++) {
                    currentSum += nums[i];
                }

                if (currentSum === k) {
                    maxLength = Math.max(maxLength, endIndex - startIndex + 1);
                }
            }
        }
        return maxLength;
    }
}

const nums = [-1, 1, 1];
const k = 1;

// Create an instance of the Solution class
const solution = new Solution();
// Function call to get the result
const length = solution.longestSubarray(nums, k);

console.log("The length of the longest subarray is:", length);

C#:
using System;

public class Solution
{
    public int LongestSubarray(int[] nums, int k)
    {
        int n = nums.Length;
        int maxLength = 0;

        // starting index
        for (int startIndex = 0; startIndex < n; startIndex++)
        {
            // ending index
            for (int endIndex = startIndex; endIndex < n; endIndex++)
            {
                /* add all the elements of 
                   subarray = nums[startIndex...endIndex] */
                int currentSum = 0;
                for (int i = startIndex; i <= endIndex; i++)
                {
                    currentSum += nums[i];
                }

                if (currentSum == k)
                {
                    maxLength = Math.Max(maxLength, endIndex - startIndex + 1);
                }
            }
        }
        return maxLength;
    }
}

public class Program
{
    public static void Main(string[] args)
    {
        int[] nums = { -1, 1, 1 };
        int k = 1;

        // Create an instance of the Solution class
        Solution solution = new Solution();
        // Function call to get the result
        int length = solution.LongestSubarray(nums, k);

        Console.WriteLine("The length of the longest subarray is: " + length);
    }
}

Go:
package main

import (
	"fmt"
	"math"
)

// Function to find the longest subarray with a sum equal to k
func longestSubarray(nums []int, k int) int {
	n := len(nums)
	maxLength := 0

	// starting index
	for startIndex := 0; startIndex < n; startIndex++ {
		// ending index
		for endIndex := startIndex; endIndex < n; endIndex++ {
			// add all the elements of subarray = nums[startIndex...endIndex]
			currentSum := 0
			for i := startIndex; i <= endIndex; i++ {
				currentSum += nums[i]
			}

			if currentSum == k {
				maxLength = int(math.Max(float64(maxLength), float64(endIndex-startIndex+1)))
			}
		}
	}
	return maxLength
}

func main() {
	a := []int{-1, 1, 1}
	k := 1

	// Function call to get the result
	len := longestSubarray(a, k)

	fmt.Printf("The length of the longest subarray is: %d\n", len)
}


Complexity Analysis 

Time Complexity: O(N3), where N is the size of the array. Since we are using three nested loops, each running approximately N times.

Space Complexity: O(1), as we are not using any extra space.
