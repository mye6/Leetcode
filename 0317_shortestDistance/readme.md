
## Solution 1 (CPP).
```cpp
// Time: O(#Building*MN)
// Space: O(MN)
class Solution {
public:
    
    vector<vector<int>> dirs{{-1,0},{0,-1},{1,0},{0,1}};
    
    int shortestDistance(vector<vector<int>>& g) {
        int m=g.size(), n=g[0].size();
        
        vector<vector<int>> dist(m,vector<int>(n,0)); // store the total dist
        
        int T=0, res=INT_MAX;
        
        for(int i=0; i<m; ++i) {
            for(int j=0; j<n; ++j) {
                if(g[i][j]!=1) continue;
                
                res=INT_MAX;
                queue<pair<int,int>> q; q.push({i,j});
                
                int steps=1;
                while(!q.empty()) {
                    int len=q.size();
                    
                    while(len--) {
                        auto [x, y]=q.front(); q.pop();                       
                        
                        for(auto& dir : dirs) {
                            int nx=x+dir[0], ny=y+dir[1];
                            
                            if(nx<0 || nx>=m || ny<0 || ny>=n) continue;
                            if(g[nx][ny]!=T) continue;
                            
                            q.push({nx,ny});
                            --g[nx][ny];
                            dist[nx][ny]+=steps;
                            
                            res=min(res,dist[nx][ny]);
                        }                        
                    }
                    
                    ++steps;
                }
                
                if(res==INT_MAX) return -1;
                --T;
            }            
        }
        
        if(res==INT_MAX) return -1;
        return res;
    }
      
};
```
