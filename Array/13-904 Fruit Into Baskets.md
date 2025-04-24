You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array fruits where fruits[i] is the type of fruit the ith tree produces.

You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:

    You only have two baskets, and each basket can only hold a single type of fruit. There is no limit on the amount of fruit each basket can hold.
    Starting from any tree of your choice, you must pick exactly one fruit from every tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.
    Once you reach a tree with fruit that cannot fit in your baskets, you must stop.

Given the integer array fruits, return the maximum number of fruits you can pick.

https://leetcode.com/problems/fruit-into-baskets/description/

java
```java
class Solution {
    public int totalFruit(int[] fruits) {
        int result = 0;
        Map<Integer, Integer> map = new HashMap<>();
        int left = 0;
        for (int right = 0; right < fruits.length; right++) {
            map.put(fruits[right], map.getOrDefault(fruits[right], 0) + 1);
            while (map.size() > 2) {
                if (map.get(fruits[left]) == 1) {
                    map.remove(fruits[left]); 
                } else {
                    map.put(fruits[left], map.get(fruits[left]) - 1);
                }
                left++;
            }
            result = Math.max(result, right - left + 1);
        }
        return result;
    }
}
```

c#
```csharp
public class Solution {
    public int TotalFruit(int[] fruits) {
        int result = 0;
        Dictionary<int, int> map = new Dictionary<int, int>();
        int left = 0;
        
        for (int right = 0; right < fruits.Length; right++) {
            if (map.ContainsKey(fruits[right])) {
                map[fruits[right]]++;
            } else {
                map[fruits[right]] = 1;
            }
            
            while (map.Count > 2) {
                if (map[fruits[left]] == 1) {
                    map.Remove(fruits[left]);
                } else {
                    map[fruits[left]]--;
                }
                left++;
            }
            
            result = Math.Max(result, right - left + 1);
        }
        
        return result;
    }
}
```

- using the sliding window technique with a HashMap/Dictionary to track fruit types
- fruits[i] means the type of tree, not the amount of trees, eg [1,2,2,4] here fruits[0] is type 1, fruits[1] is type 2, fruits[3] is type 4, dont get confused to see it as integer, it's just the type
- the sliding window defined by left and right pointers,the HashMap/Dictionary tracks the count of each fruit type in the current window. When having more than 2 fruit types, shrink the window from the left, then rack the maximum valid window size 
- Time Complexity: O(n),  process each element at most twice (once when adding to the window, once when removing)
- Space Complexity: O(1). The HashMap/Dictionary will never have more than 3 entries due to our constraint