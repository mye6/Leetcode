
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(1)
class Solution {
public:
    
    
    string addStrings(string s1, string s2) {
        int i=s1.size()-1, j=s2.size()-1, c=0;
        
        string res;
        
        while(i>=0 || j>=0 || c>0) {
            c+=(i>=0 ? s1[i--]-'0' : 0);
            c+=(j>=0 ? s2[j--]-'0' : 0);
            res=char('0'+c%10)+res;
            c/=10;
        }
        
        return res;
    }
    
};
```
