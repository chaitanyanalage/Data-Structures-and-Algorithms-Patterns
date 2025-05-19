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

# Two Pointer - 2: Fast-Slow Pointer Pattern

This is an implementation of the **Fast-Slow Pointer Technique** (also known as Floyd's Tortoise and Hare algorithm) to find the duplicate number in an array.

## Problem Statement

Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive, there is only **one repeated number**. Find and return this duplicate number.

The algorithm must **not modify the array** and should use **only constant extra space**.

### Example:

Input:
```
nums = [1, 3, 4, 2, 2]
```

Output:
```
Duplicate number: 2
```

## Time & Space Complexity

- **Time Complexity:** O(n)
- **Space Complexity:** O(1)

## Approach

The problem is solved using Floyd’s Cycle Detection Algorithm in two phases:

### Phase 1: Detect the Intersection Point
- Use two pointers `slow` and `fast`
- `slow` moves one step at a time: `slow = nums[slow]`
- `fast` moves two steps at a time: `fast = nums[nums[fast]]`
- Loop until they meet (this confirms a cycle)

### Phase 2: Find the Entrance to the Cycle
- Reset `slow` to the start of the array
- Move both `slow` and `fast` one step at a time until they meet
- This point is the duplicate number

## Code

```cpp
#include <iostream>
#include <vector>

int findDuplicate(std::vector<int>& nums) {
    // Phase 1: Find intersection point
    int slow = nums[0], fast = nums[0];
    do {
        slow = nums[slow];
        fast = nums[nums[fast]];
    } while (slow != fast);
    
    // Phase 2: Find cycle entrance
    slow = nums[0];
    while (slow != fast) {
        slow = nums[slow];
        fast = nums[fast];
    }

    return slow;
}

int main() {
    std::vector<int> nums = {1, 3, 4, 2, 2};
    std::cout << "Duplicate number: " << findDuplicate(nums) << std::endl;
    return 0;
}
```

# Two Pointer - 3: Sliding Window Pattern

This is an implementation of the **Sliding Window Pattern** using two pointers to remove duplicates from a sorted array **in-place**.

## Problem Statement

Given a **sorted** array, remove the duplicates **in-place** such that each unique element appears only once. The relative order of the elements should be kept the same.

Return the new length of the array after duplicates have been removed.

### Example:

Input:
```
nums = [1, 1, 2, 2, 3, 4, 4]
```

Output:
```
New length: 4
Modified array: 1 2 3 4
```

## Time & Space Complexity

- **Time Complexity:** O(n)
- **Space Complexity:** O(1)

## Approach

This solution uses a **read pointer** and a **write pointer** to manage duplicate removal:

- `write_pointer` keeps track of the position where the next unique element should go.
- `read_pointer` scans the array looking for unique elements.
- When a new unique element is found, it's written at the `write_pointer` index.

This is a classic example of **sliding window** where one pointer is used to overwrite data and another to scan.

## Code

```cpp
#include <iostream>
#include <vector>

using namespace std;

int removeDuplicates(vector<int>& nums) {
    /*
    Remove duplicates in-place from sorted array.
    Time: O(n), Space: O(1)
    */
    if (nums.empty()) {
        return 0;
    }

    // Position for next unique element
    int write_pointer = 1;

    // Scan through array
    for (int read_pointer = 1; read_pointer < nums.size(); read_pointer++) {
        // Found new unique element
        if (nums[read_pointer] != nums[read_pointer - 1]) {
            nums[write_pointer] = nums[read_pointer];
            write_pointer++;
        }
    }

    return write_pointer;
}

// Example usage:
int main() {
    vector<int> nums = {1, 1, 2, 2, 3, 4, 4};
    int new_length = removeDuplicates(nums);

    cout << "New length: " << new_length << endl;
    cout << "Modified array: ";
    for (int i = 0; i < new_length; i++) {
        cout << nums[i] << " ";
    }
    cout << endl;

    return 0;
}
```
