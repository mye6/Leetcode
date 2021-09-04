
## Solution 1 (CPP). Union Find
```cpp
// Time: O(NlogN)
// Space: O(N)
class Solution {
public:
    
    unordered_map<string,string> parent;
    
    string find(string s) {
        return parent[s]=(parent[s]==s ? s : find(parent[s]));
    }
    
    void uni(string x, string y) {
        string px=find(x), py=find(y);
        if(px!=py) parent[px]=py;
    }
        
    vector<vector<string>> accountsMerge(vector<vector<string>>& A) {        
        int n=A.size();
        
        // initialize union find; record owner
        unordered_map<string, string> owner; // email->owner
        for(int i=0; i<n; ++i) {
            for(int j=1; j<A[i].size(); ++j) {
                string& e=A[i][j];
                string& o=A[i][0];
                owner[e]=o;
                parent[e]=e;                
            }            
        }
        
        // union find        
        for(int i=0; i<n; ++i) {
            for(int j=2; j<A[i].size(); ++j) {
                string& e0=A[i][1];
                string& e=A[i][j];                
                uni(e,e0);
            }
        }
        
        // group by parent
        unordered_map<string,set<string>> group; // parent->{emails}
        for(int i=0; i<n; ++i) {
            for(int j=1; j<A[i].size(); ++j) {
                string& e=A[i][j];
                string p=find(e);
                group[p].insert(e);
            }
        }
        
        // store result
        vector<vector<string>> res;
        for(auto& [p, es] : group) {
            vector<string> cur;
            cur.push_back(owner[p]);
            for(auto& e : es) {
                cur.push_back(e);
            }
            
            res.push_back(cur);
        }
        
        return res;        
    }  
};
```
