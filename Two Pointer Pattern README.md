# Two Pointer - 1: Opposite Direction Pattern

This is an implementation of the **Two Pointer Technique** (Opposite Direction Pattern) to solve the **Two Sum II** problem on a sorted array.

## Problem Statement

Given a **sorted array** of integers and a **target** value, return the 1-based indices of the two numbers such that they add up to the target.

### Example:

Input:
```
numbers = [2, 7, 11, 15]
target = 9
```

Output:
```
[1, 2]
```

Explanation: `numbers[0] + numbers[1] = 2 + 7 = 9`

## Time & Space Complexity

- **Time Complexity:** O(n)
- **Space Complexity:** O(1)

## Approach

This solution uses two pointers:
- One starting from the beginning (`left`)
- One starting from the end (`right`)

At each step:
- If the sum is equal to the target → return the indices
- If the sum is less than the target → move the `left` pointer to the right
- If the sum is greater than the target → move the `right` pointer to the left

## Code

```cpp
#include <iostream>
#include <vector>

using namespace std;

vector<int> twoSum(vector<int>& numbers, int target) {
    int left = 0, right = numbers.size() - 1;

    while (left < right) {
        int current_sum = numbers[left] + numbers[right];

        if (current_sum == target) {
            return {left + 1, right + 1};  // 1-based indexing
        } else if (current_sum < target) {
            left++;
        } else {
            right--;
        }
    }

    return {};
}

int main() {
    vector<int> numbers = {2, 7, 11, 15};
    int target = 9;
    vector<int> result = twoSum(numbers, target);

    if (!result.empty()) {
        cout << "[" << result[0] << ", " << result[1] << "]" << endl;
    } else {
        cout << "No solution found" << endl;
    }

    return 0;
}
```
