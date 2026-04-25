Intuition

In this approach, tryutilize the concept of prefix XOR to solve this problem. The prefix XOR of a subarray ending at index 𝑖 is simply the XOR of all the elements from the start of the array up to index 𝑖.

Observation:
Assume the prefix XOR of a subarray ending at index i is xr. To find subarrays with XOR equal to k, we note that if a subarray has XOR k, then the prefix XOR of the remaining part will be xr XOR k (where XOR denotes the XOR operation). So, for a subarray ending at index i with prefix XOR xr, if we remove the part with prefix XOR xr XOR k, the remaining part will have XOR k. The below image will clarify this concept.

https://static.takeuforward.org/premium/Hashing/FAQs/Count%20subarrays%20with%20given%20xor%20K-dup/illustration-ouIHQF8O
https://static.takeuforward.org/premium/Hashing/FAQs/Count%20subarrays%20with%20given%20xor%20K-dup/proof-bCMqTDaJ

XOR
XOR
Instead of directly searching for subarrays with XOR k, we use a map to count subarrays with prefix XOR xr XOR k. The map stores each prefix XOR and its count. At each index i, we check the map for xr XOR k and add the count to our result. We repeat this for all indices from 0 to n-1. This approach efficiently finds the number of subarrays with XOR k using the prefix XOR concept and a map.
Approach

The steps are as follows:

First start by declaring a map to store the prefix XORs and their counts, and set the value of 0 as 1 in the map. This setup is crucial because it helps us handle cases where the prefix XOR itself equals the target value k.
Run a loop from index 0 to n-1 (where n is the size of the array). For each index i, XOR the current element arr[i] with the existing prefix XOR. Then calculate the required prefix XOR xr^ k to check its occurrence.
Now, add the occurrence of the prefix XOR xr ^ k from the map to our answer. This gives the count of subarrays that have the desired XOR value k. Finally, store the current prefix XOR xr in the map, increasing its occurrence by 1 to keep track of its count for future subarrays.
Question: Why set the value of 0 beforehand?

To understand this, consider the array [3, 3, 1, 1, 1] with k = 3. At index 0, the total prefix XOR is 3, and k is also 3. So, the prefix XOR xr XOR k will be 3 XOR 3 = 0. If the value 0 is not previously set in the map, we will add 0 to our answer, incorrectly indicating that no subarray with XOR 3 has been found. However, index 0 itself is a subarray with XOR k = 3. Setting the value of 0 as 1 in the map beforehand avoids this issue.

Dry Run
https://static.takeuforward.org/premium/Hashing/FAQs/Count%20subarrays%20with%20given%20xor%20K-dup/1.svg-dV5twSFk
https://static.takeuforward.org/premium/Hashing/FAQs/Count%20subarrays%20with%20given%20xor%20K-dup/2.svg-_FqOKJ75
https://static.takeuforward.org/premium/Hashing/FAQs/Count%20subarrays%20with%20given%20xor%20K-dup/4.svg-hLSZLuiE
https://static.takeuforward.org/premium/Hashing/FAQs/Count%20subarrays%20with%20given%20xor%20K-dup/3.svg-P3AIhNQG
Please refer to the video for complete dry-run.

C++

#include <bits/stdc++.h>
using namespace std;

class Solution
{
public:
    int subarraysWithXorK(vector<int>& nums, int k)
    {
        int n = nums.size(); 
        int xr = 0;
        map<int, int> mpp; 
        // setting the value of 0.
        mpp[xr]++; 
        int cnt = 0;

        for (int i = 0; i < n; i++) {
            // prefix XOR till index i:
            xr = xr ^ nums[i];

            // By formula: x = xr^k:
            int x = xr ^ k;

            // add the occurrence of xr^k to the count:
            cnt += mpp[x];

            // Insert the prefix xor till index i into the map:
            mpp[xr]++;
        }
        return cnt;
    }
};

int main()
{
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
    public int subarraysWithXorK(int[] nums, int k) {
        int n = nums.length;
        int xr = 0;
        Map<Integer, Integer> mpp = new HashMap<>();
        // setting the value of 0.
        mpp.put(xr, mpp.getOrDefault(xr, 0) + 1);
        int cnt = 0;

        for (int i = 0; i < n; i++) {
            // prefix XOR till index i:
            xr = xr ^ nums[i];

            // By formula: x = xr ^ k:
            int x = xr ^ k;

            // add the occurrence of xr ^ k to the count:
            cnt += mpp.getOrDefault(x, 0);

            // Insert the prefix xor till index i into the map:
            mpp.put(xr, mpp.getOrDefault(xr, 0) + 1);
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
    def subarraysWithXorK(self, nums, k):
        n = len(nums)
        xr = 0
        mpp = {}
        # setting the value of 0.
        mpp[xr] = mpp.get(xr, 0) + 1
        cnt = 0

        for i in range(n):
            # prefix XOR till index i:
            xr = xr ^ nums[i]

            # By formula: x = xr ^ k:
            x = xr ^ k

            # add the occurrence of xr ^ k to the count:
            cnt += mpp.get(x, 0)

            # Insert the prefix xor till index i into the map:
            mpp[xr] = mpp.get(xr, 0) + 1

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
    subarraysWithXorK(nums, k) {
        const n = nums.length;
        let xr = 0;
        const mpp = new Map();
        // setting the value of 0.
        mpp.set(xr, (mpp.get(xr) || 0) + 1);
        let cnt = 0;

        for (let i = 0; i < n; i++) {
            // prefix XOR till index i:
            xr = xr ^ nums[i];

            // By formula: x = xr ^ k:
            const x = xr ^ k;

            // add the occurrence of xr ^ k to the count:
            cnt += mpp.get(x) || 0;

            // Insert the prefix xor till index i into the map:
            mpp.set(xr, (mpp.get(xr) || 0) + 1);
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
using System.Collections.Generic;

public class Solution
{
    public int SubarraysWithXorK(int[] nums, int k)
    {
        int n = nums.Length;
        int xr = 0;
        var mpp = new Dictionary<int, int>();
        // setting the value of 0.
        mpp[xr] = 1;
        int cnt = 0;

        for (int i = 0; i < n; i++)
        {
            // prefix XOR till index i:
            xr = xr ^ nums[i];

            // By formula: x = xr ^ k:
            int x = xr ^ k;

            // add the occurrence of xr ^ k to the count:
            if (mpp.ContainsKey(x))
            {
                cnt += mpp[x];
            }

            // Insert the prefix xor till index i into the map:
            if (mpp.ContainsKey(xr))
            {
                mpp[xr]++;
            }
            else
            {
                mpp[xr] = 1;
            }
        }
        return cnt;
    }

public static void Main(string[] args)
    {
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

// subarraysWithXorK counts the number of subarrays with XOR k
func subarraysWithXorK(nums []int, k int) int {
    n := len(nums)
    xr := 0
    // map to store frequency of prefix XOR values
    mpp := make(map[int]int)
    // setting the value of 0.
    mpp[0]++
    cnt := 0

    for i := 0; i < n; i++ {
        // prefix XOR till index i:
        xr = xr ^ nums[i]

        // By formula: x = xr^k:
        x := xr ^ k

        // add the occurrence of xr^k to the count:
        cnt += mpp[x]

        // Insert the prefix xor till index i into the map:
        mpp[xr]++
    }
    return cnt
}

func main() {
    a := []int{4, 2, 2, 6, 4}
    k := 6

    // Create an instance of the Solution class (conceptual)
    // Function call to get the result
    ans := subarraysWithXorK(a, k)

    fmt.Printf("The number of subarrays with XOR k is: %d\n", ans)
}


Complexity Analysis 

Time Complexity: O(N) or O(NxlogN), where N is the size of the array. If we use an unordered_map in C++, the time complexity is O(N). However, with a map data structure, the time complexity is O(NxlogN). In the worst case for an unordered_map, the searching time can increase to O(N), making the overall time complexity O(N2).

Space Complexity: O(N), as we are using a map data structure.
