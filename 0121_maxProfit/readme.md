
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(1)

class Solution {
public:
    
    int maxProfit(vector<int>& A) {
        int n=A.size();
        if(n<=1) return 0;
        
        int mn=A[0], res=0;
        for(int i=1; i<n; ++i) {
            res=max(res, A[i]-mn);
            mn=min(mn,A[i]);
        }
        
        return res;
    }
  
};
```
