
## Solution 1 (CPP).
```cpp
// Time: O(NlogN)
// Space: O(
class Solution {
public:
    
    
    vector<vector<int>> merge(vector<vector<int>>& A) {
        int n=A.size();
        if(n<=1) return A;
        
        sort(A.begin(),A.end());
        vector<vector<int>> res;
        
        int x=A[0][0], y=A[0][1];
        for(int i=1; i<n; ++i) {
            if(A[i][0]<=y) {  // overlap; xi<=y
                y=max(y,A[i][1]);
            }
            else {            // non-overlap; xi>y
                res.push_back({x,y});
                x=A[i][0]; y=A[i][1];
            }
        }
        
        res.push_back({x,y});
        return res;
    }
    
    
};
```
