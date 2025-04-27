Given an integer array nums, rotate the array to the right by k steps, where k is non-negative.

https://leetcode.com/problems/rotate-array/description/

java
```java
class Solution {
    public void rotate(int[] nums, int k) {
        int newStart = k % nums.length;
        swap(nums, 0, nums.length - 1);
        swap(nums, 0, newStart - 1);
        swap(nums, newStart, nums.length - 1);
    }

    public void swap(int[] nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }
}
```

c#
```csharp
public class Solution {
    public void Rotate(int[] nums, int k) {
        int newStart = k % nums.Length;
        Swap(nums, 0, nums.Length - 1);
        Swap(nums, 0, newStart - 1);
        Swap(nums, newStart, nums.Length - 1);
    }
    
    private void Swap(int[] nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }
}
```

-  use the actual rotation needed with k % nums.length to handle cases where k is larger than the array size. the modulo operation can usually be used to deal with circular structures, periodic events, or any scenario where calculations need to "wrap around" after reaching a certain limit.环形结构：当数据被组织成一个环或循环时，比如环形缓冲区、循环队列或像我们刚才讨论的数组旋转问题。周期性事件：处理重复出现的事件或模式，如时钟算法、调度算法等。需要"循环回绕"的计算：任何时候当一个值增长到某个上限后需要回到起点继续计算的情况。例如，时钟的小时从12后回到1，星期几从周日到周六再回到周日，或者在游戏中的角色移动到屏幕一边后从另一边出现。这种模运算（取余）操作使能够在达到某个限制值后优雅地处理"回绕"或"循环"的情况，而不必使用复杂的条件判断。

- use three targeted reversals: Reverse the entire array, Reverse the first portion (from index 0 to newStart-1), Reverse the second portion (from newStart to the end)
- Time Complexity: O(n), where n is the length of the array. Each element is touched a constant number of times. 
- Space Complexity: O(1), using only a constant amount of extra space regardless of input size.