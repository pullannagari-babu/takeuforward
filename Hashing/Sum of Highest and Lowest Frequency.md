Given an array of n integers, find the sum of the frequencies of the highest occurring number and lowest occurring number.
Example 1
Input: arr = [1, 2, 2, 3, 3, 3]
Output: 4
Explanation: The highest frequency is 3 (element 3), and the lowest frequency is 1 (element 1). Their sum is 3 + 1 = 4.
Example 2
Input: arr = [4, 4, 5, 5, 6]
Output: 3
Explanation: The highest frequency is 2 (elements 4 and 5), and the lowest frequency is 1 (element 6). Their sum is 2 + 1 = 3.
Now your turn!
Input: arr = [10, 9, 7, 7, 8, 8, 8]
Output:
Pick your answer

Sum of Highest and Lowest Frequency
Video thumbnail

21
Theory

Discussion
Brute
|
Optimal
Intuition:

The brute force way to solve this problem will be to count the frequency of each element in the array, and once found, this frequency can be compared with the highest and the lowest frequency. Accordingly, the highest and the lowest frequency can be set.

Approach:

Determine the size of the array. Initialize two variables: one to keep track of the highest frequency and another for the lowest frequency.
Initially, set the highest frequency to zero (to ensure any actual frequency found will be higher and update this value.) and the lowest to the size of the array (to ensure any actual frequency found will be lower and update this value).
Create a visited array to avoid counting the same number multiple times.
Loop through each element in the array. For each element:
If the element has already been counted (visited), skip it.
Otherwise, count how many times this element appears in the array by comparing it with every other element.
Update the highest and lowest frequency variables based on the count of the current element.
Mark all occurrences of this element as visited.
Finally, add the highest and lowest frequencies together and return the result.
Dry Run:

Image 1

1/9

Solution:

C++
Java
Python
JavaScript
C#
Go


package main

import (
	"fmt"
	"math"
)

/* Function to get the sum of highest
and lowest frequency in array */
func sumHighestAndLowestFrequency(nums []int) int {

	// Variable to store the size of array
	n := len(nums)

	/* Variable to store maximum
	and minimum frequency */
	maxFreq := 0
	minFreq := n

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

		/* Update maximum and
		minimum frequencies using math package */
		maxFreq = int(math.Max(float64(maxFreq), float64(freq)))
		minFreq = int(math.Min(float64(minFreq), float64(freq)))
	}

	// Return the required sum
	return maxFreq + minFreq
}

func main() {
	nums := []int{1, 2, 2, 3, 3, 3}

	/* Function call to get the sum of highest
	and lowest frequency in array */
	ans := sumHighestAndLowestFrequency(nums)

	fmt.Println("The sum of highest and lowest frequency in the array is:", ans)
}
Complexity Analysis:

Time Complexity: O(N2) (where N is the size of the array given) – Using two nested loops.

Space Complexity: O(N) – Using a visited array of size N and a couple of variables.

v
