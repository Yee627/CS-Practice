Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well.

You must not use any built-in exponent function or operator.

java
```java
class Solution  {
    public int mySqrt(int x) {
        long left = 1;
        long right = x;
        while (left <= right) {
            long mid = left + (right - left) / 2;
            if (mid * mid == x) {
                return (int)mid;
            } else if (mid * mid < x) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return (int)right;
    }
}
```

c#
```csharp
public class Solution {
    public int MySqrt(int x) {
        long left = 1;
        long right = x;
        
        while (left <= right) {
            long mid = left + (right - left) / 2;
            
            if (mid * mid == x) {
                return (int)mid;
            } else if (mid * mid < x) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        
        return (int)right;
    }
}
```

- When the binary search terminates (after left > right), the variable right will hold the integer value that is the floor of the square root of x, thus need to return right.
- Time Complexity: O(log n), binary search halves the search space in each iteration
- Space Complexity: O(1), only using a constant amount of extra space regardless of input size
