
## Solution 1 (CPP). DFS
```cpp
// Time: O(NlogN)
// Space: O(N)
class Solution {
public:
    
    map<int,map<int,vector<int>>> mp;
    
    void visit(TreeNode* root, int col, int row) {
        if(!root) return;
        mp[col][row].push_back(root->val);
        visit(root->left,col-1,row+1);
        visit(root->right,col+1,row+1);
    }
    
    vector<vector<int>> verticalOrder(TreeNode* root) {
        vector<vector<int>> res;
        if(!root) return res;
        visit(root,0,0);
        
        for(auto& p : mp) {
            vector<int> cols;
            for(auto& q : p.second) {
                cols.insert(cols.end(), q.second.begin(), q.second.end());
            }
            
            res.push_back(cols);
        }
        
        return res;
    }
    
    
};
```