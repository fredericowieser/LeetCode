# My Solution V1
```cpp
#include <string>

class Solution {
public:
    bool isPalindrome(int x) {
        const std::string s = std::to_string(x);
        const int l = s.size();
        for(int i = 0; i < l; i++) {
            if(s[i] != s[l - (i+1)]) {
                return 0;
            }
        }
        return 1;
    }
};
```

Runtime: 3 ms, faster than 93.47% of C++ online submissions for Palindrome Number.
Memory Usage: 9.1 MB, less than 20.54% of C++ online submissions for Palindrome Number.

## Improvements
- One way to improve would be to reduce the number of iterations my for loop does as after the half way point we are doing compute which has already been done in the previous loops.

# Other Solutions
**Solution I:**  
Convert the number to a string, revert it and compare.

```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        string rev = to_string(x);
        reverse(rev.begin(), rev.end());
        return to_string(x) == rev;
    }
};
```

**Solution II:**  
Convert the number to a string, then use two pointers at beginning and end to check if it's a palindrome.

```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        string s = to_string(x);
        int i = 0, j = s.size()-1;
        while (i <= j) if (s[i++] != s[j--]) return false;
        return true;
    }
};
```

**Solution III:**  
Reverse the second half of the number and then compare.

```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0 || (x % 10 == 0 && x != 0)) return false;
        int rev = 0;
        while (rev < x) {
            rev = rev * 10 + x % 10;
            x /= 10;
        }
        
        return x == rev || x == rev / 10;
    }
};
```