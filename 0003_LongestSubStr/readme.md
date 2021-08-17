
## Solution 1 (CPP).
Use a hash map to track the mapping from number to index.
```cpp
// Time: O(N)
// Space: O(C) where C is the range of character set
class Solution {
public:
    
    int lengthOfLongestSubstring(string s) {
        int n=s.size();
        
        vector<int> last(256,-1);
        
        int left=-1, res=0;
        for(int i=0; i<n; ++i) {
            left=max(left, last[s[i]]);
            res=max(res,i-left);
            
            last[s[i]]=i;
        }
        
        return res;
    }  
};
```


## Solution 1 (PYTHON).
Use a hash map to track the mapping from number to index.
```python
# Time: O(N)
# Space: O(N)
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        mp, res, l = {}, 0, 0
        for i, c in enumerate(s):
            if c in mp:
                l = max(l, mp[c]+1)
            
            res=max(res,i-l+1)
            mp[c]=i
            
        return res
```
