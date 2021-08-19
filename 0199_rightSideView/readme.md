
## Solution 1 (CPP). DFS
```cpp
// Time: O(N)
// Space: O(H)
class Solution {
public:
    vector<int> res;
    
    void dfs(TreeNode* root, int level) {
        if(!root) return;
        if(level+1>res.size()) res.push_back(root->val);
        
        dfs(root->right,level+1);
        dfs(root->left,level+1);
    }
    
    vector<int> rightSideView(TreeNode* root) {
        dfs(root,0);
        return res;
    }
      
};
```

## Solution 1 (Python).
```python
# Time: O(N)
# Space: O(H)
class Solution:
    
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        def dfs(root, level):
            if not root: return
            
            if level==len(res): res.append(root.val)
            
            dfs(root.right, level+1)
            dfs(root.left, level+1)
        
        res = []
        dfs(root, 0)
        return res
```

## Solution 2 (CPP). BFS
```cpp
// Time: O(N)
// Space: O(W)~O(N/2)
class Solution {
public:
    
    vector<int> rightSideView(TreeNode* root) {
        vector<int> res;
        
        if(!root) return res;
        
        queue<TreeNode*> q;
        q.push(root);
        
        while(!q.empty()) {
            int len=q.size();
            
            for(int i=0; i<len; ++i) {
                TreeNode* cur=q.front(); q.pop();
                
                if(i==len-1) res.push_back(cur->val);
                
                if(cur->left) q.push(cur->left);
                if(cur->right) q.push(cur->right);
            }
            
        }
        
        return res;
    }
      
};
```

## Solution 2 (Python). BFS
```python
# Time: O(N)
# Space: O(W)~O(N/2)
class Solution:
    
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        res = []
        if not root: return res
        
        dq = collections.deque()
        dq.append(root)
        
        while dq:
            size, val = len(dq), 0
            for _ in range(size):
                node = dq.popleft()
                val = node.val
                
                if node.left: dq.append(node.left)
                if node.right: dq.append(node.right)
            
            res.append(val)
        
        return res
```