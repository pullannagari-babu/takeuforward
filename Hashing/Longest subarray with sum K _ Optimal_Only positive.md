Note that this approach is Only valid for positive numbers. As per the question, the elements in the array can be negative as well. This means submitting this code in the editorial will give you a wrong submission.

Intuition:

The idea is to solve the problem in linear time without using extra space. Since, we are only considered about the subarray, we can use two pointers and sliding window concept to find the required subarray. Assuming that all the elements in the array are positive, we can form a window representing the subarray with the following observations:

To increase the sum of the elements in window, we can expand the window by one element.
To decrease the sum of the elements in window, we can shrink the window by one element.

This is only possible if the elements in the array are positives. Because of these observations, we will be able to find the longest subarray with sum K provided all the elements in the array are positive.
Approach:

Two pointers (left and right) are used to maintain the current window of elements in the array.
A variable (sum) keeps track of the sum of the elements in the current window.
The right pointer expands the window by including new elements.
If the sum of the window exceeds k, the left pointer shrinks the window by removing elements from the start until the sum is less than or equal to k.
If the sum of the current window equals k, the maximum length of such a subarray is updated.
The process continues until the right pointer traverses the entire array.
The maximum length of the subarray with sum k is returned as the result.
Solution:

C++

#include <bits/stdc++.h>
using namespace std;

class Solution{
public:
    // Function to find the length of longest subarray having sum k
    int longestSubarray(vector<int> &nums, int k){
        int n = nums.size();
        
        // To store the maximum length of the subarray
        int maxLen = 0;
        
        // Pointers to mark the start and end of window
        int left = 0, right = 0;
        
        // To store the sum of elements in the window
        int sum = nums[0];
        
        // Traverse all the elements
        while(right < n) {
            
            // If the sum exceeds K, shrink the window
            while(left <= right && sum > k) {
                sum -= nums[left];
                left++;
            }
            
            // store the maximum length
            if(sum == k) {
                maxLen = max(maxLen, right - left + 1);
            }
            
            right++;
            if(right < n) sum += nums[right];
        }
        
        return maxLen;
    }
};

int main() {
	vector<int> nums = {10, 5, 2, 7, 1, 9};
    int k = 15;
    
	// Creating an object of Solution class
	Solution sol;

	/* Function call to find the length
	of longest subarray having sum k */
	int ans = sol.longestSubarray(nums, k);

	cout << "The length of longest subarray having sum k is: " << ans;

	return 0;
}

Java
import java.util.*;

class Solution {
    public int longestSubarray(int[] nums, int k) {
        int n = nums.length;

        // To store the maximum length of the subarray
        int maxLen = 0;

        // Pointers to mark the start and end of window
        int left = 0, right = 0;

        // To store the sum of elements in the window
        int sum = nums[0];

        // Traverse all the elements
        while (right < n) {

            // If the sum exceeds K, shrink the window
            while (left <= right && sum > k) {
                sum -= nums[left];
                left++;
            }

            // Store the maximum length
            if (sum == k) {
                maxLen = Math.max(maxLen, right - left + 1);
            }

            right++;
            if (right < n) sum += nums[right];
        }

        return maxLen;
    }
}

class Main {
    public static void main(String[] args) {
        int[] nums = {10, 5, 2, 7, 1, 9};
        int k = 15;

        // Creating an object of Solution class
        Solution sol = new Solution();

        /* Function call to find the length
        of longest subarray having sum k */
        int ans = sol.longestSubarray(nums, k);

        System.out.println("The length of longest subarray having sum k is: " + ans);
    }
}

Python
class Solution:
    # Function to find the length of longest subarray having sum k
    def longestSubarray(self, nums, k):
        n = len(nums)
        
        # To store the maximum length of the subarray
        maxLen = 0
        
        # Pointers to mark the start and end of window
        left = 0
        right = 0
        
        # To store the sum of elements in the window
        sum = nums[0]
        
        # Traverse all the elements
        while right < n:
            
            # If the sum exceeds K, shrink the window
            while left <= right and sum > k:
                sum -= nums[left]
                left += 1
            
            # Store the maximum length
            if sum == k:
                maxLen = max(maxLen, right - left + 1)
            
            right += 1
            if right < n:
                sum += nums[right]
        
        return maxLen


nums = [10, 5, 2, 7, 1, 9]
k = 15

# Creating an object of Solution class
sol = Solution()

# Function call to find the length
# of longest subarray having sum k
ans = sol.longestSubarray(nums, k)

print(f"The length of longest subarray having sum k is: {ans}")

JavaScript
class Solution {
    // Function to find the length of longest subarray having sum k
    longestSubarray(nums, k) {
        let n = nums.length;
        
        // To store the maximum length of the subarray
        let maxLen = 0;
        
        // Pointers to mark the start and end of window
        let left = 0, right = 0;
        
        // To store the sum of elements in the window
        let sum = nums[0];
        
        // Traverse all the elements
        while (right < n) {
            
            // If the sum exceeds K, shrink the window
            while (left <= right && sum > k) {
                sum -= nums[left];
                left++;
            }
            
            // Store the maximum length
            if (sum === k) {
                maxLen = Math.max(maxLen, right - left + 1);
            }
            
            right++;
            if (right < n) sum += nums[right];
        }
        
        return maxLen;
    }
}

// Input array and target sum
const nums = [10, 5, 2, 7, 1, 9];
const k = 15;

// Creating an object of Solution class
const sol = new Solution();

/* Function call to find the length
of longest subarray having sum k */
const ans = sol.longestSubarray(nums, k);

console.log(`The length of longest subarray having sum k is: ${ans}`);

C#
using System;

public class Solution
{
    // Function to find the length of longest subarray having sum k
    public int LongestSubarray(int[] nums, int k)
    {
        if (nums == null || nums.Length == 0)
        {
            return 0;
        }

        int n = nums.Length;

        // To store the maximum length of the subarray
        int maxLen = 0;

        // Pointers to mark the start and end of window
        int left = 0;
        int right = 0;

        // To store the sum of elements in the window
        long sum = nums[0];

        // Traverse all the elements
        while (right < n)
        {
            // If the sum exceeds K, shrink the window
            while (left <= right && sum > k)
            {
                sum -= nums[left];
                left++;
            }

            // Store the maximum length
            if (sum == k)
            {
                maxLen = Math.Max(maxLen, right - left + 1);
            }

            right++;
            if (right < n)
            {
                sum += nums[right];
            }
        }

        return maxLen;
    }
}

class Program
{
    public static void Main(string[] args)
    {
        // Input array and target sum
        int[] nums = { 10, 5, 2, 7, 1, 9 };
        int k = 15;

        // Creating an object of Solution class
        Solution sol = new Solution();

        /* Function call to find the length
           of longest subarray having sum k */
        int ans = sol.LongestSubarray(nums, k);

        Console.WriteLine($"The length of longest subarray having sum k is: {ans}");
    }
}
Go
package main

import (
	"fmt"
	"math"
)

// Function to find the length of longest subarray having sum k
func longestSubarray(nums []int, k int) int {
	n := len(nums)
	
	// To store the maximum length of the subarray
	maxLen := 0
	
	// Pointers to mark the start and end of window
	left, right := 0, 0
	
	// To store the sum of elements in the window
	sum := nums[0]
	
	// Traverse all the elements
	for right < n {
		
		// If the sum exceeds K, shrink the window
		for left <= right && sum > k {
			sum -= nums[left]
			left++
		}
		
		// store the maximum length
		if sum == k {
			maxLen = int(math.Max(float64(maxLen), float64(right - left + 1)))
		}
		
		right++
		if right < n {
			sum += nums[right]
		}
	}
	
	return maxLen
}

func main() {
	nums := []int{10, 5, 2, 7, 1, 9}
	k := 15
	
	// Function call to find the length of longest subarray having sum k
	ans := longestSubarray(nums, k)

	fmt.Printf("The length of longest subarray having sum k is: %d", ans)
}

Complexity Analysis:

Time Complexity: O(N), where N is the size of the array.
There are two pointers left and right which traverse the array at once taking linear time.

Space Complexity: O(1), as only a couple of variables are used.
