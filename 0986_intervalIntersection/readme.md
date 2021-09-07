
## Solution 1 (CPP). Two pointers
```cpp
// Time: O(N)
// Space: O(1)
class Solution {
public:
    
    vector<vector<int>> intervalIntersection(
        vector<vector<int>>& A, vector<vector<int>>& B) {
        
        int m=A.size(), n=B.size(), i=0, j=0;
        
        vector<vector<int>> res;        
        while(i<m && j<n) {
            if(A[i][1]>=B[j][0] && B[j][1]>=A[i][0]) {
                int x=max(A[i][0], B[j][0]);
                int y=min(A[i][1], B[j][1]);
                
                res.push_back({x,y});
            }
                        
            if(A[i][1]<B[j][1]) ++i;
            else ++j;
        }
        
        return res;
    }
    
    
};
```
