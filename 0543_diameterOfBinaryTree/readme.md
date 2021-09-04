
## Solution 1 (CPP). DFS
```cpp
// Time: O(N)
// Space: O(N)

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */

class Solution {
public:
    
    int res=0;
    
    int maxDepth(TreeNode* root) {
        if(!root) return 0;
        
        int l=maxDepth(root->left);
        int r=maxDepth(root->right);
        
        res=max(res,l+r);
        
        return max(l,r)+1;
    }
    
    
    int diameterOfBinaryTree(TreeNode* root) {
        maxDepth(root);
        
        return res;
    }
};
```
