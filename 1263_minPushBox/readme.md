
## Solution 1 (CPP). BFS
```cpp
// Time: O(N^4)
// Space: O(N^4)
class Solution {
public:
    
    struct Node {
        int bx, by, px, py;    
    };
    
    vector<vector<int>> dirs{{-1,0},{0,-1},{0,1},{1,0}};
    
    int minPushBox(vector<vector<char>>& g) {
        int m=g.size(), n=g[0].size();
        int bx, by, px, py, tx, ty;
        
        // 1. identify bx, by, px, py, tx, ty
        for(int i=0; i<m; ++i) {
            for(int j=0; j<n; ++j) {
                if(g[i][j]=='S') {
                    px=i; py=j;
                    g[i][j]='.';
                }
                else if(g[i][j]=='B') {
                    bx=i; by=j;
                    g[i][j]='.';
                }
                else if(g[i][j]=='T') {
                    tx=i; ty=j;
                    g[i][j]='.';
                }
            }
        }
        
        // 2. bfs to find the minimum
        int dp[21][21][21][21]; // (bx,by,px,py)
        memset(dp,-1,sizeof(dp));
        dp[bx][by][px][py]=0;
        
        deque<Node> dq;
        dq.push_back({bx,by,px,py});
        
        while(!dq.empty()) {
            auto [bx,by,px,py]=dq.front(); dq.pop_front();
            
            if(bx==tx && by==ty)
                return dp[bx][by][px][py];
            
            for(auto& dir : dirs) {
                int px2=px+dir[0], py2=py+dir[1];
                
                if(px2<0||px2>=m||py2<0||py2>=n) continue;
                if(g[px2][py2]!='.') continue;
                if(px2==bx&&py2==by) continue;
                if(dp[bx][by][px2][py2]>=0) continue;
                
                dp[bx][by][px2][py2]=dp[bx][by][px][py];
                dq.push_front({bx,by,px2,py2});
            }
            
            if(abs(px-bx)+abs(py-by)==1) {
                for(auto& dir : dirs) {
                    if(px+dir[0]==bx && py+dir[1]==by) {
                        int bx2=bx+dir[0], by2=by+dir[1];
                        
                        if(bx2<0||bx2>=m||by2<0||by2>=n) continue;
                        if(g[bx2][by2]!='.') continue;
                        if(dp[bx2][by2][bx][by]>=0) continue;
                        
                        dp[bx2][by2][bx][by]=dp[bx][by][px][py]+1;
                        dq.push_back({bx2,by2,bx,by});
                    }
                }
            }
            
        }
        
        return -1;
    }
    
    
};
```
