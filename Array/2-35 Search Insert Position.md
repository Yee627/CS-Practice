Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

https://leetcode.com/problems/search-insert-position/description/

java
```java
public int searchInsert(int[] nums, int target) {
    int left = 0;
    int right = nums.length;
    while (left < right){
        int mid = left + ((right - left) >> 1);
        if (nums[mid] > target){
            right = mid;
        } else if (nums[mid] < target){
            left = mid + 1;
        } else {
            return mid;
        }
    }
    return right;
}
```

c#
```csharp
public int SearchInsert(int[] nums, int target) {
    int left = 0;
    int right = nums.Length;
    while (left < right) {
        int mid = left + ((right - left) >> 1);
        if (nums[mid] > target) {
            right = mid;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else {
            return mid;
        }
    }
    return right;
}
```

using a half-open interval pattern [left, right)
loop condition is while (left < right)
my updates are either right = mid or left = mid + 1

This design guarantees that:

The search space reduces by at least one element in each iteration
When the loop exits, left will always equal right