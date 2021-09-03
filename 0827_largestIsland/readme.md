
## Solution 1 (CPP). DFS
```cpp
// Time: O(M*N)
// Space: O(M*N)
class Solution {
public:
    
    int m, n, k=2;
    unordered_map<int,int> area; // label->area
    
    bool valid(int i, int j) {
        return 0<=i && i<m && 0<=j && j<n;
    }
    
    vector<vector<int>> dirs{{-1,0},{0,-1},{0,1},{1,0}};
    
    void dfs(vector<vector<int>>& g, int i, int j) {
        if(!valid(i,j) || g[i][j]!=1) return;
        
        g[i][j]=k;
        ++area[k];
        
        for(auto& dir : dirs) {
            int ni=i+dir[0], nj=j+dir[1];
            dfs(g,ni,nj);
        }
    }
    
    int largestIsland(vector<vector<int>>& g) {
        m=g.size(); n=g[0].size();    
        
        int res=0;
        for(int i=0; i<m; ++i) {
            for(int j=0; j<n; ++j) {
                dfs(g,i,j);
                res=max(res,area[k]);
                ++k;
            }
        }
        
        queue<pair<int,int>> q;
        for(int i=0; i<m; ++i) {
            for(int j=0; j<n; ++j) {
                if(g[i][j]==0) q.push({i,j});
            }
        }
        
        while(!q.empty()) {
            auto [x,y]=q.front(); q.pop();
            
            unordered_set<int> seen; // check label already visited
            
            int sum=0;
            for(auto& dir : dirs) {
                int nx=x+dir[0], ny=y+dir[1];
                if(!valid(nx,ny) || g[nx][ny]==0) continue;
                
                int label=g[nx][ny];
                if(seen.count(label)) continue;
                seen.insert(label);
                sum+=area[label];
            }
            
            res=max(res,sum+1);
        }
     
        return res;
    }
    
    
};
```