
## Solution 1 (CPP). Two Pointers
```cpp
// Time: O(N)
// Space: O(1)
class Solution {
public:
    
    bool validWordAbbreviation(string w, string a) {
        int m=w.size(), n=a.size(), i=0, j=0;
        
        while(i<m && j<n) {            
            if(isdigit(a[j])) {                
                if(a[j]=='0') return false;
                                
                int v=0;
                while(j<n && isdigit(a[j]))
                    v=v*10+a[j++]-'0';
                
                i+=v;
            }
            else {             
                if(w[i]==a[j]) {
                    ++i; ++j;
                }                
                else {
                    return false;
                }
            }
        }
    
        return i==m && j==n;
    }    
    
};
```
