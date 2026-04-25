Intuition

In this approach, we refine the brute-force method by focusing only on potential starting numbers of sequences, rather than searching for sequences for every array element. This targeted strategy enhances efficiency using a Set data structure.

Approach

We will use two variables, cnt to store the length of the current sequence and longest to store the maximum length found.

First, all array elements are placed into a set data structure.

For each element x that can start a sequence (i.e., x - 1 does not exist in the set) we follow the below steps:

Initialize cnt to 1, indicating the starting element of a new sequence.
Utilize the set to search for consecutive elements such as x + 1, x + 2, and so on, to determine the maximum possible length of the current sequence. Update cnt accordingly.
Compare cnt with longest and update longest to hold the maximum value (longest = max(longest, cnt)).
Finally, longest will contain the length of the longest consecutive sequence found in the array.

Dry Run

https://static.takeuforward.org/premium/Hashing/FAQs/Longest%20Consecutive%20Sequence%20in%20an%20Array-dup/1.svg-2fed0UqH
https://static.takeuforward.org/premium/Hashing/FAQs/Longest%20Consecutive%20Sequence%20in%20an%20Array-dup/2.png-QvnlkPGv
https://static.takeuforward.org/premium/Hashing/FAQs/Longest%20Consecutive%20Sequence%20in%20an%20Array-dup/3.svg--lwj7YmE
https://static.takeuforward.org/premium/Hashing/FAQs/Longest%20Consecutive%20Sequence%20in%20an%20Array-dup/4.png-GxcFLfp2
https://static.takeuforward.org/premium/Hashing/FAQs/Longest%20Consecutive%20Sequence%20in%20an%20Array-dup/5.svg-1RPTA06F

Please refer to the video for complete dry-run.

C++:


#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    int longestConsecutive(vector<int>& a) {
        int n = a.size();
        // If the array is empty
        if (n == 0) return 0; 
    
        // Initialize the longest sequence length
        int longest = 1; 
        unordered_set<int> st;
    
        // Put all the array elements into the set
        for (int i = 0; i < n; i++) {
            st.insert(a[i]);
        }
    
        /* Traverse the set to 
           find the longest sequence  */
        for (auto it : st) {
            // Check if 'it' is a starting number of a sequence
            if (st.find(it - 1) == st.end()) {
                // Initialize the count of the current sequence
                int cnt = 1; 
                // Starting element of the sequence
                int x = it; 
    
                // Find consecutive numbers in the set
                while (st.find(x + 1) != st.end()) {
                    // Move to the next element in the sequence
                    x = x + 1; 
                    // Increment the count of the sequence
                    cnt = cnt + 1; 
                }
                // Update the longest sequence length
                longest = max(longest, cnt);
            }
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
        // If the array is empty
        if (n == 0) return 0;

        // Initialize the longest sequence length
        int longest = 1; 
        Set<Integer> st = new HashSet<>();

        // Put all the array elements into the set
        for (int i = 0; i < n; i++) {
            st.add(nums[i]);
        }

        /* Traverse the set to 
           find the longest sequence */
        for (int it : st) {
            // Check if 'it' is a starting number of a sequence
            if (!st.contains(it - 1)) {
                // Initialize the count of the current sequence
                int cnt = 1; 
                // Starting element of the sequence
                int x = it; 

                // Find consecutive numbers in the set
                while (st.contains(x + 1)) {
                    // Move to the next element in the sequence
                    x = x + 1; 
                    // Increment the count of the sequence
                    cnt = cnt + 1; 
                }
                // Update the longest sequence length
                longest = Math.max(longest, cnt);
            }
        }
        return longest;
    }

    public static void main(String[] args) {
        int[] a = {100, 4, 200, 1, 3, 2}; 
        // Create an instance of the solution class
        Solution solution = new Solution(); 
        // Function call to find the longest consecutive sequence
        int ans = solution.longestConsecutive(a); 
        System.out.println("The longest consecutive sequence is " + ans); 
    }
}


Python:
class Solution:
    def longestConsecutive(self, nums):
        n = len(nums)
        # If the array is empty
        if n == 0:
            return 0 

        # Initialize the longest sequence length
        longest = 1 
        st = set()

        # Put all the array elements into the set
        for i in range(n):
            st.add(nums[i])

        # Traverse the set to find the longest sequence
        for it in st:
            # Check if 'it' is a starting number of a sequence
            if it - 1 not in st:
                # Initialize the count of the current sequence
                cnt = 1 
                # Starting element of the sequence
                x = it 

                # Find consecutive numbers in the set
                while x + 1 in st:
                    # Move to the next element in the sequence
                    x = x + 1 
                    # Increment the count of the sequence
                    cnt = cnt + 1 
                # Update the longest sequence length
                longest = max(longest, cnt)
        return longest

if __name__ == "__main__":
    a = [100, 4, 200, 1, 3, 2] 
    # Create an instance of the solution class
    solution = Solution() 
    # Function call to find the longest consecutive sequence
    ans = solution.longestConsecutive(a) 
    print("The longest consecutive sequence is", ans)

JavaScript:
class Solution {
    longestConsecutive(nums) {
        let n = nums.length;
        // If the array is empty
        if (n === 0) return 0;

        // Initialize the longest sequence length
        let longest = 1; 
        let st = new Set();

        // Put all the array elements into the set
        for (let i = 0; i < n; i++) {
            st.add(nums[i]);
        }

        // Traverse the set to find the longest sequence
        for (let it of st) {
            // Check if 'it' is a starting number of a sequence
            if (!st.has(it - 1)) {
                // Initialize the count of the current sequence
                let cnt = 1; 
                // Starting element of the sequence
                let x = it; 

                // Find consecutive numbers in the set
                while (st.has(x + 1)) {
                    // Move to the next element in the sequence
                    x = x + 1; 
                    // Increment the count of the sequence
                    cnt = cnt + 1; 
                }
                // Update the longest sequence length
                longest = Math.max(longest, cnt);
            }
        }
        return longest;
    }
}

// Sample array
const a = [100, 4, 200, 1, 3, 2]; 
// Create an instance of the solution class
const solution = new Solution(); 
// Function call to find the longest consecutive sequence
const ans = solution.longestConsecutive(a); 
console.log("The longest consecutive sequence is " + ans);

C#:
using System;
using System.Collections.Generic;

public class Solution 
    {
        public int LongestConsecutive(int[] nums) 
        {
            int n = nums.Length;
            // If the array is empty
            if (n == 0) return 0;

            // Initialize the longest sequence length
            int longest = 1; 
            var st = new HashSet<int>();

            // Put all the array elements into the set
            for (int i = 0; i < n; i++) {
                st.Add(nums[i]);
            }

            // Traverse the set to find the longest sequence
            foreach (int it in st) {
                // Check if 'it' is a starting number of a sequence
                if (!st.Contains(it - 1)) {
                    // Initialize the count of the current sequence
                    int cnt = 1; 
                    // Starting element of the sequence
                    int x = it; 

                    // Find consecutive numbers in the set
                    while (st.Contains(x + 1)) {
                        // Move to the next element in the sequence
                        x = x + 1; 
                        // Increment the count of the sequence
                        cnt = cnt + 1; 
                    }
                    // Update the longest sequence length
                    longest = Math.Max(longest, cnt);
                }
            }
            return longest;
        }
    

    public static void Main(string[] args)
    {
        // Sample array
        int[] a = { 100, 4, 200, 1, 3, 2 }; 
        // Create an instance of the solution class
        Solution solution = new Solution(); 
        // Function call to find the longest consecutive sequence
        int ans = solution.LongestConsecutive(a); 
        Console.WriteLine("The longest consecutive sequence is " + ans);
    }
}
Go:

package main

import "fmt"

// longestConsecutive finds the longest consecutive sequence in an array
func longestConsecutive(nums []int) int {
    n := len(nums)
    // If the array is empty
    if n == 0 {
        return 0
    }

    // Initialize the longest sequence length
    longest := 1
    st := make(map[int]struct{})

    // Put all the array elements into the set
    for _, v := range nums {
        st[v] = struct{}{}
    }

    /* Traverse the set to
       find the longest sequence */
    for num := range st {
        // Check if 'num' is a starting number of a sequence
        if _, exists := st[num-1]; !exists {
            // Initialize the count of the current sequence
            cnt := 1
            // Starting element of the sequence
            x := num

            // Find consecutive numbers in the set
            for {
                if _, ok := st[x+1]; ok {
                    x = x + 1
                    cnt = cnt + 1
                } else {
                    break
                }
            }

            // Update the longest sequence length
            if cnt > longest {
                longest = cnt
            }
        }
    }
    return longest
}

func main() {
    a := []int{100, 4, 200, 1, 3, 2}

    // Create an instance and call longestConsecutive
    ans := longestConsecutive(a)
    fmt.Printf("The longest consecutive sequence is %d\n", ans)
}
Complexity Analysis 

Time Complexity: O(N) + O(2xN) ~ O(3xN), where N is the size of the array. The function takes O(N) to insert all elements into the set data structure. After that, for every starting element, we find the consecutive elements. Although nested loops are used, the set will be traversed at most twice in the worst case. Therefore, the time complexity is O(2xN) instead of O(N2).

Space Complexity: O(N), as we use a set data structure to solve this problem.
Note: The time complexity assumes that we use an unordered_set, which has O(1) time complexity for set operations.

In the worst case, if the set operations take O(N), the total time complexity would be approximately O(N2). If we use a set instead of an unordered_set, the set operations will have a time complexity of O(logN), resulting in a total time complexity of O(NlogN).
