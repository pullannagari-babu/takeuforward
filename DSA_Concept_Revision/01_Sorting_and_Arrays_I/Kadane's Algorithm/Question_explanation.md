Kadane's Algorithm
Medium

Hints
Company
Given an integer array nums, find the subarray with the largest sum and return the sum of the elements present in that subarray.
A subarray is a contiguous non-empty sequence of elements within an array.
Example 1
Input: nums = [2, 3, 5, -2, 7, -4]
Output: 15
Explanation:
The subarray from index 0 to index 4 has the largest sum = 15
Example 2
Input: nums = [-2, -3, -7, -2, -10, -4]
Output: -2
Explanation:
The element on index 0 or index 3 make up the largest sum when taken as a subarray
Now your turn!
Input: nums = [-1, 2, 3, -1, 2, -6, 5]
Output:
Pick your answer
Constraints
1 <= nums.length <= 105
-104 <= nums[i] <= 104

Follow up question
Can you print the subarray that has the max sum ?

Intuition 
The idea is to store the starting index and the ending index of the subarray. Thus its easily possible to get the subarray with maximum sum afterward without actually storing the subarray elements. On careful observation we can notice that the subarray always starts at the particular index where the sum variable is equal to 0, and at the ending index, the sum always crosses the previous maximum sum. Using this observation print the subarray with maximum sum.

Approach 
Keep a track of the starting index of the subarray inside the loop, using a start variable.
Initialize two variables ansStart and ansEnd with -1, & when the sum crosses the maximum sum, set ansStart to the start variable and ansEnd to the current index i.e. i. Rest of the steps are exact same as Kadane's Algorithm.

Complexity Analysis 
Time Complexity: O(N), for using a single loop running N times, where N is the size of the array.

Space Complexity: O(1), for not using any extra space.
