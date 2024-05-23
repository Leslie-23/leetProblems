# 3 Sum problem.
```
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var threeSum = function(nums) {
    nums.sort((a, b) => a - b); // Step 1: Sort the array
    const result = [];
    
    for (let i = 0; i < nums.length; i++) {
        // Step 2: Skip duplicates for the fixed element
        if (i > 0 && nums[i] === nums[i - 1]) {
            continue;
        }
        
        // Step 3: Use two-pointer technique for the remaining two elements
        let left = i + 1;
        let right = nums.length - 1;
        
        while (left < right) {
            const sum = nums[i] + nums[left] + nums[right];
            if (sum === 0) {
                result.push([nums[i], nums[left], nums[right]]);
                // Skip duplicates for left and right pointers
                while (left < right && nums[left] === nums[left + 1]) left++;
                while (left < right && nums[right] === nums[right - 1]) right--;
                left++;
                right--;
            } else if (sum < 0) {
                left++; // Increase sum by moving left pointer to the right
            } else {
                right--; // Decrease sum by moving right pointer to the left
            }
        }
    }
    
    return result;
};

// Example usage:
const nums = [-1, 0, 1, 2, -1, -4];
console.log(threeSum(nums)); // Output: [[-1, -1, 2], [-1, 0, 1]]
```

The Three Sum problem, often referred to as "3Sum," is a classic algorithmic problem in computer science and competitive programming. Understanding why solving 3Sum is necessary involves recognizing the value it brings in terms of:

Algorithm Design and Problem-Solving Skills:

Algorithm Complexity: The problem teaches important concepts in algorithm design, such as sorting, two-pointer techniques, and managing time complexity. The straightforward brute force solution has a time complexity of 
𝑂
(
𝑛
3
)
O(n 
3
 ), which is inefficient for large datasets. Learning how to optimize this to 
𝑂
(
𝑛
2
)
O(n 
2
 ) with the two-pointer technique is a valuable exercise.
Problem-Solving Patterns: 3Sum is a variant of the subset-sum problem and is closely related to other problems like Two Sum and k-Sum. Solving it helps build a foundation for tackling these and other related problems.
Handling Edge Cases and Duplicates:

Avoiding Duplicates: The requirement to return unique triplets challenges you to handle duplicates effectively. This is a common requirement in real-world problems where data integrity and uniqueness are crucial.
Edge Cases: The problem includes various edge cases, such as arrays with fewer than three elements or arrays where all elements are the same. Addressing these cases sharpens your ability to write robust, error-free code.
Practical Applications:

Financial Transactions: In financial systems, you might need to identify three transactions that sum up to a particular amount, akin to solving the 3Sum problem.
Data Analysis: In data analysis, finding sets of three items that together meet a specific criterion (e.g., three chemical compounds that react together to form a neutral substance) can be framed as a 3Sum problem.
Recommendation Systems: Recommendation algorithms sometimes need to find groups of items that together match a user's preference profile, which can involve similar logic to the 3Sum problem.
Detailed Explanation of the Problem and Its Necessity
Understanding the Problem:

Input: An integer array nums.
Output: All unique triplets [nums[i], nums[j], nums[k]] such that the sum of the triplet is zero.
Constraints:
Indices 
𝑖, j, and k must be different.
The sum 

nums[i]+nums[j]+nums[k] must equal zero.
No duplicate triplets in the output.
Why 3Sum Is Necessary:

Educational Value: It serves as an excellent educational problem to understand more advanced algorithmic techniques beyond brute force. It also reinforces the concept of sorting and efficient searching.
Real-World Relevance: Many real-world problems require finding specific combinations of elements that meet certain criteria. The 3Sum problem is a simplified model of these real-world issues.
Foundation for Complex Problems: Mastering the 3Sum problem prepares you for more complex problems like 4Sum, k-Sum, and other variations where you need to find sets of numbers that meet a specific condition.
Example and Practicality
Consider a scenario in financial technology:

Example: You have a list of daily profits/losses, and you want to identify any three days where the net profit/loss is zero. This is important for detecting anomalies or for making strategic financial decisions.
Example:
Input: nums = [-1, 0, 1, 2, -1, -4]
Output: [[-1, -1, 2], [-1, 0, 1]]
Explanation:
Triplets 

[−1,−1,2] are the only unique combinations that sum to zero.
This helps in identifying the sets of numbers meeting the required condition.
Code Implementation
To solve this problem efficiently:

Sort the Array: Makes it easier to handle duplicates and use the two-pointer technique.
Use a Loop to Fix the First Element: Iterate through each element as the first element of the triplet.
Two-Pointer Technique: For the remaining two elements, use two pointers to find pairs that sum to the negative of the fixed element.
Avoid Duplicates: Ensure the same triplet is not added more than once by skipping duplicate elements.
