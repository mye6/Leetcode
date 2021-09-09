
## Solution 1 (CPP). 2D Presum
```cpp
// Time: O(MN)
// Space: O(MN)

class NumMatrix {
public:
    
    int m, n;
    
    vector<vector<int>> dp;
    
    NumMatrix(vector<vector<int>>& A) {
        m=A.size(); n=A[0].size();
        dp=vector<vector<int>>(m+1,vector<int>(n+1,0));
        
        for(int i=1; i<=m; ++i) {
            for(int j=1; j<=n; ++j) {
                dp[i][j]=dp[i-1][j]+dp[i][j-1]-dp[i-1][j-1]+A[i-1][j-1];
            }            
        }        
    }
    
    int sumRegion(int x1, int y1, int x2, int y2) {
        return dp[x2+1][y2+1]-dp[x1][y2+1]-dp[x2+1][y1]+dp[x1][y1];
    }
    
};
```
