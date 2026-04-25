Intuition
A more efficient method involves sorting the array first and then finding the longest consecutive sequence using a simple iteration.

Approach
Begin by sorting the entire array in ascending order. This step helps group consecutive numbers together, simplifying the sequence detection process.
Use a loop to iterate through each element of the sorted array.
Track consecutive sequences by comparing each element arr[i] with the lastSmaller variable. If arr[i] - 1 == lastSmaller, increment the length of the current sequence (cnt) and update lastSmaller to arr[i]. Skip the current element if arr[i] equals lastSmaller, as it's already part of a sequence. If arr[i] is greater than lastSmaller + 1, start a new sequence from arr[i] by updating lastSmaller to arr[i] and reset cnt to 1.
Throughout the iteration, compare cnt with longest and update longest to store the maximum sequence length encountered.
Note: Here, we are distorting the given array by sorting it.

Dry Run:-Please refer to the video for the dry-run.

C++:


#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        int n = nums.size();

        // Return 0 if array is empty
        if (n == 0) return 0; 

        sort(nums.begin(), nums.end()); 

        // Track last smaller element
        int lastSmaller = INT_MIN; 
        // Count current sequence length
        int cnt = 0; 
        // Track longest sequence length
        int longest = 1; 

        for (int i = 0; i < n; i++) {
            // If consecutive number exists
            if (nums[i] - 1 == lastSmaller) {
                // Increment sequence count
                cnt += 1; 
                // Update last smaller element
                lastSmaller = nums[i]; 
            } 
            // If consecutive number doesn't exits
            else if (nums[i] != lastSmaller) {
                // Reset count for new sequence
                cnt = 1; 
                // Update last smaller element
                lastSmaller = nums[i]; 
            }
            // Update longest if needed
            longest = max(longest, cnt); 
        }
        return longest;
    }
};

int main() {
    vector<int> a = {100, 4, 200, 1, 3, 2}; 

    // Create an instance of solution class
    Solution solution; 
    // Function call for finding longest consecutive sequence
    int ans = solution.longestConsecutive(a); 
    cout << "The longest consecutive sequence is " << ans << "\n";
    return 0;
}

Java:

import java.util.*;

class Solution {
    public int longestConsecutive(int[] nums) {
        int n = nums.length;

        // Return 0 if array is empty
        if (n == 0) return 0; 

        Arrays.sort(nums); // Sort the array

        // Track last smaller element
        int lastSmaller = Integer.MIN_VALUE; 
        // Count current sequence length
        int cnt = 0; 
        // Track longest sequence length
        int longest = 1; 

        for (int i = 0; i < n; i++) {
            // If consecutive number exists
            if (nums[i] - 1 == lastSmaller) {
                // Increment sequence count
                cnt += 1; 
                // Update last smaller element
                lastSmaller = nums[i]; 
            } 
            // If consecutive number doesn't exist
            else if (nums[i] != lastSmaller) {
                // Reset count for new sequence
                cnt = 1; 
                // Update last smaller element
                lastSmaller = nums[i]; 
            }
            // Update longest if needed
            longest = Math.max(longest, cnt); 
        }
        return longest;
    }

    public static void main(String[] args) {
        int[] a = {100, 4, 200, 1, 3, 2}; 

        // Create an instance of solution class
        Solution solution = new Solution(); 
        // Function call for finding longest consecutive sequence
        int ans = solution.longestConsecutive(a); 
        System.out.println("The longest consecutive sequence is " + ans);
    }
}

Python:

class Solution:
    def longestConsecutive(self, nums):
        n = len(nums)

        # Return 0 if array is empty
        if n == 0:
            return 0 

        nums.sort()

        # Track last smaller element
        lastSmaller = float('-inf') 
        # Count current sequence length
        cnt = 0 
        # Track longest sequence length
        longest = 1 

        for i in range(n):
            # If consecutive number exists
            if nums[i] - 1 == lastSmaller:
                # Increment sequence count
                cnt += 1 
                # Update last smaller element
                lastSmaller = nums[i] 
            # If consecutive number doesn't exist
            elif nums[i] != lastSmaller:
                # Reset count for new sequence
                cnt = 1 
                # Update last smaller element
                lastSmaller = nums[i] 
            # Update longest if needed
            longest = max(longest, cnt) 
        return longest

# Sample array
a = [100, 4, 200, 1, 3, 2]

# Create an instance of solution class
solution = Solution() 
# Function call for finding longest consecutive sequence
ans = solution.longestConsecutive(a) 
print("The longest consecutive sequence is", ans)

JavaScript:

class Solution {
    longestConsecutive(nums) {
        let n = nums.length;

        // Return 0 if array is empty
        if (n === 0) return 0; 

        nums.sort((a, b) => a - b);

        // Track last smaller element
        let lastSmaller = -Infinity; 
        // Count current sequence length
        let cnt = 0; 
        // Track longest sequence length
        let longest = 1; 

        for (let i = 0; i < n; i++) {
            // If consecutive number exists
            if (nums[i] - 1 === lastSmaller) {
                // Increment sequence count
                cnt += 1; 
                // Update last smaller element
                lastSmaller = nums[i]; 
            } 
            // If consecutive number doesn't exist
            else if (nums[i] !== lastSmaller) {
                // Reset count for new sequence
                cnt = 1; 
                // Update last smaller element
                lastSmaller = nums[i]; 
            }
            // Update longest if needed
            longest = Math.max(longest, cnt); 
        }
        return longest;
    }
}

// Sample array
const a = [100, 4, 200, 1, 3, 2];

// Create an instance of solution class
const solution = new Solution(); 
// Function call for finding longest consecutive sequence
const ans = solution.longestConsecutive(a); 
console.log("The longest consecutive sequence is " + ans);

C#:
using System;

public class Solution
{
    public int LongestConsecutive(int[] nums)
    {
        int n = nums.Length;

        // Return 0 if array is empty
        if (n == 0) return 0;

        Array.Sort(nums);

        // Track last smaller element
        int lastSmaller = int.MinValue;
        // Count current sequence length
        int cnt = 0;
        // Track longest sequence length
        int longest = 1;

        for (int i = 0; i < n; i++)
        {
            // If consecutive number exists
            if (nums[i] - 1 == lastSmaller)
            {
                // Increment sequence count
                cnt += 1;
                // Update last smaller element
                lastSmaller = nums[i];
            }
            // If consecutive number doesn't exist
            else if (nums[i] != lastSmaller)
            {
                // Reset count for new sequence
                cnt = 1;
                // Update last smaller element
                lastSmaller = nums[i];
            }
            // Update longest if needed
            longest = Math.Max(longest, cnt);
        }
        return longest;
    }
}

public class Program
{
    public static void Main(string[] args)
    {
        // Sample array
        int[] a = { 100, 4, 200, 1, 3, 2 };

        // Create an instance of solution class
        Solution solution = new Solution();
        // Function call for finding longest consecutive sequence
        int ans = solution.LongestConsecutive(a);
        Console.WriteLine("The longest consecutive sequence is " + ans);
    }
}
Go:

package main

import (
    "fmt"
    "math"
    "sort"
)

func longestConsecutive(nums []int) int {
    n := len(nums)

    // Return 0 if array is empty
    if n == 0 {
        return 0
    }

    sort.Ints(nums) // Sort the array 

    // Track last smaller element
    lastSmaller := math.MinInt
    // Count current sequence length
    cnt := 0
    // Track longest sequence length
    longest := 1

    for i := 0; i < n; i++ {
        // If current is consecutive to lastSmaller
        if nums[i]-1 == lastSmaller {
            // Increment sequence count
            cnt++
            lastSmaller = nums[i]
        } else if nums[i] != lastSmaller {
            // Reset count for new sequence
            cnt = 1
            lastSmaller = nums[i]
        }
        // Update longest if needed
        longest = int(math.Max(float64(longest), float64(cnt)))
    }

    return longest
}


func main() {
    a := []int{100, 4, 200, 1, 3, 2}

    ans := longestConsecutive(a)
    fmt.Printf("The longest consecutive sequence is %d\n", ans)
}    
Complexity Analysis 
Time Complexity: O(NlogN) + O(N), here N is the size of the given array. Here, O(NlogN) is for sorting the array. To find the longest sequence, we use a loop that results in O(N).

Space Complexity: O(1), as we are not using any extra space to solve this problem.
