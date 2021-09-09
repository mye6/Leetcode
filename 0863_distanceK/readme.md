
## Solution 1 (CPP). DFS + BFS
```cpp
// Time: O(N)
// Space: O(N)

class Solution {
public:
    
    unordered_map<TreeNode*, vector<TreeNode*>> g;
    
    void buildGraph(TreeNode* node, TreeNode* parent) {
        if(!node) return;
        
        if(parent) {
            g[node].push_back(parent);
            g[parent].push_back(node);
        }
        
        if(node->left) buildGraph(node->left, node);
        if(node->right) buildGraph(node->right, node);
    }    
    
    vector<int> distanceK(TreeNode* root, TreeNode* target, int k) {
        buildGraph(root, nullptr);
        
        vector<int> res;
        queue<TreeNode*> q; q.push(target);
        unordered_set<TreeNode*> seen; seen.insert(target);
        
        while(!q.empty() && k>=0) {
            int len=q.size();
            
            while(len--) {
                TreeNode* cur=q.front(); q.pop();
                seen.insert(cur);
                if(k==0) res.push_back(cur->val);
                for(TreeNode* nxt : g[cur]) {
                    if(nxt && !seen.count(nxt))
                        q.push(nxt);
                }                
            }
            
            --k;
        }
        
        return res;
    }
    
};
```
