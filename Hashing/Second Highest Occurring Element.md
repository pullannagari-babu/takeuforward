Second Highest Occurring Element
Easy
Company
Given an array of n integers, find the second most frequent element in it.

If there are multiple elements that appear second most frequent times, find the smallest of them.

If second most frequent element does not exist return -1.
Example 1
Input: arr = [1, 2, 2, 3, 3, 3]
Output: 2
Explanation:
The number 2 appears the second most (2 times) and number 3 appears the most(3 times). 
Example 2
Input: arr = [4, 4, 5, 5, 6, 7]
Output: 6
Explanation:
Both 6 and 7 appear second most times, but 6 is smaller.
Now your turn!
Input: arr = [10, 9 ,7, 7]
Output:
Pick your answer


Intuition:

Imagine you have a bag full of marbles, each with a different number. Your task is to find the marble that appears the second most number of times in the bag. To solve this, we need to keep track of the number of times each marble appears. We should identify the marble with the highest occurrence first and then look for the marble that comes next in terms of frequency. This way, we ensure that we correctly find the second highest occurring marble in the bag.

Approach:

Create variables to store the highest and second highest frequencies. Also, create variables to store the corresponding elements. Use a visited array of boolean type to mark elements that have already been counted to avoid recounting them.
Loop through each element in the array. For each element, if it hasn't been counted yet, proceed to count its occurrences. For each element, count how many times it appears in the array. Mark these elements as counted.
Compare the frequency of the current element with the highest and second highest frequencies. Update the highest and second highest frequencies and their corresponding elements as needed.
If two elements have the same frequency, choose the smaller one. After processing all elements, return the element with the second highest frequency.
Dry Run:

https://static.takeuforward.org/premium/Beginner%20Problems/Basic%20Hashing/Second%20highest%20occurring%20element/1.png-oXihNMjN

https://static.takeuforward.org/premium/Beginner%20Problems/Basic%20Hashing/Second%20highest%20occurring%20element/2.png-pT7yDMQJ

https://static.takeuforward.org/premium/Beginner%20Problems/Basic%20Hashing/Second%20highest%20occurring%20element/3.png-gxpTO8fz

https://static.takeuforward.org/premium/Beginner%20Problems/Basic%20Hashing/Second%20highest%20occurring%20element/4.png-ZAelXBIV

https://static.takeuforward.org/premium/Beginner%20Problems/Basic%20Hashing/Second%20highest%20occurring%20element/5.png-MHoqUCRy

https://static.takeuforward.org/premium/Beginner%20Problems/Basic%20Hashing/Second%20highest%20occurring%20element/6.png-PpqMVNpa

https://static.takeuforward.org/premium/Beginner%20Problems/Basic%20Hashing/Second%20highest%20occurring%20element/7.png--hiHzT3T

https://static.takeuforward.org/premium/Beginner%20Problems/Basic%20Hashing/Second%20highest%20occurring%20element/8.png-DtqWFXas

https://static.takeuforward.org/premium/Beginner%20Problems/Basic%20Hashing/Second%20highest%20occurring%20element/9.png-9OdvCTwx

https://static.takeuforward.org/premium/Beginner%20Problems/Basic%20Hashing/Second%20highest%20occurring%20element/10.png-Mk4kFwIT

1/10

Solution:

C++

#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    /* Function to get the second highest 
    occurring element in array */
    int secondMostFrequentElement(vector<int> &nums) {
        
        // Variable to store the size of array
        int n = nums.size();
        
        /* Variable to store maximum frequency
        and second Max frequency */
        int maxFreq = 0;
        int secMaxFreq = 0;
        
        /* Variable to store elements with most 
        and second most frequency */
        int maxEle = -1, secEle = -1;
        
        // Visited array
        vector<bool> visited(n, false);
        
        // First loop
        for(int i = 0; i < n; i++) {
            // Skip second loop if already visited
            if(visited[i]) continue;
            
            /* Variable to store frequency
            of current element */
            int freq = 0;
            
            // Second loop
            for(int j = i; j < n; j++) {
                if(nums[i] == nums[j]) {
                    freq++;
                    visited[j] = true;
                }
            }
            
            /* Update variables if new element  
            having highest frequency or second
            highest frequency is found */
            if(freq > maxFreq) {
                secMaxFreq = maxFreq;
                maxFreq = freq;
                secEle = maxEle;
                maxEle = nums[i];
            } 
            else if(freq == maxFreq) {
                maxEle = min(maxEle, nums[i]);
            }
            else if(freq > secMaxFreq) {
                secMaxFreq = freq;
                secEle = nums[i];
            }
            else if(freq == secMaxFreq) {
                secEle = min(secEle, nums[i]);
            }
            
        }
        
        // Return the result
        return secEle;
    }
};

int main() {
    vector<int> nums = {4, 4, 5, 5, 6, 7};
    
    /* Creating an instance of 
    Solution class */
    Solution sol; 
    
    /* Function call to get the second
    highest occurring element in array */
    int ans = sol.secondMostFrequentElement(nums);
    
    cout << "The second highest occurring element in the array is: " << ans;
    
    return 0;
}


Java

import java.util.*;

class Solution {
    /* Function to get the second highest 
    occurring element in array */
    public int secondMostFrequentElement(int[] nums) {
        
        // Variable to store the size of array
        int n = nums.length;
        
        /* Variable to store maximum frequency
        and second Max frequency */
        int maxFreq = 0;
        int secMaxFreq = 0;
        
        /* Variable to store elements with most 
        and second most frequency */
        int maxEle = -1, secEle = -1;
        
        // Visited array
        boolean[] visited = new boolean[n];
        
        // First loop
        for(int i = 0; i < n; i++) {
            // Skip second loop if already visited
            if(visited[i]) continue;
            
            /* Variable to store frequency
            of current element */
            int freq = 0;
            
            // Second loop
            for(int j = i; j < n; j++) {
                if(nums[i] == nums[j]) {
                    freq++;
                    visited[j] = true;
                }
            }
            
            /* Update variables if new element  
            having highest frequency or second
            highest frequency is found */
            if(freq > maxFreq) {
                secMaxFreq = maxFreq;
                maxFreq = freq;
                secEle = maxEle;
                maxEle = nums[i];
            } 
            else if(freq == maxFreq) {
                maxEle = Math.min(maxEle, nums[i]);
            }
            else if(freq > secMaxFreq) {
                secMaxFreq = freq;
                secEle = nums[i];
            }
            else if(freq == secMaxFreq) {
                secEle = Math.min(secEle, nums[i]);
            }
            
        }
        
        // Return the result
        return secEle;
    }

    public static void main(String[] args) {
        int[] nums = {4, 4, 5, 5, 6, 7};
        
        /* Creating an instance of 
        Solution class */
        Solution sol = new Solution();
        
        /* Function call to get the second
        highest occurring element in array */
        int ans = sol.secondMostFrequentElement(nums);
        
        System.out.println("The second highest occurring element in the array is: " + ans);
    }
}

Python

class Solution:
    """Function to get the second highest 
    occurring element in array"""
    def secondMostFrequentElement(self, nums):
        
        # Variable to store the size of array
        n = len(nums)
        
        """Variable to store maximum frequency
        and second Max frequency"""
        maxFreq = 0
        secMaxFreq = 0
        
        """Variable to store elements with most 
        and second most frequency"""
        maxEle = -1
        secEle = -1
        
        # Visited array
        visited = [False] * n
        
        # First loop
        for i in range(n):
            # Skip second loop if already visited
            if visited[i]:
                continue
            
            """Variable to store frequency
            of current element"""
            freq = 0
            
            # Second loop
            for j in range(i, n):
                if nums[i] == nums[j]:
                    freq += 1
                    visited[j] = True
            
            """Update variables if new element  
            having highest frequency or second
            highest frequency is found"""
            if freq > maxFreq:
                secMaxFreq = maxFreq
                maxFreq = freq
                secEle = maxEle
                maxEle = nums[i]
            elif freq == maxFreq:
                maxEle = min(maxEle, nums[i])
            elif freq > secMaxFreq:
                secMaxFreq = freq
                secEle = nums[i]
            elif freq == secMaxFreq:
                secEle = min(secEle, nums[i])
        
        # Return the result
        return secEle

if __name__ == "__main__":
    nums = [4, 4, 5, 5, 6, 7]
    
    """Creating an instance of 
    Solution class"""
    sol = Solution()
    
    """Function call to get the second
    highest occurring element in array"""
    ans = sol.secondMostFrequentElement(nums)
    
    print(f"The second highest occurring element in the array is: {ans}")

JavaScript
class Solution {
    /* Function to get the second highest 
    occurring element in array */
    secondMostFrequentElement(nums) {
        
        // Variable to store the size of array
        let n = nums.length;
        
        /* Variable to store maximum frequency
        and second Max frequency */
        let maxFreq = 0;
        let secMaxFreq = 0;
        
        /* Variable to store elements with most 
        and second most frequency */
        let maxEle = -1, secEle = -1;
        
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
                if (nums[i] === nums[j]) {
                    freq++;
                    visited[j] = true;
                }
            }
            
            /* Update variables if new element  
            having highest frequency or second
            highest frequency is found */
            if (freq > maxFreq) {
                secMaxFreq = maxFreq;
                maxFreq = freq;
                secEle = maxEle;
                maxEle = nums[i];
            } 
            else if (freq === maxFreq) {
                maxEle = Math.min(maxEle, nums[i]);
            }
            else if (freq > secMaxFreq) {
                secMaxFreq = freq;
                secEle = nums[i];
            }
            else if (freq === secMaxFreq) {
                secEle = Math.min(secEle, nums[i]);
            }
        }
        
        // Return the result
        return secEle;
    }
}

// Example usage
let nums = [4, 4, 5, 5, 6, 7];

/* Creating an instance of 
Solution class */
let sol = new Solution();

/* Function call to get the second
highest occurring element in array */
let ans = sol.secondMostFrequentElement(nums);

console.log("The second highest occurring element in the array is: " + ans);

C#

using System;

public class Solution
{
    /* Function to get the second highest 
    occurring element in array */
    public int SecondMostFrequentElement(int[] nums)
    {
        
        // Variable to store the size of array
        int n = nums.Length;
        
        /* Variable to store maximum frequency
        and second Max frequency */
        int maxFreq = 0;
        int secMaxFreq = 0;
        
        /* Variable to store elements with most 
        and second most frequency */
        int maxEle = -1, secEle = -1;
        
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
            
            /* Update variables if new element  
            having highest frequency or second
            highest frequency is found */
            if (freq > maxFreq) {
                secMaxFreq = maxFreq;
                maxFreq = freq;
                secEle = maxEle;
                maxEle = nums[i];
            } 
            else if (freq == maxFreq) {
                maxEle = Math.Min(maxEle, nums[i]);
            }
            else if (freq > secMaxFreq) {
                secMaxFreq = freq;
                secEle = nums[i];
            }
            else if (freq == secMaxFreq) {
                secEle = Math.Min(secEle, nums[i]);
            }
        }
        
        // Return the result
        return secEle;
    }
}

public class Program
{
    public static void Main(string[] args)
    {
        // Example usage
        int[] nums = {4, 4, 5, 5, 6, 7};

        /* Creating an instance of 
        Solution class */
        Solution sol = new Solution();

        /* Function call to get the second
        highest occurring element in array */
        int ans = sol.SecondMostFrequentElement(nums);

        Console.WriteLine("The second highest occurring element in the array is: " + ans);
    }
}

Go

package main

import (
	"fmt"
	"math"
)

/* Function to get the second highest 
 occurring element in array */
func secondMostFrequentElement(nums []int) int {

	// Variable to store the size of array
	n := len(nums)

	/* Variable to store maximum frequency
	and second Max frequency */
	maxFreq := 0
	secMaxFreq := 0

	/* Variable to store elements with most 
	and second most frequency */
	maxEle := -1
	secEle := -1

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

		/* Update variables if new element  
		having highest frequency or second
		highest frequency is found */
		if freq > maxFreq {
			secMaxFreq = maxFreq
			maxFreq = freq
			secEle = maxEle
			maxEle = nums[i]
		} else if freq == maxFreq {
			maxEle = int(math.Min(float64(maxEle), float64(nums[i])))
		} else if freq > secMaxFreq {
			secMaxFreq = freq
			secEle = nums[i]
		} else if freq == secMaxFreq {
			secEle = int(math.Min(float64(secEle), float64(nums[i])))
		}
	}

	// Return the result
	return secEle
}

func main() {
	nums := []int{4, 4, 5, 5, 6, 7}

	/* Function call to get the second
	highest occurring element in array */
	ans := secondMostFrequentElement(nums)

	fmt.Printf("The second highest occurring element in the array is: %d\n", ans)
}


Complexity Analysis:

Time Complexity: O(N2) (where N is the size of the array given) – Using two nested loops.

Space Complexity: O(N) – Using a visited array of size N and a couple of variables.
