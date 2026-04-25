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
Output:
Pick your answer



Intuition

If we carefully observe, we can notice that to get the XOR of the current subarray, we just need to XOR the current element (i.e., arr[j]) with the XOR of the previous subarray (i.e., arr[i...j-1]). Assume the previous subarray is arr[i...j-1] and the current subarray is arr[i...j]. The XOR of arr[i...j] can be calculated as (XOR of arr[i...j-1]) ^ arr[j]. This approach allows us to remove the third loop, and calculate the XOR while moving the j pointer.

Approach

First, run a loop (let's call it i) that selects every possible starting index of the subarray. The starting indices can range from index 0 to n−1 (where n is the size of the array). Inside this loop, run another loop (let's call it j) that signifies the ending index of the subarray. For each subarray starting from index i, the ending index can range from i to n−1.
For each subarray from index i to j, calculate the XOR of all the elements in that subarray by simply doing XOR operation on the previous XOR and the element at j index.
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
            int xorr = 0;
            for (int j = i; j < n; j++) {
                /* Step 2: Calculate XOR of
                   all elements in the subarray */
                xorr = xorr ^ nums[j];

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
            int xorr = 0;
            for (int j = i; j < n; j++) {
                /* Step 2: Calculate XOR of
                   all elements in the subarray */
                xorr = xorr ^ nums[j];

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
            xorr = 0
            for j in range(i, n):
                # Step 2: Calculate XOR of all elements in the subarray
                xorr ^= nums[j]

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
            let xorr = 0;
            for (let j = i; j < n; j++) {
                /* Step 2: Calculate XOR of
                   all elements in the subarray */
                xorr ^= nums[j];

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
            int xorr = 0;
            for (int j = i; j < n; j++) {
                /* Step 2: Calculate XOR of
                   all elements in the subarray */
                xorr ^= nums[j];

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
        xorr := 0
        for j := i; j < n; j++ {
            // Step 2: Calculate XOR of all elements in the subarray
            xorr = xorr ^ nums[j]

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

Time Complexity: O(N2), where N is the size of the array. Since we are using two nested loops, each running for N times, the time complexity will be approximately O(N2).

Space Complexity: O(1) as we are not using any additional space.
