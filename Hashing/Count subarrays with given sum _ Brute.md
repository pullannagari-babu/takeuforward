Intuition

To find the number of subarrays with a sum equal to k, use three nested loops. The first two loops (i and j) will iterate over every possible starting and ending index of a subarray, respectively. In each iteration, the subarray range will be from index i to index j. Using a third loop, calculate the sum of the elements in the subarray [i…j], then count only those subarrays where the calculated sum equals k.

Approach

First, use a loop (i) to select every possible starting index of the subarray. The starting indices can range from index 0 to index n-1 (where n is the size of the array).
Inside this loop, run another loop (j) to signify the ending index of the subarray. For each subarray starting from index i, the possible ending indices can vary from index i to n-1.
Next, for each subarray defined by the range i to j (i.e., arr[i…j]), use another loop to calculate the sum of all the elements in that subarray.
After calculating the sum, check if the sum is equal to the given k. If it is, increase the count.

C++

#include <bits/stdc++.h>
using namespace std;

class Solution
{
public:
    int subarraySum(vector<int> &nums, int k)
    {
        int n = nums.size();
        // Number of subarrays
        int cnt = 0;

        // starting index i
        for (int i = 0; i < n; i++) {
            // ending index j
            for (int j = i; j < n; j++) {

                // calculate the sum of subarray [i...j]
                int sum = 0;
                for (int K = i; K <= j; K++)
                    sum += nums[K];

                // Increase the count if sum == k:
                if (sum == k)
                    cnt++;
            }
        }
        return cnt;
    }
};

int main() {
    Solution solution;
    vector<int> nums = {3, 1, 2, 4};
    int k = 6;
    // Function call to find the result
    int cnt = solution.subarraySum(nums, k);
    cout << "The number of subarrays is: " << cnt << "\n";
    return 0;
}

Java


class Solution {
    public int subarraySum(int[] nums, int k) {
        int n = nums.length;
        // Number of subarrays
        int cnt = 0;

        // starting index i
        for (int i = 0; i < n; i++) {
            // ending index j
            for (int j = i; j < n; j++) {

                // calculate the sum of subarray [i...j]
                int sum = 0;
                for (int K = i; K <= j; K++)
                    sum += nums[K];

                // Increase the count if sum == k:
                if (sum == k)
                    cnt++;
            }
        }
        return cnt;
    }
}

public class Main {
    public static void main(String[] args) {
        Solution solution = new Solution();
        int[] nums = {3, 1, 2, 4};
        int k = 6;
        // Function call to find the result
        int cnt = solution.subarraySum(nums, k);
        System.out.println("The number of subarrays is: " + cnt);
    }
}


Python


class Solution:
    def subarraySum(self, nums, k):
        n = len(nums)
        # Number of subarrays
        cnt = 0

        # starting index i
        for i in range(n):
            # ending index j
            for j in range(i, n):

                # calculate the sum of subarray [i...j]
                sum = 0
                for K in range(i, j + 1):
                    sum += nums[K]

                # Increase the count if sum == k:
                if sum == k:
                    cnt += 1
        return cnt

if __name__ == "__main__":
    solution = Solution()
    nums = [3, 1, 2, 4]
    k = 6
    # Function call to find the result
    cnt = solution.subarraySum(nums, k)
    print("The number of subarrays is:", cnt)


JavaScript


class Solution {
    subarraySum(nums, k) {
        let n = nums.length;
        // Number of subarrays
        let cnt = 0;

        // starting index i
        for (let i = 0; i < n; i++) {
            // ending index j
            for (let j = i; j < n; j++) {

                // calculate the sum of subarray [i...j]
                let sum = 0;
                for (let K = i; K <= j; K++)
                    sum += nums[K];

                // Increase the count if sum == k:
                if (sum == k)
                    cnt++;
            }
        }
        return cnt;
    }
}

const solution = new Solution();
const nums = [3, 1, 2, 4];
const k = 6;
// Function call to find the result
const cnt = solution.subarraySum(nums, k);
console.log("The number of subarrays is:", cnt);

C#

using System;

public class Solution
{
    public int SubarraySum(int[] nums, int k)
    {
        int n = nums.Length;
        // Number of subarrays
        int cnt = 0;

        // starting index i
        for (int i = 0; i < n; i++)
        {
            // ending index j
            for (int j = i; j < n; j++)
            {

                // calculate the sum of subarray [i...j]
                int sum = 0;
                for (int K = i; K <= j; K++)
                    sum += nums[K];

                // Increase the count if sum == k:
                if (sum == k)
                    cnt++;
            }
        }
        return cnt;
    }

    public static void Main(string[] args)
    {
        Solution solution = new Solution();
        int[] nums = { 3, 1, 2, 4 };
        int k = 6;
        // Function call to find the result
        int cnt = solution.SubarraySum(nums, k);
        Console.WriteLine("The number of subarrays is: " + cnt);
    }
}

Go

package main

import (
	"fmt"
)

// Function to count the number of subarrays whose sum is equal to k
func subarraySum(nums []int, k int) int {
	n := len(nums)
	cnt := 0

	// Iterate over all possible subarrays
	for i := 0; i < n; i++ {
		for j := i; j < n; j++ {
			sum := 0
			for x := i; x <= j; x++ {
				sum += nums[x]
			}
			if sum == k {
				cnt++
			}
		}
	}
	return cnt
}

func main() {
	nums := []int{3, 1, 2, 4}
	k := 6

	cnt := subarraySum(nums, k)

	fmt.Printf("The number of subarrays is: %d\n", cnt)
}


Complexity Analysis 

Time Complexity: O(N3), where N is the size of the array. We are using three nested loops here. Though all loops are not running exactly N times, the time complexity will be approximately O(N3).

Space Complexity: O(1), as we are not using any extra space.
