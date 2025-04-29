Given a sorted integer array <strong><em>nums</em></strong>, where the range of elements are in the <strong>inclusive range</strong><b><strong> </strong>[<i>lower</i>, <i>upper</i>]</b>, return its missing ranges.

<strong>Example:</strong>

<pre>
<strong>Input:</strong> <strong><em>nums</em></strong> = <code>[0, 1, 3, 50, 75]</code>, <strong><i>lower</i></strong> = 0 and <strong><i>upper</i></strong> = 99,
<strong>Output:</strong> <code>[&quot;2&quot;, &quot;4-&gt;49&quot;, &quot;51-&gt;74&quot;, &quot;76-&gt;99&quot;]</code>
</pre>

https://leetcode.com/problems/missing-ranges/description/

java
```java
public List<string> findRanges(int[] nums, int lower, int upper) {
    List<string> result = new ArrayList<string>();
    int next = lower;
    for (int i = 0; i < nums.length; i++) {
        if (lower == Integer.MAX_VALUE) {
            return result;
        } 

        if (nums[i] < next) continue;

        if (nums[i] == next) {
            next++;
            continue;
        }

        result.add(getRange(next, nums[i] - 1));   
        if (num[i] == Intger.MAX_VALUE) {
            return result;
        }
        next = nums[i] + 1;
     }

    if (next <= upper) {
        result.add(getRange(next, upper));
    }
    return result;
}

public string getRange(int num1, int num2) {
    return (num1 == num2) ? String.valueOf(num1) : String.format("%d->%d", num1, num2);
}
```

c#
```csharp
public IList<string> FindRanges(int[] nums, int lower, int upper) {
    var result = new List<string>();
    var next = lower;
    
    for (int i = 0; i < nums.Length; i++) {
        if (lower == int.MaxValue) {
            return result;
        }
        
        if (nums[i] < next) continue;
        
        if (nums[i] == next) {
            next++;
            continue;
        }
        
        result.Add(GetRange(next, nums[i] - 1));
        
        if (nums[i] == int.MaxValue) {
            return result;
        }
        
        next = nums[i] + 1;
    }
    
    if (next <= upper) {
        result.Add(GetRange(next, upper));
    }
    
    return result;
}

public string GetRange(int num1, int num2) {
    return (num1 == num2) ? num1.ToString() : $"{num1}->{num2}";
}
```

- Start with the lower bound and track the "next expected number". When a gap is found between the expected number and current array element, create a range. Update the next expected number after processing each element. Handle the case where there might be missing numbers after the array ends
- The condition if (nums[i] < next) continue; handles cases when the input array contains duplicate elements
- This condition nums[i] == int.MaxValue handles a specific edge case related to integer overflow. When nums[i] is int.MaxValue (2,147,483,647 in C# and Java), adding 1 to it would cause an integer overflow. 
- Time Complexity: O(n) where n is the length of the input array. We're doing a single pass through the array.
- Space Complexity: O(k) where k is the number of missing ranges. In the worst case, k could be O(n) if there are many gaps.