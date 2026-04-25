Medium
Faqs_Brute_Array_Longest Consecutive Sequence in an Array.md
Given an array nums of n integers.
Return the length of the longest sequence of consecutive integers. The integers in this sequence can appear in any order.
Example 1
Input: nums = [100, 4, 200, 1, 3, 2]
Output: 4
Explanation:
The longest sequence of consecutive elements in the array is [1, 2, 3, 4], which has a length of 4. This sequence can be formed regardless of the initial order of the elements in the array.
Example 2
Input: nums = [0, 3, 7, 2, 5, 8, 4, 6, 0, 1]
Output: 9
Explanation:
The longest sequence of consecutive elements in the array is [0, 1, 2, 3, 4, 5, 6, 7, 8], which has a length of 9. 
Now your turn!
Input: nums = [1, 9, 3, 10, 4, 20, 2]
Output:
Pick your answer


Intuition
One simple approach is to look for sequences of consecutive numbers by utilising linear search in the array. For each number 𝑥 in the array, we'll check if the next numbers like 𝑥+1, 𝑥+2, 𝑥+3, and so on, are also in the array. This is like checking if we can build a chain of numbers that follow each other directly. By doing this for every number in the array, we can find the longest chain of consecutive numbers. Finally, we'll find the length of the longest chain among all the numbers in the array.

Approach
As you iterate through each number in the array, begin by checking if consecutive numbers like ( x+1, x+2, x+3 ), and so on, exist in the array. The occurrence of the next consecutive number can be checked by using linear search.
When you find consecutive numbers, start counting them using a counter. Increment this counter each time you find the next consecutive number in the sequence.
This counter effectively keeps track of how long the current consecutive sequence is as you move through the array and find more consecutive numbers.
Dry Run:-Please refer to the video for the dry-run.

C++

#include <bits/stdc++.h>
using namespace std;

class Solution {
private:
    // Helper function to perform linear search
    bool linearSearch(vector<int>& a, int num) {
        int n = a.size(); 
        // Traverse through the array 
        for (int i = 0; i < n; i++) {
            if (a[i] == num)
                return true;
        }
        return false;
    }

public:
    // Function to find the longest consecutive sequence
    int longestConsecutive(vector<int>& nums) {
        // If the array is empty
        if (nums.size() == 0) {
            return 0;
        }
        int n = nums.size();
        // Initialize the longest sequence length
        int longest = 1; 

        // Iterate through each element in the array
        for (int i = 0; i < n; i++) {
            // Current element
            int x = nums[i]; 
            // Count of the current sequence
            int cnt = 1; 

            // Search for consecutive numbers
            while (linearSearch(nums, x + 1) == true) {
                // Move to the next number in the sequence
                x += 1; 
                // Increment the count of the sequence
                cnt += 1; 
            }

            // Update the longest sequence length found so far
            longest = max(longest, cnt);
        }
        return longest;
    }
};

int main() {
    vector<int> a = {100, 4, 200, 1, 3, 2};

    // Create an instance of the Solution class
    Solution solution;

    // Function call for longest consecutive sequence
    int ans = solution.longestConsecutive(a);
    cout << "The longest consecutive sequence is " << ans << "\n"; 
    return 0;
}

Java:

import java.util.*;

class Solution {
    // Helper function to perform linear search
    private boolean linearSearch(int[] a, int num) {
        int n = a.length;
        // Traverse through the array
        for (int i = 0; i < n; i++) {
            if (a[i] == num)
                return true;
        }
        return false;
    }

    public int longestConsecutive(int[] nums) {
        // If the array is empty
        if (nums.length == 0) {
            return 0;
        }
        int n = nums.length;
        // Initialize the longest sequence length
        int longest = 1;

        // Iterate through each element in the array
        for (int i = 0; i < n; i++) {
            // Current element
            int x = nums[i];
            // Count of the current sequence
            int cnt = 1;

            // Search for consecutive numbers
            while (linearSearch(nums, x + 1) == true) {
                // Move to the next number in the sequence
                x += 1;
                // Increment the count of the sequence
                cnt += 1;
            }

            // Update the longest sequence length found so far
            longest = Math.max(longest, cnt);
        }
        return longest;
    }

    public static void main(String[] args) {
        int[] a = {100, 4, 200, 1, 3, 2};

        // Create an instance of the Solution class
        Solution solution = new Solution();

        // Function call for longest consecutive sequence
        int ans = solution.longestConsecutive(a);
        System.out.println("The longest consecutive sequence is " + ans);
    }
}


Python:

class Solution:
    # Helper function to perform linear search
    def linearSearch(self, nums, num):
        n = len(nums)
        # Traverse through the array
        for i in range(n):
            if nums[i] == num:
                return True
        return False

    def longestConsecutive(self, nums):
        # If the array is empty
        if len(nums) == 0:
            return 0
        n = len(nums)
        # Initialize the longest sequence length
        longest = 1

        # Iterate through each element in the array
        for i in range(n):
            # Current element
            x = nums[i]
            # Count of the current sequence
            cnt = 1

            # Search for consecutive numbers
            while self.linearSearch(nums, x + 1):
                # Move to the next number in the sequence
                x += 1
                # Increment the count of the sequence
                cnt += 1

            # Update the longest sequence length found so far
            longest = max(longest, cnt)
        return longest

if __name__ == "__main__":
    a = [100, 4, 200, 1, 3, 2]

    # Create an instance of the Solution class
    solution = Solution()

    # Function call for longest consecutive sequence
    ans = solution.longestConsecutive(a)
    print("The longest consecutive sequence is", ans)

JavaScript:

class Solution {
    // Helper function to perform linear search
    linearSearch(nums, num) {
        const n = nums.length;
        // Traverse through the array
        for (let i = 0; i < n; i++) {
            if (nums[i] === num)
                return true;
        }
        return false;
    }

    longestConsecutive(nums) {
        // If the array is empty
        if (nums.length === 0) {
            return 0;
        }
        const n = nums.length;
        // Initialize the longest sequence length
        let longest = 1;

        // Iterate through each element in the array
        for (let i = 0; i < n; i++) {
            // Current element
            let x = nums[i];
            // Count of the current sequence
            let cnt = 1;

            // Search for consecutive numbers
            while (this.linearSearch(nums, x + 1)) {
                // Move to the next number in the sequence
                x += 1;
                // Increment the count of the sequence
                cnt += 1;
            }

            // Update the longest sequence length found so far
            longest = Math.max(longest, cnt);
        }
        return longest;
    }
}

const a = [100, 4, 200, 1, 3, 2];

// Create an instance of the Solution class
const solution = new Solution();

// Function call for longest consecutive sequence
const ans = solution.longestConsecutive(a);
console.log("The longest consecutive sequence is", ans);

C#:
using System;

public class Solution
{
    // Helper function to perform linear search
    private bool LinearSearch(int[] nums, int num)
    {
        int n = nums.Length;
        // Traverse through the array
        for (int i = 0; i < n; i++)
        {
            if (nums[i] == num)
                return true;
        }
        return false;
    }

    public int LongestConsecutive(int[] nums)
    {
        // If the array is empty
        if (nums.Length == 0)
        {
            return 0;
        }
        int n = nums.Length;
        // Initialize the longest sequence length
        int longest = 1;

        // Iterate through each element in the array
        for (int i = 0; i < n; i++)
        {
            // Current element
            int x = nums[i];
            // Count of the current sequence
            int cnt = 1;

            // Search for consecutive numbers
            while (LinearSearch(nums, x + 1))
            {
                // Move to the next number in the sequence
                x += 1;
                // Increment the count of the sequence
                cnt += 1;
            }

            // Update the longest sequence length found so far
            longest = Math.Max(longest, cnt);
        }
        return longest;
    }
}

public class Program
{
    public static void Main(string[] args)
    {
        int[] a = { 100, 4, 200, 1, 3, 2 };

        // Create an instance of the Solution class
        Solution solution = new Solution();

        // Function call for longest consecutive sequence
        int ans = solution.LongestConsecutive(a);
        Console.WriteLine("The longest consecutive sequence is " + ans);
    }
}

Go:
package main

import "fmt"

// Helper function to perform linear search
func linearSearch(a []int, num int) bool {
    n := len(a)
    // Traverse through the array
    for i := 0; i < n; i++ {
        if a[i] == num {
            return true
        }
    }
    return false
}

// Function to find the longest consecutive sequence
func longestConsecutive(nums []int) int {
    // If the array is empty
    if len(nums) == 0 {
        return 0
    }
    n := len(nums)
    // Initialize the longest sequence length
    longest := 1

    // Iterate through each element in the array
    for i := 0; i < n; i++ {
        // Current element
        x := nums[i]
        // Count of the current sequence
        cnt := 1

        // Search for consecutive numbers
        for linearSearch(nums, x+1) == true {
            // Move to the next number in the sequence
            x += 1
            // Increment the count of the sequence
            cnt += 1
        }

        // Update the longest sequence length found so far
        if cnt > longest {
            longest = cnt
        }
    }
    return longest
}

func main() {
    a := []int{100, 4, 200, 1, 3, 2}

    // Function call for longest consecutive sequence
    ans := longestConsecutive(a)
    fmt.Printf("The longest consecutive sequence is %d\n", ans)
}


Complexity Analysis:
Time Complexity: O(N3), where N is the size of the array.
In the worst case, all N elements form a single consecutive sequence. Each element in nums is checked in the outer loop O(N) times. The inner while loop could also run O(N) times for one outer iteration. Since linearSearch() is called inside the conditional statement of the while loop and itself runs in O(N), this results in a cubic time complexity.

Space Complexity: O(1), as we are not using any extra space to solve this pr
