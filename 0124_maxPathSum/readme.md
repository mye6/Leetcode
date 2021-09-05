
## Solution 1 (CPP). DFS
```cpp
// Time: O(N)
// Space: O(H)
class Solution {
public:

    int res=INT_MIN;
    
    int pathSum(TreeNode* root) {
        if(!root) return 0;
        
        int l=pathSum(root->left);
        int r=pathSum(root->right);
        
        if(l<0) l=0;
        if(r<0) r=0;
        
        res=max(res,root->val+l+r);
        
        return max(l,r)+root->val;        
    }
    
    int maxPathSum(TreeNode* root) {
        if(!root) return 0;        
        
        pathSum(root);
        return res;
    }
    
};
```
