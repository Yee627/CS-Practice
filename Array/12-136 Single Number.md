Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.

https://leetcode.com/problems/single-number/description/

java
```java
class Solution {
    public int singleNumber(int[] nums) {
        if (nums.length == 1) {
            return nums[0];
        }
        int res = 0;
        for (int x : nums) {
            res ^= x;
        }
        return res;
    }
}
```
c#
```csharp
public class Solution {
    public int SingleNumber(int[] nums) {
        if (nums.Length == 1) {
            return nums[0];
        }
        int res = 0;
        foreach (int x in nums) {
            res ^= x;
        }
        return res;
    }
}
```

-  uses the XOR (exclusive or) bitwise operation. By XORing all elements in the array, the elements that appear twice cancel out (become 0), and only the single element remains.
    - a ^ a = 0 (XOR of a number with itself is zero)
    - a ^ 0 = a (XOR of any number with zero returns the number)
    - a ^ b ^ a = b (XOR is commutative and associative)

e.g. [1,2,2,3,1]
the binary reprentation of '0' is '0000'\
the binary reprentation of '1' is '0001'\
the binary reprentation of '2' is '0010'\
the binary reprentation of '3' is '0011'

0 ^ 1 = 0001\
1 ^ 2 = 0011\
3 ^ 2 = 0001\
1 ^ 3 = 0010\
2 ^ 1 = 0011, which is 3, so the answer is 3

- Time Complexity: O(n) - perform a single pass through the array of n elements.
- Space Complexity: O(1) - only use a single variable (res) regardless of input size.

if there is no restriction for space complexity, could use the following hashset solution

java
```java
class Solution {
    public int singleNumber(int[] nums) {
        int result = 0;
        HashSet<Integer> set = new HashSet<>();

        for (int num : nums) {
            if (!set.contains(num)) {
                set.add(num);
                result += num;
            } else {
                result -= num;
            }
        }
        return result;
    }
}
```
- Time Complexity: O(n) 
- Space Complexity: O(n)
