# **Two Pointer Pattern**
Master the art of solving array and string problems using two pointers.

## **Contents**
- Practice
- Visualizer
- Two Pointer Pattern

## **Overview**
The two-pointer technique is a powerful algorithmic pattern that uses two pointers to traverse an array or string, often moving in tandem or in opposite directions. This pattern can transform O(n²) solutions into O(n) by eliminating nested loops.

## **Core Concepts**
### **Types of Two-Pointer Movements**
#### **Opposite Direction**
- Start from both ends
- Move towards center
- Used for palindromes, container problems
- Efficient for sorted arrays

#### **Same Direction**
- Start from beginning
- Move at different speeds
- Used for cycle detection
- Efficient for linked lists

#### **Window-Like Movement**
- Maintain a gap between pointers
- Used for subarray problems
- Dynamic size windows
- Fixed distance tracking

---

## **Common Applications**
### **Array Operations**
- Finding pairs with target sum
- Three sum variations
- Container with most water
- Removing duplicates

### **String Manipulations**
- Palindrome verification
- Reversing strings
- Character matching
- Substring problems

### **Linked List Operations**
- Finding middle element
- Cycle detection
- Intersection point
- Merging sorted lists

---

## **Implementation Patterns**
### **1. Opposite Direction Pattern**
Used for:
- Sorted arrays
- Finding pairs
- Optimizing space complexity

### **C++ Code: Two Sum (Sorted Array)**
```cpp
#include <vector>
#include <iostream>

using namespace std;

vector<int> twoSum(vector<int>& numbers, int target) {
    int left = 0, right = numbers.size() - 1;
    
    while (left < right) {
        int sum = numbers[left] + numbers[right];
        
        if (sum == target)
            return {left + 1, right + 1}; // 1-based indexing
        else if (sum < target)
            left++;
        else
            right--;
    }
    
    return {}; // No solution found
}

// Example usage
int main() {
    vector<int> numbers = {2, 7, 11, 15};
    int target = 9;
    vector<int> result = twoSum(numbers, target);
    
    for (int num : result)
        cout << num << " ";
    return 0;
}
```

... (Additional code continues for other patterns, following the structure)

## **Conclusion**
The two-pointer pattern is a powerful technique that optimizes solutions for a variety of problems, from searching and sorting to substring analysis and optimization challenges.

This README provides implementations in C++ for various problems. You can explore these techniques further by practicing them with different inputs and edge cases.

Happy Coding! 🚀
