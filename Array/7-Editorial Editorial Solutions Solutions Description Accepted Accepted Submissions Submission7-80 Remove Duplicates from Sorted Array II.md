Given an integer array nums sorted in non-decreasing order, remove some duplicates in-place such that each unique element appears at most twice. The relative order of the elements should be kept the same.

https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description/

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums == null || nums.length == 0) {
            return 0;
        }

        int slowIndex = 0;
        for (int fastIndex = 0; fastIndex < nums.length; fastIndex++) {
            int count = 1;
            while (fastIndex + 1 < nums.length && nums[fastIndex] == nums[fastIndex + 1]) {
                fastIndex += 1;
                count += 1;
            }
            for (int i = 1; i <= Math.min(2, count); i++) {
                nums[slowIndex] = nums[fastIndex];
                slowIndex += 1;
            }
        }
        return slowIndex;
    }
}
```

```csharp
public class Solution {
    public int RemoveDuplicates(int[] nums) {
        if (nums == null || nums.Length == 0) {
            return 0;
        }
        
        int slowIndex = 0;
        for (int fastIndex = 0; fastIndex < nums.Length; fastIndex++) {
            int count = 1;
            while (fastIndex + 1 < nums.Length && nums[fastIndex] == nums[fastIndex + 1]) {
                fastIndex += 1;
                count += 1;
            }
            
            for (int i = 1; i <= Math.Min(2, count); i++) {
                nums[slowIndex] = nums[fastIndex];
                slowIndex += 1;
            }
        }
        
        return slowIndex;
    }
}
```

- implements the "two-pointer", The fastIndex scans through the array, identifying duplicates and counting them. The slowIndex keeps track of where to place the next valid element, keeping at most 2 occurrences of each number
- Time Complexity: O(n). The algorithm makes a single pass through the array
- Space Complexity: O(1). Only a constant amount of extra space is used regardless of input size