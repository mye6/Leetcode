
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(1)
class Solution {
public:
    
    int minAddToMakeValid(string s) {
        int n=s.size();
        
        int l=0, m=0; // l: #opened; m: #completed
        
        for(char c : s) {
            if(c=='(') ++l;
            else {
                if(l>0) {
                    --l; ++m;
                }                
            }
        }
        
        return n-2*m;
    }
    
};
```
