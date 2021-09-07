
## Solution 1 (CPP). Topological sort
```cpp
// Time: O(N)
// Space: O(N)
class Solution {
public:
    
    string alienOrder(vector<string>& words) {
        unordered_map<char,vector<char>> g;
        unordered_map<char,int> in;
        
        // 1. iterate all words
        int n=words.size();
        for(int i=0; i<n; ++i) {
            // 1a. obtain the in degrees of all chars
            string& a=words[i];            
            for(char c : a) {
                if(!in.count(c)) in[c]=0;
            }
            
            // 1b. built the adj list
            if(i==n-1) break;
            string& b=words[i+1];
            
            int j=0, mn=min(a.size(),b.size());
            for( ; j<mn; ++j) {
                if(a[j]!=b[j]) {
                    g[a[j]].push_back(b[j]);
                    ++in[b[j]];
                    break;
                }
            }
            if(j==mn && a.size()>b.size()) return "";
        }
        
        // 2. topo sort
        queue<char> q;
        for(auto& [c, cnt] : in) {
            if(in[c]==0) q.push(c);
        }
        
        string res;
        while(!q.empty()) {
            char u=q.front(); q.pop();
            res+=u;
            
            for(char v : g[u]) {
                if(--in[v]==0) q.push(v);
            }
        }
        
        if(res.size()!=in.size()) return "";
        return res;
    }
      
};
```
