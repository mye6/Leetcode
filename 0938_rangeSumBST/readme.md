
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(H)
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
    
    int rangeSumBST(TreeNode* root, int low, int high) {
        if(!root) return 0;
        
        int sum = 0;
        if(root->val > low) sum += rangeSumBST(root->left, low, high);
        if(root->val < high) sum += rangeSumBST(root->right, low, high);
        
        if(low<=root->val && root->val<=high)
            sum+=root->val;
        
        return sum;
    }
    
};
```

## Solution 1 (Python).
```python
// Time: O(N)
// Space: O(H) due to recursive call stacks
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    
    def rangeSumBST(self, root: Optional[TreeNode], low: int, high: int) -> int:
        if not root: return 0
        
        sum = 0
        if root.val > low:
            sum += self.rangeSumBST(root.left, low, high)
        
        if root.val < high:
            sum += self.rangeSumBST(root.right, low, high)
        
        if low<=root.val and root.val<=high:
            sum += root.val
        
        return sum
```