
## Solution 1 (CPP).
```cpp
// Time: O(MN)
// Space: O(1)

class Solution {
public:
    
    bool isToeplitzMatrix(vector<vector<int>>& A) {
        int m=A.size(), n=A[0].size();
        
        for(int i=1; i<m; ++i) {
            for(int j=1; j<n; ++j) {
                if(A[i][j]!=A[i-1][j-1])
                    return false;
            }            
        }
        
        return true;
    }
    
};
```
