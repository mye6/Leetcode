
## Solution 1 (CPP).
```cpp
// Time: O(MN)
// Space: O(1)

class Solution {
public:
    
    int m, n;
    
    void dfs(vector<vector<char>>& g, int i, int j) {
        if(i<0 || i>=m || j<0 || j>=n || g[i][j]=='0') return;
        
        g[i][j]='0';
        dfs(g,i+1,j);
        dfs(g,i-1,j);
        dfs(g,i,j-1);
        dfs(g,i,j+1);
    }
    
    int numIslands(vector<vector<char>>& g) {
        m=g.size(); n=g[0].size();
        
        int res=0;
        for(int i=0; i<m; ++i) {
            for(int j=0; j<n; ++j) {
                if(g[i][j]=='1') {
                    ++res;
                    dfs(g,i,j);    
                }
            }
        }
        
        return res;
    }
    
};
```
