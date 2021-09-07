
## Solution 1 (CPP). Stack
```cpp
// Time: average O(1)
// Space: average O(H)
class BSTIterator {
public:
    
    stack<TreeNode*> st;
    
    void pushLeft(TreeNode* node) {
        while(node) {
            st.push(node);
            node=node->left;
        }
    }
    
    BSTIterator(TreeNode* root) {
        pushLeft(root);
    }
    
    int next() {
        TreeNode* cur=st.top(); st.pop();
        pushLeft(cur->right);
        return cur->val;
    }
    
    bool hasNext() {
        return !st.empty();    
    }
    
};
```
