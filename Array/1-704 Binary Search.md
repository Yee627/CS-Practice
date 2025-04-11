https://leetcode.com/problems/binary-search/description/

Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.

Java
```java
public int search(int[] nums, int target) 
{
    if (target < nums[0] || target > nums[nums.length - 1]){
        return -1;
    }

    int left = 0, right = nums.length - 1;
    while (left <= right){
        int mid = left + ((right - left) >> 1);
        if (nums[mid] == target){
            return mid;
        }
        else if (nums[mid] < target){
            left = mid + 1;
        }
        else if (nums[mid] > target){
            right = mid - 1;
        }
    }
    return -1;
}
```

C#
```csharp
public int Search(int[] nums, int target) {
    if (target < nums[0] || target > nums[nums.Length - 1]){
        return -1;
    }
    int left = 0, right = nums.Length - 1;
    while (left <= right){
        int mid = left + ((right - left) >> 1);
        if (nums[mid] == target){
            return mid;
        }
        else if (nums[mid] < target){
            left = mid + 1;
        }
        else if (nums[mid] > target){
            right = mid - 1;
        }
    }
    return -1;
}
```

- mid-point calculation: Uses left + ((right - left) >> 1) instead of (left + right) / 2 to avoid potential integer overflow
- time complexity is O(log n) and space complexity is O(1)