Print the matrix in spiral manner
Medium
Hints
Company
Given an M * N matrix, print the elements in a clockwise spiral manner.
Return an array with the elements in the order of their appearance when printed in a spiral manner.
Example 1
Input: matrix = [[1, 2, 3], [4 ,5 ,6], [7, 8, 9]]
Output: [1, 2, 3, 6, 9, 8, 7, 4, 5]
Explanation:
The elements in the spiral order are 1, 2, 3 -> 6, 9 -> 8, 7 -> 4, 5
Example 2
Input: matrix = [[1, 2, 3, 4], [5, 6, 7, 8]]
Output: [1, 2, 3, 4, 8, 7, 6, 5]
Explanation:
The elements in the spiral order are 1, 2, 3, 4 -> 8, 7, 6, 5
Now your turn!
Input: matrix = [[1, 2], [3, 4], [5, 6], [7, 8]]
Output:
Pick your answer

Intuition
The idea is to use four separate loops to print the array elements in spiral. 1st loop will print the elements from left to right. 2nd loop will print the elements from top to bottom. 3rd loop will print the elements from right to left. 4th loop will print the elements from bottom to top.

Approach 
Initialize four variables top as 0, left as 0, bottom as TotalRow - 1, right as TotalColumn - 1.
Iterate till top is less than or equal to bottom and left less than or equal to right
For moving left to right use a loop(say i) and add the elements. Increment top by 1.
For moving top to bottom use another loop and add the elements in answer. Decrement right by 1.
If top is less than or equal to bottom then for moving right to left use another loop and add the elements in answer. Decrement bottom by 1.
If left is less than or equal to right the for moving bottom to top take another loop and add the elements in answer. Increment left by 1. Lastly, return the answer.
Illustration 


C++:

#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    //Function to print matrix in spiral manner.
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
         // Define ans vector to store the result
        vector<int> ans; 
        
        // Number of rows
        int n = matrix.size();

        // Number of columns
        int m = matrix[0].size();
        
        // Initialize pointers for traversal
        int top = 0, left = 0;
        int bottom = n - 1, right = m - 1;
        
        // Traverse the matrix in spiral order
        while (top <= bottom && left <= right) {

            // Traverse from left to right
            for (int i = left; i <= right; ++i) {
                ans.push_back(matrix[top][i]);
            }

            top++;
            
            // Traverse from top to bottom
            for (int i = top; i <= bottom; ++i) {
                ans.push_back(matrix[i][right]);
            }
            right--;
            
            // Traverse from right to left
            if (top <= bottom) {
                for (int i = right; i >= left; --i) {
                    ans.push_back(matrix[bottom][i]);
                }
                bottom--;
            }
            
            // Traverse from bottom to top
            if (left <= right) {
                for (int i = bottom; i >= top; --i) {
                    ans.push_back(matrix[i][left]);
                }
                left++;
            }
        }
        
        //Return the ans
        return ans;
    }
};

int main() {
    vector<vector<int>> mat = {
        {1, 2, 3, 4},
        {5, 6, 7, 8},
        {9, 10, 11, 12},
        {13, 14, 15, 16}
    };
    
    // Create an instance of the Solution class
    Solution finder;
    
    // Get spiral order using class method
    vector<int> ans = finder.spiralOrder(mat);
    
    cout << "Elements in spiral order are: ";
    for (int i = 0; i < ans.size(); ++i) {
        cout << ans[i] << " ";
    }
    cout << endl;
    
    return 0;
}

Java:
import java.util.*;

class Solution {
    //Function to print matrix in spiral manner
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> ans = new ArrayList<>();
        
        // Number of rows
        int n = matrix.length;

        // Number of columns
        int m = matrix[0].length;
        
        // Initialize pointers for traversal
        int top = 0, left = 0;      
        int bottom = n - 1, right = m - 1;
        
        // Traverse the matrix in spiral order
        while (top <= bottom && left <= right) {
            // Traverse from left to right
            for (int i = left; i <= right; ++i) {
                ans.add(matrix[top][i]);
            }
            top++;
            
            // Traverse from top to bottom
            for (int i = top; i <= bottom; ++i) {
                ans.add(matrix[i][right]);
            }
            right--;
            
            // Traverse from right to left
            if (top <= bottom) {
                for (int i = right; i >= left; --i) {
                    ans.add(matrix[bottom][i]);
                }
                bottom--;
            }
            
            // Traverse from bottom to top
            if (left <= right) {
                for (int i = bottom; i >= top; --i) {
                    ans.add(matrix[i][left]);
                }
                left++;
            }
        }
        
        //Return the ans
        return ans;
    }
    
    public static void main(String[] args) {
        int[][] mat = {
            {1, 2, 3, 4},
            {5, 6, 7, 8},
            {9, 10, 11, 12},
            {13, 14, 15, 16}
        };
        
        // Create an instance of the Solution class
        Solution finder = new Solution();
        
        // Get spiral order using class method
        List<Integer> ans = finder.spiralOrder(mat);
       
        System.out.print("Elements in spiral order are: ");
        for (int i = 0; i < ans.size(); ++i) {
            System.out.print(ans.get(i) + " ");
        }
        System.out.println();
    }
}

Python:

from typing import List

class Solution:
    # Function to print matrix in spiral manner
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        ans = []
        
        # Number of rows
        n = len(matrix)

         # Number of columns
        m = len(matrix[0])
        
        # Initialize pointers for traversal
        top, left = 0, 0
        bottom, right = n - 1, m - 1
        
        # Traverse the matrix in spiral order
        while top <= bottom and left <= right:
            # Traverse from left to right
            for i in range(left, right + 1):
                ans.append(matrix[top][i])
            top += 1
            
            # Traverse from top to bottom
            for i in range(top, bottom + 1):
                ans.append(matrix[i][right])
            right -= 1
            
            # Traverse from right to left
            if top <= bottom:
                for i in range(right, left - 1, -1):
                    ans.append(matrix[bottom][i])
                bottom -= 1
            
            # Traverse from bottom to top
            if left <= right:
                for i in range(bottom, top - 1, -1):
                    ans.append(matrix[i][left])
                left += 1
        
        #Return the ans
        return ans

# Test the solution
if __name__ == "__main__":
    mat = [
        [1, 2, 3, 4],
        [5, 6, 7, 8],
        [9, 10, 11, 12],
        [13, 14, 15, 16]
    ]
    
    # Create an instance of the Solution class
    finder = Solution()
    
    # Get spiral order using class method
    ans = finder.spiralOrder(mat)

    print("Elements in spiral order are:", ans)


JavaScript:

class Solution {
   //Function to print matrix in spiral manner
    spiralOrder(matrix) {
        let ans = [];
        
        // Number of rows
        let n = matrix.length;

        // Number of columns
        let m = matrix[0].length;
        
        // Initialize pointers for traversal
        let top = 0, left = 0;
        let bottom = n - 1, right = m - 1;
        
        // Traverse the matrix in spiral order
        while (top <= bottom && left <= right) {
            // Traverse from left to right
            for (let i = left; i <= right; ++i) {
                ans.push(matrix[top][i]);
            }
            top++;
            
            // Traverse from top to bottom
            for (let i = top; i <= bottom; ++i) {
                ans.push(matrix[i][right]);
            }
            right--;
            
            // Traverse from right to left
            if (top <= bottom) {
                for (let i = right; i >= left; --i) {
                    ans.push(matrix[bottom][i]);
                }
                bottom--;
            }
            
            // Traverse from bottom to top
            if (left <= right) {
                for (let i = bottom; i >= top; --i) {
                    ans.push(matrix[i][left]);
                }
                left++;
            }
        }
        
        //Return the ans
        return ans;
    }
}

// Test the solution
let mat = [
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12],
    [13, 14, 15, 16]
];

// Create an instance of the Solution class
let finder = new Solution();

// Get spiral order using class method
let ans = finder.spiralOrder(mat);

console.log("Elements in spiral order are:", ans.join(" "));


C#:

using System;
using System.Collections.Generic;
using System.Linq;

public class Solution
{
    //Function to print matrix in spiral manner
    public List<int> SpiralOrder(List<List<int>> matrix)
    {
        List<int> ans = new List<int>();
        
        // Number of rows
        int n = matrix.Count;
        if (n == 0) return ans;

        // Number of columns
        int m = matrix[0].Count;
        if (m == 0) return ans;
        
        // Initialize pointers for traversal
        int top = 0, left = 0;
        int bottom = n - 1, right = m - 1;
        
        // Traverse the matrix in spiral order
        while (top <= bottom && left <= right)
        {
            // Traverse from left to right
            for (int i = left; i <= right; ++i)
            {
                ans.Add(matrix[top][i]);
            }
            top++;
            
            // Traverse from top to bottom
            for (int i = top; i <= bottom; ++i)
            {
                ans.Add(matrix[i][right]);
            }
            right--;
            
            // Traverse from right to left
            if (top <= bottom)
            {
                for (int i = right; i >= left; --i)
                {
                    ans.Add(matrix[bottom][i]);
                }
                bottom--;
            }
            
            // Traverse from bottom to top
            if (left <= right)
            {
                for (int i = bottom; i >= top; --i)
                {
                    ans.Add(matrix[i][left]);
                }
                left++;
            }
        }
        
        //Return the ans
        return ans;
    }
}

public class Program
{
    public static void Main(string[] args)
    {
        // Test the solution
        List<List<int>> mat = new List<List<int>>
        {
            new List<int> {1, 2, 3, 4},
            new List<int> {5, 6, 7, 8},
            new List<int> {9, 10, 11, 12},
            new List<int> {13, 14, 15, 16}
        };

        // Create an instance of the Solution class
        Solution finder = new Solution();

        // Get spiral order using class method
        List<int> ans = finder.SpiralOrder(mat);

        Console.WriteLine("Elements in spiral order are: " + string.Join(" ", ans));
    }
}

Go:

package main

import (
    "fmt"
)

func spiralOrder(matrix [][]int) []int {
    // Define ans slice to store the result
    ans := []int{}

    // Number of rows and columns
    n := len(matrix)
    m := len(matrix[0])

    // Initialize pointers for traversal
    top, left := 0, 0
    bottom, right := n-1, m-1

    // Traverse the matrix in spiral order
    for top <= bottom && left <= right {
        // Traverse from left to right
        for i := left; i <= right; i++ {
            ans = append(ans, matrix[top][i])
        }
        top++

        // Traverse from top to bottom
        for i := top; i <= bottom; i++ {
            ans = append(ans, matrix[i][right])
        }
        right--

        // Traverse from right to left
        if top <= bottom {
            for i := right; i >= left; i-- {
                ans = append(ans, matrix[bottom][i])
            }
            bottom--
        }

        // Traverse from bottom to top
        if left <= right {
            for i := bottom; i >= top; i-- {
                ans = append(ans, matrix[i][left])
            }
            left++
        }
    }

    // Return the ans
    return ans
}

func main() {
    mat := [][]int{
        {1, 2, 3, 4},
        {5, 6, 7, 8},
        {9, 10, 11, 12},
        {13, 14, 15, 16},
    }

    ans := spiralOrder(mat)

    fmt.Print("Elements in spiral order are: ")
    for _, v := range ans {
        fmt.Print(v, " ")
    }
    fmt.Println()
}

Complexity Analysis 
Time Complexity: O(MxN) since all the elements are being traversed once and there are total N x M elements ( M elements in each row and total N rows) so the time complexity will be O(N x M).

Space Complexity: O(1) as extra space to store answer is not considered.