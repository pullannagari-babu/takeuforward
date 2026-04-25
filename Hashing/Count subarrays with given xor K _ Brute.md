Count subarrays with given xor K
Hard
Hints
Company
Given an array of integers nums and an integer k, return the total number of subarrays whose XOR equals to k.
Example 1
Input : nums = [4, 2, 2, 6, 4], k = 6

Output : 4

Explanation : The subarrays having XOR of their elements as 6 are [4, 2],  [4, 2, 2, 6, 4], [2, 2, 6], and [6]
Example 2
Input :nums = [5, 6, 7, 8, 9], k = 5

Output : 2

Explanation : The subarrays having XOR of their elements as 5 are [5] and [5, 6, 7, 8, 9]
Now your turn!
Input : nums = [5, 2, 9], k = 7



Intuition

We will check the XOR of every possible subarray and count how many of them are equal to k. To do this, use three nested loops. The first two loops (let's call them i and j) will iterate over every possible starting and ending index of a subarray. In each iteration, the subarray range will be from index i to index j. Using another loop, calculate the XOR of the elements in the subarray [i...j]. Count the number of subarrays where the XOR is equal to k.

Note: Select every possible subarray using two nested loops, and for each subarray, calculate the XOR of all its elements using another loop.

Approach

First, run a loop (let's call it i) that selects every possible starting index of the subarray. The starting indices can range from index 0 to n−1 (where n is the size of the array). Inside this loop, run another loop (let's call it j) that signifies the ending index of the subarray. For each subarray starting from index i, the ending index can range from i to n−1.
For each subarray from index i to j (i.e., arr[i...j]), run another loop to calculate the XOR of all the elements in that subarray.
If the XOR equals k, increase the count by 1.

C++:


#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    // Function to count the number of subarrays with XOR k
    int subarraysWithXorK(vector<int>& nums, int k) {
        int n = nums.size(); 
        int cnt = 0;

        // Step 1: Generate subarrays
        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                int xorr = 0;
                /* Step 2: Calculate XOR of 
                   all elements in the subarray */
                for (int K = i; K <= j; K++) {
                    xorr = xorr ^ nums[K];
                }
                // Step 3: Check XOR and count
                if (xorr == k) cnt++;
            }
        }
        return cnt;
    }
};

int main() {
    vector<int> a = {4, 2, 2, 6, 4}; 
    int k = 6; 

    // Create an instance of the Solution class
    Solution solution;

    // Function call to get the result
    int ans = solution.subarraysWithXorK(a, k);
  
    cout << "The number of subarrays with XOR k is: " << ans << "\n";
    return 0;
}

Java:


import java.util.*;

class Solution {
    // Function to count the number of subarrays with XOR k
    public int subarraysWithXorK(int[] nums, int k) {
        int n = nums.length; 
        int cnt = 0;

        // Step 1: Generate subarrays
        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                int xorr = 0;
                /* Step 2: Calculate XOR of 
                   all elements in the subarray */
                for (int K = i; K <= j; K++) {
                    xorr = xorr ^ nums[K];
                }
                // Step 3: Check XOR and count
                if (xorr == k) cnt++;
            }
        }
        return cnt;
    }

    public static void main(String[] args) {
        int[] a = {4, 2, 2, 6, 4}; 
        int k = 6; 

        // Create an instance of the Solution class
        Solution solution = new Solution();

        // Function call to get the result
        int ans = solution.subarraysWithXorK(a, k);
   
        System.out.println("The number of subarrays with XOR k is: " + ans);
    }
}

Python:


class Solution:
    # Function to count the number of subarrays with XOR k
    def subarraysWithXorK(self, nums, k):
        n = len(nums)
        cnt = 0

        # Step 1: Generate subarrays
        for i in range(n):
            for j in range(i, n):
                xorr = 0
                # Step 2: Calculate XOR of all elements in the subarray
                for K in range(i, j + 1):
                    xorr ^= nums[K]
                # Step 3: Check XOR and count
                if xorr == k:
                    cnt += 1
        return cnt

if __name__ == "__main__":
    a = [4, 2, 2, 6, 4]
    k = 6

    # Create an instance of the Solution class
    solution = Solution()

    # Function call to get the result
    ans = solution.subarraysWithXorK(a, k)
 
    print("The number of subarrays with XOR k is:", ans)

JavaScript:

class Solution {
    // Function to count the number of subarrays with XOR k
    subarraysWithXorK(nums, k) {
        const n = nums.length;
        let cnt = 0;

        // Step 1: Generate subarrays
        for (let i = 0; i < n; i++) {
            for (let j = i; j < n; j++) {
                let xorr = 0;
                /* Step 2: Calculate XOR of 
                   all elements in the subarray */
                for (let K = i; K <= j; K++) {
                    xorr ^= nums[K];
                }
                // Step 3: Check XOR and count
                if (xorr === k) cnt++;
            }
        }
        return cnt;
    }
}

const a = [4, 2, 2, 6, 4];
const k = 6;

// Create an instance of the Solution class
const solution = new Solution();

// Function call to get the result
const ans = solution.subarraysWithXorK(a, k);

console.log("The number of subarrays with XOR k is:", ans);

C#:

using System;

public class Solution {
    // Function to count the number of subarrays with XOR k
    public int SubarraysWithXorK(int[] nums, int k) {
        int n = nums.Length;
        int cnt = 0;

        // Step 1: Generate subarrays
        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                int xorr = 0;
                /* Step 2: Calculate XOR of 
                   all elements in the subarray */
                for (int K = i; K <= j; K++) {
                    xorr ^= nums[K];
                }
                // Step 3: Check XOR and count
                if (xorr == k) cnt++;
            }
        }
        return cnt;
    }

public static void Main(string[] args) {
        int[] a = { 4, 2, 2, 6, 4 };
        int k = 6;

        // Create an instance of the Solution class
        Solution solution = new Solution();

        // Function call to get the result
        int ans = solution.SubarraysWithXorK(a, k);

        Console.WriteLine("The number of subarrays with XOR k is: " + ans);
    }
}

Go:

package main

import "fmt"

// Function to count the number of subarrays with XOR k
func subarraysWithXorK(nums []int, k int) int {
    n := len(nums)
    cnt := 0

    // Step 1: Generate subarrays
    for i := 0; i < n; i++ {
        for j := i; j < n; j++ {
            xorr := 0
            // Step 2: Calculate XOR of all elements in the subarray
            for k := i; k <= j; k++ {
                xorr = xorr ^ nums[k]
            }
            // Step 3: Check XOR and count
            if xorr == k {
                cnt++
            }
        }
    }
    return cnt
}

func main() {
    a := []int{4, 2, 2, 6, 4}
    k := 6

    // Function call to get the result
    ans := subarraysWithXorK(a, k)

    fmt.Printf("The number of subarrays with XOR k is: %d\n", ans)
}
Complexity Analysis 

Time Complexity: O(N3), where N is the size of the array. This is because we are using three nested loops, each running approximately N times.

Space Complexity: O(1) since we are not using any additional space.
