Highest Occurring Element in an Array
Given an array nums of n integers, find the most frequent element in it i.e., the element that occurs the maximum number of times. If there are multiple elements that appear a maximum number of times, find the smallest of them.



Please note that this section might seem a bit difficult without prior knowledge on what hashing is, we will soon try to add basics concepts for your ease! If you know the concepts already please go ahead to give a shot to the problem. Cheers!


Example 1

Input: nums = [1, 2, 2, 3, 3, 3]

Output: 3

Explanation: The number 3 appears the most (3 times). It is the most frequent element.

Example 2

Input: nums = [4, 4, 5, 5, 6]

Output: 4

Explanation: Both 4 and 5 appear twice, but 4 is smaller. So, 4 is the most frequent element.

Example 3

Input: nums = [2, 4, 3, 2, 5, 4]

Output:

2
Constraints

1 <= n <= 105
1 <= nums[i] <= 104

Intuition:
A brute-force way to solve this problem will be to use two loops:

First loop to iterate on the array, selecting an element.
Second loop to traverse the remaining array to find the occurrences of the selected element in the first loop.

Maintain a visited array to mark the elements to keep track of duplicate elements that were already taken into account.
Approach:
Initialize a visited array of boolean type having size n, where n is the size of the array with all elements set to false. Also, declare the following variables :
maxFreq - to store the frequency of the highest occurring element.
maxEle - to store the highest occurring element in the array.
In the first loop, start iterating on the elements of the array selecting one element at a time.
In the second loop, iterate on the rest portion of the array and count the frequency (number of occurrences) of the selected element. And every time, the same element is found, mark the corresponding index in the visited array as true.
If the frequency of the current element is found greater than maxFreq, update maxFreq and maxEle with the new frequency and new element respectively.
If the frequency of the current element is the same as maxFreq, store the smaller of maxEle and the current element in maxEle.
Before starting the second loop, check if the element is marked as unvisited. Skip the element if it is visited because its frequency has already been taken into consideration.
Dry Run:
<img width="950" height="660" alt="1" src="https://github.com/user-attachments/assets/0f673a7b-a630-48d3-8446-c69baa7cef3b" />
<img width="950" height="660" alt="2" src="https://github.com/user-attachments/assets/709099cb-22a6-4af9-b228-ba73880f0bd3" />
<img width="950" height="660" alt="3" src="https://github.com/user-attachments/assets/2e8beb18-8d34-48dd-ba14-1906b4d2d8a1" />
<img width="950" height="660" alt="4" src="https://github.com/user-attachments/assets/328d578d-3522-432a-bccb-7c4afd82d45e" />
<img width="950" height="659" alt="5" src="https://github.com/user-attachments/assets/ba0f24fa-322a-4367-9a39-4741f79a5b94" />
<img width="950" height="659" alt="6" src="https://github.com/user-attachments/assets/aa80e219-5ce9-474e-bf6b-8119804ecfd1" />
<img width="950" height="659" alt="7" src="https://github.com/user-attachments/assets/37a1186e-8fa0-4e10-a1df-81b08cda874d" />
<img width="950" height="659" alt="8" src="https://github.com/user-attachments/assets/70c96da5-576d-4248-8713-f8a2d4ccaa52" />
<img width="950" height="659" alt="9" src="https://github.com/user-attachments/assets/30a29d73-8765-4607-b53a-df03ba95f5b3" />

1/9

Solution:
C:

#include <stdio.h>
#include <stdbool.h>

// Function to find the most frequent element
int mostFrequentElement(int nums[], int n) {
    int maxFreq = 0;
    int maxEle = nums[0];
    
    // Boolean array to keep track of processed elements
    bool visited[n];
    for (int i = 0; i < n; i++) 
		visited[i] = false;
    
    for (int i = 0; i < n; i++) {
        if (visited[i]) 
			continue;
        
        int freq = 0;
        // Count occurrences of nums[i]
        for (int j = i; j < n; j++) {
            if (nums[i] == nums[j]) {
                freq++;
                visited[j] = true;
            }
        }
        
        // Update logic for max frequency
        if (freq > maxFreq) {
            maxFreq = freq;
            maxEle = nums[i];
        } else if (freq == maxFreq) {
            // Find the minimum element in case of a tie
            if (nums[i] < maxEle) {
                maxEle = nums[i];
            }
        }
    }
    return maxEle;
}

int main() {
    int nums[] = {4, 4, 5, 5, 6};
    int n = sizeof(nums) / sizeof(nums[0]);
    
    int ans = mostFrequentElement(nums, n);
    
    printf("The highest occurring element in the array is: %d\n", ans);
    
    return 0;
}


C++

class Solution {
    /* Function to get the highest 
    occurring element in array nums */
    mostFrequentElement(nums) {
        
        // Variable to store the size of array
        let n = nums.length;
        
        // Variable to store maximum frequency
        let maxFreq = 0; 
        
        /* Variable to store element 
        with maximum frequency */
        let maxEle = 0;
        
        // Visited array
        let visited = new Array(n).fill(false);
        
        // First loop
        for (let i = 0; i < n; i++) {
            // Skip second loop if already visited
            if (visited[i]) continue;
            
            /* Variable to store frequency
            of current element */
            let freq = 0;
            
            // Second loop
            for (let j = i; j < n; j++) {
                if (nums[i] == nums[j]) {
                    freq++;
                    visited[j] = true;
                }
            }
            
            /* Update variables if new element having 
            highest frequency is found */
            if (freq > maxFreq) {
                maxFreq = freq;
                maxEle = nums[i];
            } else if (freq == maxFreq) {
                maxEle = Math.min(maxEle, nums[i]);
            }
        }
        
        // Return the result
        return maxEle;
    }
}
// Input array
let nums = [4, 4, 5, 5, 6];

// Creating an instance of Solution class
let sol = new Solution();

/* Function call to get the
highest occurring element in array nums */
let ans = sol.mostFrequentElement(nums);

Java: 
import java.util.*;

class Solution {
    /* Function to get the highest 
    occurring element in array nums */
    public int mostFrequentElement(int[] nums) {
        
        // Variable to store the size of array
        int n = nums.length;
        
        // Variable to store maximum frequency
        int maxFreq = 0; 
        
        /* Variable to store element 
        with maximum frequency */
        int maxEle = 0;
        
        // Visited array
        boolean[] visited = new boolean[n];
        
        // First loop
        for (int i = 0; i < n; i++) {
            // Skip second loop if already visited
            if (visited[i]) continue;
            
            /* Variable to store frequency
            of current element */
            int freq = 0;
            
            // Second loop
            for (int j = i; j < n; j++) {
                if (nums[i] == nums[j]) {
                    freq++;
                    visited[j] = true;
                }
            }
            
            /* Update variables if new element having 
            highest frequency is found */
            if (freq > maxFreq) {
                maxFreq = freq;
                maxEle = nums[i];
            } else if (freq == maxFreq) {
                maxEle = Math.min(maxEle, nums[i]);
            }
        }
        
        // Return the result
        return maxEle;
    }
    
    public static void main(String[] args) {
        int[] nums = {4, 4, 5, 5, 6};
        
        /* Creating an instance of 
        Solution class */
        Solution sol = new Solution(); 
        
        /* Function call to get the
        highest occurring element in array nums */
        int ans = sol.mostFrequentElement(nums);
        
        System.out.println("The highest occurring element in the array is: " + ans);
    }
}

Python:
class Solution:
    # Function to get the highest 
    # occurring element in array nums
    def mostFrequentElement(self, nums):
        
        # Variable to store the size of array
        n = len(nums)
        
        # Variable to store maximum frequency
        maxFreq = 0 
        
        # Variable to store element 
        # with maximum frequency
        maxEle = 0
        
        # Visited array
        visited = [False] * n
        
        # First loop
        for i in range(n):
            # Skip second loop if already visited
            if visited[i]:
                continue
            
            # Variable to store frequency
            # of current element 
            freq = 0
            
            # Second loop
            for j in range(i, n):
                if nums[i] == nums[j]:
                    freq += 1
                    visited[j] = True
            
            # Update variables if new element having 
            # highest frequency is found
            if freq > maxFreq:
                maxFreq = freq
                maxEle = nums[i]
            elif freq == maxFreq:
                maxEle = min(maxEle, nums[i])
        
        # Return the result
        return maxEle

if __name__ == "__main__":
    nums = [4, 4, 5, 5, 6]
    
    # Creating an instance of Solution class
    sol = Solution()
    
    # Function call to get the
    # highest occurring element in array nums
    ans = sol.mostFrequentElement(nums)
    
    print("The highest occurring element in the array is:", ans)
Javascript:
class Solution {
    /* Function to get the highest 
    occurring element in array nums */
    mostFrequentElement(nums) {
        
        // Variable to store the size of array
        let n = nums.length;
        
        // Variable to store maximum frequency
        let maxFreq = 0; 
        
        /* Variable to store element 
        with maximum frequency */
        let maxEle = 0;
        
        // Visited array
        let visited = new Array(n).fill(false);
        
        // First loop
        for (let i = 0; i < n; i++) {
            // Skip second loop if already visited
            if (visited[i]) continue;
            
            /* Variable to store frequency
            of current element */
            let freq = 0;
            
            // Second loop
            for (let j = i; j < n; j++) {
                if (nums[i] == nums[j]) {
                    freq++;
                    visited[j] = true;
                }
            }
            
            /* Update variables if new element having 
            highest frequency is found */
            if (freq > maxFreq) {
                maxFreq = freq;
                maxEle = nums[i];
            } else if (freq == maxFreq) {
                maxEle = Math.min(maxEle, nums[i]);
            }
        }
        
        // Return the result
        return maxEle;
    }
}

// Input array
let nums = [4, 4, 5, 5, 6];

// Creating an instance of Solution class
let sol = new Solution();

/* Function call to get the
highest occurring element in array nums */
let ans = sol.mostFrequentElement(nums);

console.log("The highest occurring element in the array is: " + ans);

C#:
using System;

public class Solution
{
    /* Function to get the highest 
    occurring element in array nums */
    public int mostFrequentElement(int[] nums)
    {
        
        // Variable to store the size of array
        int n = nums.Length;
        
        // Variable to store maximum frequency
        int maxFreq = 0; 
        
        /* Variable to store element 
        with maximum frequency */
        int maxEle = 0;
        
        // Visited array
        bool[] visited = new bool[n];
        
        // First loop
        for (int i = 0; i < n; i++) {
            // Skip second loop if already visited
            if (visited[i]) continue;
            
            /* Variable to store frequency
            of current element */
            int freq = 0;
            
            // Second loop
            for (int j = i; j < n; j++) {
                if (nums[i] == nums[j]) {
                    freq++;
                    visited[j] = true;
                }
            }
            
            /* Update variables if new element having 
            highest frequency is found */
            if (freq > maxFreq) {
                maxFreq = freq;
                maxEle = nums[i];
            } else if (freq == maxFreq) {
                maxEle = Math.Min(maxEle, nums[i]);
            }
        }
        
        // Return the result
        return maxEle;
    }
}            
public class Program
{
    public static void Main(string[] args)
    {
        // Input array
        int[] nums = { 4, 4, 5, 5, 6 };

        // Creating an instance of Solution class
        Solution sol = new Solution();

        /* Function call to get the
highest occurring element in array nums */
        int ans = sol.mostFrequentElement(nums);

        Console.WriteLine("The highest occurring element in the array is: " + ans);
    }
}


GO:
package main

import (
	"fmt"
)

func mostFrequentElement(nums []int) int {

	/* Function to get the highest
	occurring element in array nums */

	// Variable to store the size of array
	n := len(nums)

	// Variable to store maximum frequency
	maxFreq := 0

	/* Variable to store element
	with maximum frequency */
	maxEle := 0

	// Visited array
	visited := make([]bool, n)

	// First loop
	for i := 0; i < n; i++ {
		// Skip second loop if already visited
		if visited[i] {
			continue
		}

		/* Variable to store frequency
		of current element */
		freq := 0

		// Second loop
		for j := i; j < n; j++ {
			if nums[i] == nums[j] {
				freq++
				visited[j] = true
			}
		}

		/* Update variables if new element having
		highest frequency is found */
		if freq > maxFreq {
			maxFreq = freq
			maxEle = nums[i]
		} else if freq == maxFreq {
			if nums[i] < maxEle {
				maxEle = nums[i]
			}
		}
	}

	// Return the result
	return maxEle
}

func main() {
	nums := []int{4, 4, 5, 5, 6}

	/* Function call to get the
	highest occurring element in array nums */
	ans := mostFrequentElement(nums)

	fmt.Println("The highest occurring element in the array is:", ans)
}

console.log("The highest occurring element in the array is: " + ans);
Complexity Analysis:
Time Complexity: O(N2) (where N is the size of the array given) – Using two nested loops.

Space Complexity: O(N) – Using a visited array of size N and a couple of variables.
