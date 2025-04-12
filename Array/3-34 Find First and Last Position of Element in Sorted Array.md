Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1]. You must write an algorithm with O(log n) runtime complexity.

https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/

java
```java
public int[] searchRange(int[] nums, int target) {
    int index = binarySearch(nums, target);
    if (index == -1) {
        return new int[]{-1, -1};
    }
    int left = index;
    int right = index;

    while (left - 1 >= 0 && nums[left - 1] == target) {
        left--;
    }

    while (right + 1 < nums.length && nums[right + 1] == target) {
        right++;
    }
    return new int[]{left, right};

}

public int binarySearch(int[] nums, int target) {
    if (nums.length == 0 || nums[0] > target || nums[nums.length - 1] < target){
        return -1;
    }

    int left = 0;
    int right = nums.length;
    while (left < right) {
        int mid = left + (right - left) >> 1;
        if (nums[mid] == target) {
            return mid;
        } else if (nums[mid] > target) {
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    return -1;
}
```
c#
```csharp
public class Solution {
    public int[] SearchRange(int[] nums, int target) {
        int index = BinarySearch(nums, target);
        if (index == -1) {
            return new int[]{-1, -1};
        }
        
        int left = index;
        int right = index;
        
        while (left - 1 >= 0 && nums[left - 1] == target) {
            left--;
        }
        
        while (right + 1 < nums.Length && nums[right + 1] == target) {
            right++;
        }
        
        return new int[]{left, right};
    }
    
    public int BinarySearch(int[] nums, int target) {
        if (nums.Length == 0 || nums[0] > target || nums[nums.Length - 1] < target) {
            return -1;
        }
        
        int left = 0;
        int right = nums.Length;
        
        while (left < right) {
            int mid = left + (right - left) >> 1;
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] > target) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        
        return -1;
    }
}
```

Time Complexity: O(log n + k), Binary search O(log n), Expanding to find boundaries O(k), where k is the number of occurrences of the target

Space Complexity: O(1) as only use a constant amount of extra space