Given two strings s and t, return true if they are equal when both are typed into empty text editors. '#' means a backspace character.

Note that after backspacing an empty text, the text will continue empty.

https://leetcode.com/problems/backspace-string-compare/description/

java
```java
class Solution {
    public boolean backspaceCompare(String s, String t) {
       int i = s.length() - 1, j = t.length() - 1;
       int skipS = 0, skipT = 0;
       while (i >= 0 || j >= 0) {
            while (i >= 0) {
                if (s.charAt(i) == '#') {
                    skipS++;
                    i--;
                } else if (skipS > 0) {
                    skipS--;
                    i--;
                } else break;
            }

            while (j >= 0) {
                if (t.charAt(j) == '#') {
                    skipT++;
                    j--;
                } else if (skipT > 0) {
                    skipT--;
                    j--;
                } else break;
            }

            if (i >= 0 && j >= 0 && s.charAt(i) != t.charAt(j)) {
                return false;
            }

            if ((i >= 0 && j < 0) || (j >= 0 && i < 0)) {
                return false;
            }

            i--;
            j--;
       }
       return true;
    }
}
```

c#
```csharp
public class Solution {
    public bool BackspaceCompare(string s, string t) {
        int i = s.Length - 1, j = t.Length - 1;
        int skipS = 0, skipT = 0;
        
        while (i >= 0 || j >= 0) {
            while (i >= 0) {
                if (s[i] == '#') {
                    skipS++;
                    i--;
                } else if (skipS > 0) {
                    skipS--;
                    i--;
                } else break;
            }

            while (j >= 0) {
                if (t[j] == '#') {
                    skipT++;
                    j--;
                } else if (skipT > 0) {
                    skipT--;
                    j--;
                } else break;
            }

            if (i >= 0 && j >= 0 && s[i] != t[j]) {
                return false;
            }

            if ((i >= 0 && j < 0) || (j >= 0 && i < 0)) {
                return false;
            }

            i--;
            j--;
        }
        
        return true;
    }
}
```
-  the two-pointer approach with an in-place comparison working backward from the end of both strings, because if it begins comparison from the begining, its hard to count the amount of #.
- uses two pointers i and j starting from the end of each string.
-  maintains two counters skipS and skipT to track how many characters # to skip due to backspaces
- processes both strings character by character, applying backspaces appropriately
- compares the "final" characters after backspaces are applied
- Time Complexity: O(n + m) where n and m are the lengths of strings s and t respectively.It iterate through each character at most once
- Space Complexity*: O(1) with only using a constant amount of extra space regardless of input size


