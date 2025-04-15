Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in nums.

https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        int slowIndex = 0;
        for (int fastIndex = 1; fastIndex < nums.length; fastIndex++) {
            if (nums[fastIndex] != nums[slowIndex]) {
                nums[slowIndex + 1] = nums[fastIndex];
                slowIndex++;
            }
        }
        return slowIndex + 1;
    }
}
```

```csharp
public class Solution {
    public int RemoveDuplicates(int[] nums) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        int slowIndex = 0;
        for (int fastIndex = 1; fastIndex < nums.Length; fastIndex++) {
            if (nums[fastIndex] != nums[slowIndex]) {
                nums[slowIndex + 1] = nums[fastIndex];
                slowIndex++;
            }
        }
        return slowIndex + 1;
    }
}
```

- uses the two-pointer technique. slowIndex points to the current position where a new unique element should be placed. fastIndex scans through the array looking for unique elements. When a new unique element is found, it's copied to the position after slowIndex.
- Time Complexity: O(n) where n is the length of the array, as scaning through the array exactly once. Space Complexity: O(1) as modifying the array in-place with only a constant amount of extra memory regardless of input size.
- C#: nums.Distinct().ToArray() (LINQ)
- Java: Arrays.stream(nums).distinct().toArray()