Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.

https://leetcode.com/problems/remove-element/description/

java
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        int slowIndex = 0;
        
        for (int fastIndex = 0; fastIndex < nums.length; fastIndex++) {
            if (nums[fastIndex] != val) {
                nums[slowIndex] = nums[fastIndex];
                slowIndex++;
            }
        }
        return slowIndex;
    }
}
```

```csharp
public class Solution {
    public int RemoveElement(int[] nums, int val) {
        if (nums == null || nums.Length == 0) {
            return 0;
        }
        
        int slowIndex = 0;
        for (int fastIndex = 0; fastIndex < nums.Length; fastIndex++) {
            if (nums[fastIndex] != val) {
                nums[slowIndex] = nums[fastIndex];
                slowIndex++;
            }
        }
        
        return slowIndex;
    }
}
```

- implementws the "two-pointer" technique. slowIndex keeps track of the position where non-matching elements should be placed, fastIndex scans through the entire array looking for non-matching elements. When a non-matching element is found, it's copied to the position indicated by slowIndex
- Time Complexity: O(n), where n is the length of the array. 
- Space Complexity: O(1), as it uses only a constant amount of extra space regardless of input size (just the two index variables).