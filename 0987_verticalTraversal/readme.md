
## Solution 1 (CPP). DFS
```cpp
// Time: O(NlogN)
// Space: O(N)
class Solution {
public:
    
    map<int,map<int,multiset<int>>> mp; // col->row->ms
    
    void dfs(TreeNode* root, int col, int row) {
        if(!root) return;
        
        mp[col][row].insert(root->val);
        dfs(root->left,col-1,row+1);
        dfs(root->right,col+1,row+1);
    }
    
    vector<vector<int>> verticalTraversal(TreeNode* root) {
        dfs(root,0,0);
        
        vector<vector<int>> res;
        
        for(auto& kv : mp) { // per col
            vector<int> cur;
            
            for(auto& kv2 : kv.second) {
                cur.insert(cur.end(), kv2.second.begin(), kv2.second.end());
            }
            
            res.push_back(cur);
        }
            
        return res;
    }
      
};
```
