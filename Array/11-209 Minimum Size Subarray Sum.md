Given an array of positive integers nums and a positive integer target, return the minimal length of a whose sum is greater than or equal to target. If there is no such subarray, return 0 instead.

https://leetcode.com/problems/minimum-size-subarray-sum/description/

java
```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int left = 0;
        int sum = 0;
        int result = Integer.MAX_VALUE;
        for (int right = 0; right < nums.length; right++) {
            sum += nums[right];
            while (sum >= target) {
                result = Math.min(result, right - left + 1);
                sum -= nums[left];
                left++;
            }
        }
        return result == Integer.MAX_VALUE ? 0 : result;
    }
}
```

c#
```csharp
public class Solution {
    public int MinSubArrayLen(int target, int[] nums) {
        int left = 0;
        int sum = 0;
        int result = int.MaxValue;
        for (int right = 0; right < nums.Length; right++) {
            sum += nums[right];
            while (sum >= target) {
                result = Math.Min(result, right - left + 1);
                sum -= nums[left];
                left++;
            }
        }
        return result == int.MaxValue ? 0 : result;
    }
}
```

- using the sliding window, which is an efficient way to solve problems involving subarrays or substrings. 
- Move the right pointer from start to end of the array. Add the current element to the running sum. While the sum is greater than or equal to the target, update the result with the minimum subarray length, remove the leftmost element from the sum and move the left pointer forward
- Time Complexity: O(n). Although there are nested loops, each element is added to the sum once and removed at most once. The right pointer moves n steps, and the left pointer moves at most n steps
- Space Complexity: O(1), only use a constant amount of extra space regardless of input size