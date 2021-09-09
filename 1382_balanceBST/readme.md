
## Solution 1 (CPP). Inorder + Recursion
```cpp
// Time: O(N)
// Space: O(N)
class Solution {
public:
    
    void inorder(TreeNode* root, vector<int>& res) {
        if(!root) return;
        
        inorder(root->left, res);
        res.push_back(root->val);
        inorder(root->right, res);        
    }
    
    TreeNode* buildTree(vector<int>& res, int l, int r) {
        if(l>r) return nullptr;
        
        int mid=l+(r-l)/2;
        TreeNode* root= new TreeNode(res[mid]);
        
        root->left = buildTree(res,l,mid-1);
        root->right = buildTree(res,mid+1,r);
        return root;
    }    
    
    TreeNode* balanceBST(TreeNode* root) {
        vector<int> res;
        inorder(root, res);
        
        return buildTree(res,0,res.size()-1);
    }
      
};
```
