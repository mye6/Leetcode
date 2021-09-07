
## Solution 1 (CPP).
```cpp
// Time: O(H)
// Space: O(1)
class Solution {
public:
    
    int closestValue(TreeNode* root, double T) {
        int res=root->val;
        
        while(root) {
            if(fabs(T - root->val) < fabs(T - res)) res=root->val;
            
            if(T < root->val) root=root->left;
            else root=root->right;            
        }
        
        return res;
    }
    
};
```
