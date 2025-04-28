Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.

You must solve this problem without using the library's sort function.

https://leetcode.com/problems/sort-colors/description/

java
```java
class Solution {
    public void sortColors(int[] nums) {
        int left = 0, right = nums.length - 1;
        int index = 0;
        while (index <= right) {
            if (nums[index] == 0) {
                swap(nums, left, index);
                left++;
                index++;
            } else if (nums[index] == 2) {
                swap(nums, right, index);
                right--;
            } else {
                index++;
            }
        }
    }
     private void swap(int[]nums, int left, int right) {
        int temp = nums[left];
        nums[left] = nums[right];
        nums[right] = temp;
     }
}
```
c#
```csharp
public class Solution {
    public void SortColors(int[] nums) {
        int left = 0, right = nums.Length - 1;
        int index = 0;
        
        while (index <= right) {
            if (nums[index] == 0) {
                Swap(nums, left, index);
                left++;
                index++;
            } else if (nums[index] == 2) {
                Swap(nums, right, index);
                right--;
            } else {
                index++;
            }
        }
    }
    
    private void Swap(int[] nums, int left, int right) {
        int temp = nums[left];
        nums[left] = nums[right];
        nums[right] = temp;
    }
}
```

- this used Dutch National Flag algorithm, designed by Edsger W. Dijkstra. It's a one-pass algorithm that sorts an array containing only three distinct values.
- Maintain three pointers: left, right, and index. As index traverses the array: If nums[index] is 0, swap it with nums[left] and increment both left and index. If nums[index] is 2, swap it with nums[right] and decrement right. Don't increment index as the swapped value needs to be checked. If nums[index] is 1, just increment index.
- Time Complexity: O(n) where n is the length of the array. The algorithm traverses the array only once.
- Space Complexity: O(1) as it sorts the array in-place without using any extra space except for a few variables.