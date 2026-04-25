Intuition

In this approach, we use the concept of prefix sums to solve the problem of finding the longest subarray with a sum equal to 𝑘. The prefix sum of a subarray ending at index 𝑖 is simply the sum of all the elements of that subarray. By keeping track of these prefix sums and their occurrences, we can efficiently determine the longest subarray that meets the criteria.

Approach

First, we will declare a map to store the prefix sums and their corresponding indices.
We will run a loop from index 0 to n-1 (where n is the size of the array).
For each index i, add the current element a[i] to the prefix sum. If the prefix sum equals k, consider the length of the current subarray (i+1) and update the maximum length if needed. Calculate the prefix sum for the remaining subarray (prefix sum - k).
If this remaining sum exists in the map, calculate the length of the subarray ending at i and starting after the prefix sum, i.e., i - map[remaining sum], and update the maximum length if this length is greater. If the remaining sum does not exist in the map, add the current prefix sum and index to the map to ensure we store the earliest index where each prefix sum occurs.
The prefix sum of a subarray ending at index i is simply the sum of all the elements up to that index. By tracking these sums and their occurrences, we can efficiently determine the longest subarray that sums to k.

Observations
Assume the prefix sum of a subarray ending at index i is x. We need to find another subarray ending at i whose sum equals k. If such a subarray exists, the prefix sum of the remaining part will be x-k.

For a subarray ending at index i with the prefix sum x, if we remove the part with the prefix sum x-k, we are left with a subarray whose sum equals k. This is our target.

Instead of searching for subarrays with sum k, we will use a map to track the prefix sums at each index. The map will store each prefix sum and its corresponding index as a key-value pair. At index i, we will check the map for the prefix sum x-k. If it exists, we calculate the subarray length as i - preSumMap[x-k]. We update the maximum length if this subarray is longer.

We repeat this process for all indices from 0 to n-1 (where n is the size of the array).

Edge Case
Why do we need to check if the prefix sum already exists in the map? Let's understand with an example:

Assume the array is [2, 0, 0, 3]. If we don't check the map before inserting, the algorithm might incorrectly update the index for repeated prefix sums. For instance, at indices 2 and 3, the prefix sum remains the same but the index is updated. When i reaches the end, the calculated length might be incorrect. To avoid this, we only update the map with the first occurrence of each prefix sum. This ensures we get the maximum subarray length. Take the reference of the below image for better understanding.

https://static.takeuforward.org/premium/Hashing/FAQs/Longest%20subarray%20with%20sum%20K-dup/1.svg-frqWZTwt
https://static.takeuforward.org/premium/Hashing/FAQs/Longest%20subarray%20with%20sum%20K-dup/2.svg-sG3OHCSm
https://static.takeuforward.org/premium/Hashing/FAQs/Longest%20subarray%20with%20sum%20K-dup/3.svg-lrsdEoEK
https://static.takeuforward.org/premium/Hashing/FAQs/Longest%20subarray%20with%20sum%20K-dup/4.svg-aQBxVHID

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

        map<int, int> preSumMap;
        int sum = 0;
        int maxLen = 0;
        for (int i = 0; i < n; i++) {
            // calculate the prefix sum till index i
            sum += nums[i];

            // if the sum equals k, update maxLen
            if (sum == k) {
                maxLen = max(maxLen, i + 1);
            }

            // calculate the sum of remaining part i.e., sum - k
            int rem = sum - k;

            // calculate the length and update maxLen
            if (preSumMap.find(rem) != preSumMap.end()) {
                int len = i - preSumMap[rem];
                maxLen = max(maxLen, len);
            }

            // update the map if sum is not already present
            if (preSumMap.find(sum) == preSumMap.end()) {
                preSumMap[sum] = i;
            }
        }

        return maxLen;
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

        Map<Integer, Integer> preSumMap = new HashMap<>();
        int sum = 0;
        int maxLen = 0;
        for (int i = 0; i < n; i++) {
            // calculate the prefix sum till index i
            sum += nums[i];

            // if the sum equals k, update maxLen
            if (sum == k) {
                maxLen = Math.max(maxLen, i + 1);
            }

            // calculate the sum of remaining part i.e., sum - k
            int rem = sum - k;

            // calculate the length and update maxLen
            if (preSumMap.containsKey(rem)) {
                int len = i - preSumMap.get(rem);
                maxLen = Math.max(maxLen, len);
            }

            // update the map if sum is not already present
            if (!preSumMap.containsKey(sum)) {
                preSumMap.put(sum, i);
            }
        }

        return maxLen;
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

        preSumMap = {}
        sum = 0
        maxLen = 0
        for i in range(n):
            # calculate the prefix sum till index i
            sum += nums[i]

            # if the sum equals k, update maxLen
            if sum == k:
                maxLen = max(maxLen, i + 1)

            # calculate the sum of remaining part i.e., sum - k
            rem = sum - k

            # calculate the length and update maxLen
            if rem in preSumMap:
                length = i - preSumMap[rem]
                maxLen = max(maxLen, length)

            # update the map if sum is not already present
            if sum not in preSumMap:
                preSumMap[sum] = i

        return maxLen

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

        const preSumMap = new Map();
        let sum = 0;
        let maxLen = 0;
        for (let i = 0; i < n; i++) {
            // calculate the prefix sum till index i
            sum += nums[i];

            // if the sum equals k, update maxLen
            if (sum === k) {
                maxLen = Math.max(maxLen, i + 1);
            }

            // calculate the sum of remaining part i.e., sum - k
            const rem = sum - k;

            // calculate the length and update maxLen
            if (preSumMap.has(rem)) {
                const len = i - preSumMap.get(rem);
                maxLen = Math.max(maxLen, len);
            }

            // update the map if sum is not already present
            if (!preSumMap.has(sum)) {
                preSumMap.set(sum, i);
            }
        }

        return maxLen;
    }
}

const nums = [-1, 1, 1];
const k = 1;

// Create an instance of the Solution class
const solution = new Solution();
// Function call to get the result
const len = solution.longestSubarray(nums, k);

console.log("The length of the longest subarray is:", len);

C#:
using System;
using System.Collections.Generic;

public class Solution
{
    public int LongestSubarray(int[] nums, int k)
    {
        var preSumMap = new Dictionary<int, int>();
        int sum = 0;
        int maxLen = 0;
        for (int i = 0; i < nums.Length; i++)
        {
            // calculate the prefix sum till index i
            sum += nums[i];

            // if the sum equals k, update maxLen
            if (sum == k)
            {
                maxLen = Math.Max(maxLen, i + 1);
            }

            // calculate the sum of remaining part i.e., sum - k
            int rem = sum - k;

            // calculate the length and update maxLen
            if (preSumMap.ContainsKey(rem))
            {
                int len = i - preSumMap[rem];
                maxLen = Math.Max(maxLen, len);
            }

            // update the map if sum is not already present
            if (!preSumMap.ContainsKey(sum))
            {
                preSumMap.Add(sum, i);
            }
        }

        return maxLen;
    }

public static void Main(string[] args)
    {
        int[] nums = { -1, 1, 1 };
        int k = 1;

        // Create an instance of the Solution class
        Solution solution = new Solution();
        // Function call to get the result
        int len = solution.LongestSubarray(nums, k);

        Console.WriteLine("The length of the longest subarray is: " + len);
    }
}

Go:
package main

import "fmt"

func longestSubarray(nums []int, k int) int {
    n := len(nums)

    // map to store prefix sums and their first occurrence indices
    preSumMap := make(map[int]int)
    sum := 0
    maxLen := 0

    for i := 0; i < n; i++ {
        // calculate the prefix sum till index i
        sum += nums[i]

        // if the sum equals k, update maxLen
        if sum == k {
            if i+1 > maxLen {
                maxLen = i + 1
            }
        }

        // calculate the sum of remaining part i.e., sum - k
        rem := sum - k

        // calculate the length and update maxLen
        if idx, exists := preSumMap[rem]; exists {
            if i-idx > maxLen {
                maxLen = i - idx
            }
        }

        // update the map if sum is not already present
        if _, exists := preSumMap[sum]; !exists {
            preSumMap[sum] = i
        }
    }

    return maxLen
}

func main() {
    a := []int{-1, 1, 1}
    k := 1

    // Function call to get the result
    len := longestSubarray(a, k)
    fmt.Printf("The length of the longest subarray is: %d\n", len)
}
Complexity Analysis 

Time Complexity: O(N) or O(NxlogN) depending on the map data structure used, where N is the size of the array. For example, using an unordered_map in C++ gives a time complexity of O(N) (though in the worst case, unordered_map takes O(N) to find an element, making the time complexity O(N2)). If we use a map data structure, the time complexity is O(NxlogN). The best case complexity is O(N) as we are traversing the array with a loop.

Space Complexity: O(N), since we are using a map data structure.
