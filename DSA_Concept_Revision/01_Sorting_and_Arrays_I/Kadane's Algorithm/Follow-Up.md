
Solution:
C++:

#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    // Function to find maximum sum of subarrays and print the subarray having maximum sum
    int maxSubArray(vector<int>& nums) {
        
        // maximum sum
        long long maxi = LLONG_MIN; 
        
        // current sum of subarray
        long long sum = 0;
        
        // starting index of current subarray
        int start = 0; 
        
        // indices of the maximum sum subarray
        int ansStart = -1, ansEnd = -1; 
        
        // Iterate through the array
        for (int i = 0; i < nums.size(); i++) {
            
            // update starting index if sum is reset
            if (sum == 0) {
                start = i;
            }
            
            // add current element to the sum
            sum += nums[i]; 
            
            /* Update maxi and subarray indice
            s if current sum is greater*/
            if (sum > maxi) {
                maxi = sum;
                ansStart = start;
                ansEnd = i;
            }
            
            // Reset sum to 0 if it becomes negative
            if (sum < 0) {
                sum = 0;
            }
        }
        
        // Printing the subarray
        cout << "The subarray is: [";
        for (int i = ansStart; i <= ansEnd; i++) {
            cout << nums[i] << " ";
        }
        cout << "]" << endl;
        
        // Return the maximum subarray sum found
        return maxi;
    }
};

int main() {
    vector<int> arr = { -2, 1, -3, 4, -1, 2, 1, -5, 4 };

    // Create an instance of Solution class
    Solution sol;

    int maxSum = sol.maxSubArray(arr);

    // Print the max subarray sum
    cout << "The maximum subarray sum is: " << maxSum << endl;

    return 0;
}

Java:

import java.util.*;

class Solution {
   // Function to find maximum sum of subarrays and print the subarray having maximum sum
    public int maxSubArray(int[] nums) {
        
        // maximum sum
        long maxi = Long.MIN_VALUE; 
        
        // current sum of subarray
        long sum = 0; 
        
        // starting index of current subarray
        int start = 0; 
        
        // indices of the maximum sum subarray
        int ansStart = -1, ansEnd = -1; 
        
        // Iterate through the array
        for (int i = 0; i < nums.length; i++) {
            
            // update starting index if sum is reset
            if (sum == 0) {
                start = i;
            }
            
            // add current element to the sum
            sum += nums[i]; 
            
            /* Update maxi and subarray indices
            if current sum is greater */
            if (sum > maxi) {
                maxi = sum;
                ansStart = start;
                ansEnd = i;
            }
            
            // Reset sum to 0 if it becomes negative
            if (sum < 0) {
                sum = 0;
            }
        }
        
        // Printing the subarray
        System.out.print("The subarray is: [");
        for (int i = ansStart; i <= ansEnd; i++) {
            System.out.print(nums[i] + " ");
        }
        System.out.println("]");

        // Return the maximum subarray sum found
        return (int) maxi;
    }

    public static void main(String[] args) {
        int[] arr = { -2, 1, -3, 4, -1, 2, 1, -5, 4 };

        // Create an instance of Solution class
        Solution sol = new Solution();

        int maxSum = sol.maxSubArray(arr);

        // Print the max subarray sum
        System.out.println("The maximum subarray sum is: " + maxSum);
    }
}

Python:

from typing import List

class Solution:
    # Function to find maximum sum of subarrays and print the subarray having maximum sum
    def maxSubArray(self, nums: List[int]) -> int:
        
        # maximum sum
        maxi = float('-inf') 
        
        # current sum of subarray
        sum = 0 
        
        # starting index of current subarray
        start = 0 
        
        # indices of the maximum sum subarray
        ansStart = -1
        ansEnd = -1
        
        # Iterate through the array
        for i in range(len(nums)):
            
            # update starting index if sum is reset
            if sum == 0:
                start = i
            
            # add current element to the sum
            sum += nums[i] 
            
            """ Update maxi and subarray indices
            if current sum is greater """
            if sum > maxi:
                maxi = sum
                ansStart = start
                ansEnd = i
            
            # Reset sum to 0 if it becomes negative
            if sum < 0:
                sum = 0
        
        # Printing the subarray
        print("The subarray is: [", end="")
        for i in range(ansStart, ansEnd + 1):
            print(nums[i], end=" ")
        print("]")

        # Return the maximum subarray sum found
        return maxi

if __name__ == "__main__":
    arr = [ -2, 1, -3, 4, -1, 2, 1, -5, 4 ]

    # Create an instance of Solution class
    sol = Solution()

    maxSum = sol.maxSubArray(arr)

    # Print the max subarray sum
    print(f"The maximum subarray sum is: {maxSum}")

JavaScript:

class Solution {
    /* Function to find maximum sum of subarrays and
    print the subarray having maximum sum */
    maxSubArray(nums) {
        
        // maximum sum
        let maxi = Number.MIN_SAFE_INTEGER; 
        
        // current sum of subarray
        let sum = 0;
        
        // starting index of current subarray
        let start = 0; 
        
        // indices of the maximum sum subarray
        let ansStart = -1, ansEnd = -1; 
        
        // Iterate through the array
        for (let i = 0; i < nums.length; i++) {
            
            // update starting index if sum is reset
            if (sum === 0) {
                start = i;
            }
            
            // add current element to the sum
            sum += nums[i]; 
            
            /* Update maxi and subarray indices
            if current sum is greater*/
            if (sum > maxi) {
                maxi = sum;
                ansStart = start;
                ansEnd = i;
            }
            
            // Reset sum to 0 if it becomes negative
            if (sum < 0) {
                sum = 0;
            }
        }
        
        // Printing the subarray
        let subarray = [];
        for (let i = ansStart; i <= ansEnd; i++) {
            subarray.push(nums[i]);
        }
        console.log("The subarray is: [" + subarray.join(" ") + "]");
        
        // Return the maximum subarray sum found
        return maxi;
    }
}

// Main
let arr = [ -2, 1, -3, 4, -1, 2, 1, -5, 4 ];

// Create an instance of Solution class
let sol = new Solution();

let maxSum = sol.maxSubArray(arr);

// Print the max subarray sum
console.log("The maximum subarray sum is: " + maxSum);

C#:

using System;
using System.Collections.Generic;

class Solution {
    /* Function to find maximum sum of subarrays and
    print the subarray having maximum sum */
    public int MaxSubArray(List<int> nums) {
        
        // maximum sum
        long maxi = long.MinValue; 
        
        // current sum of subarray
        long sum = 0;
        
        // starting index of current subarray
        int start = 0; 
        
        // indices of the maximum sum subarray
        int ansStart = -1, ansEnd = -1; 
        
        // Iterate through the array
        for (int i = 0; i < nums.Count; i++) {
            
            // update starting index if sum is reset
            if (sum == 0) {
                start = i;
            }
            
            // add current element to the sum
            sum += nums[i]; 
            
            /* Update maxi and subarray indices
            if current sum is greater*/
            if (sum > maxi) {
                maxi = sum;
                ansStart = start;
                ansEnd = i;
            }
            
            // Reset sum to 0 if it becomes negative
            if (sum < 0) {
                sum = 0;
            }
        }
        
        // Printing the subarray
        Console.Write("The subarray is: [");
        for (int i = ansStart; i <= ansEnd; i++) {
            Console.Write(nums[i] + " ");
        }
        Console.WriteLine("]");
        
        // Return the maximum subarray sum found
        return (int)maxi;
    }
}

class Program {
    static void Main() {
        List<int> arr = new List<int> { -2, 1, -3, 4, -1, 2, 1, -5, 4 };

        // Create an instance of Solution class
        Solution sol = new Solution();

        long maxSum = sol.MaxSubArray(arr);

        // Print the max subarray sum
        Console.WriteLine("The maximum subarray sum is: " + maxSum);
    }
}
Go:

package main

import (
	"fmt"
	"math"
)

/* Function to find maximum sum of subarrays and
print the subarray having maximum sum */
func maxSubArray(nums []int) int {

	// maximum sum
	maxi := math.MinInt64

	// current sum of subarray
	sum := 0

	// starting index of current subarray
	start := 0

	// indices of the maximum sum subarray
	ansStart, ansEnd := -1, -1

	// Iterate through the array
	for i := 0; i < len(nums); i++ {

		// update starting index if sum is reset
		if sum == 0 {
			start = i
		}

		// add current element to the sum
		sum += nums[i]

		/* Update maxi and subarray indices
		if current sum is greater*/
		if sum > maxi {
			maxi = sum
			ansStart = start
			ansEnd = i
		}

		// Reset sum to 0 if it becomes negative
		if sum < 0 {
			sum = 0
		}
	}

	// Printing the subarray
	fmt.Print("The subarray is: [")
	for i := ansStart; i <= ansEnd; i++ {
		fmt.Print(nums[i], " ")
	}
	fmt.Println("]")

	// Return the maximum subarray sum found
	return maxi
}

func main() {
	arr := []int{-2, 1, -3, 4, -1, 2, 1, -5, 4}

	maxSum := maxSubArray(arr)

	// Print the max subarray sum
	fmt.Println("The maximum subarray sum is:", maxSum)
}
