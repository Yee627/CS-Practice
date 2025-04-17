Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description/

java
```java
class Solution {
    public void moveZeroes(int[] nums) {
        int slowIndex = 0;
        for (int fastIndex = 0; fastIndex < nums.length; fastIndex++) {
            if (nums[fastIndex] != 0) {
                switchItem(nums, slowIndex, fastIndex);
                slowIndex++;
            }
        }
    }

    public void switchItem(int[] nums, int item1, int item2) {
        int temp = nums[item1];
        nums[item1] = nums[item2];
        nums[item2] = temp;
    }
}
```
c#
```csharp
public class Solution {
    public void MoveZeroes(int[] nums) {
        int slowIndex = 0;
        for (int fastIndex = 0; fastIndex < nums.Length; fastIndex++) {
            if (nums[fastIndex] != 0) {
                SwitchItem(nums, slowIndex, fastIndex);
                slowIndex++;
            }
        }
    }
    
    public void SwitchItem(int[] nums, int item1, int item2) {
        int temp = nums[item1];
        nums[item1] = nums[item2];
        nums[item2] = temp;
    }
}
```

- The slowIndex points to the position where the next non-zero element should be placed. The fastIndex scans through the array to find non-zero elements. When a non-zero element is found, it's swapped with the element at the slowIndex position
- Time Complexity: O(n), where n is the length of the array
- Space Complexity: O(1). The algorithm uses a constant amount of extra space regardless of input size