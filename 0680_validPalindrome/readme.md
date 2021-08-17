
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(1)
class Solution {
public:
    bool isValid(string& s, int l, int r) {
        while(l<r) {
            if(s[l++]!=s[r--]) return false;
        }
        return true;
    }
    
    bool validPalindrome(string s) {
        for(int i=0, j=s.size()-1; i<j; ++i, --j) {
            if(s[i]!=s[j]) {
                return isValid(s,i+1,j) || isValid(s,i,j-1);
            }
        }
        
        return true;
    }
};
```

## Solution 1 (Python).
```python
# Time: O(N)
# Space: O(1)
class Solution:
    def valid(self, s : str, l : int, r: int) -> bool:
        while l < r:
            if s[l] == s[r]:
                l += 1
                r -= 1
            else:
                return False
        
        return True
    
    def validPalindrome(self, s: str) -> bool:
        l, r = 0, len(s)-1
        
        while l < r:
            if s[l] == s[r]:
                l += 1
                r -= 1
            else:
                return self.valid(s,l+1,r) or self.valid(s,l,r-1)
            
        return True
```