Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

https://leetcode.com/problems/squares-of-a-sorted-array/description/

java
```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        int left = 0, right = nums.length - 1;
        int[] result = new int[nums.length];
        int index = result.length - 1;
        while (left <= right) {
            if (nums[left] * nums[left] > nums[right] * nums[right]) {
                result[index] = nums[left] * nums[left];
                index--;
                left++;
            } else {
                result[index] = nums[right] * nums[right];
                index--;
                right--;
            }
        }
        return result;
    }
}
```

c#
```csharp
public class Solution {
    public int[] SortedSquares(int[] nums) {
        int left = 0, right = nums.Length - 1;
        int[] result = new int[nums.Length];
        int index = result.Length - 1;
        
        while (left <= right) {
            if (nums[left] * nums[left] > nums[right] * nums[right]) {
                result[index] = nums[left] * nums[left];
                index--;
                left++;
            } else {
                result[index] = nums[right] * nums[right];
                index--;
                right--;
            }
        }
        
        return result;
    }
}

```

- Initialize pointers at the start and end of the array, the largest squared value is either the start or the end of the current array, so compare both end of this array
- Time Complexity: O(n) where n is the length of the input array
- Space Complexity*: O(n), as only creating a new array of the same size as the input