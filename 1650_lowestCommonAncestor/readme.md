
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(1)
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* left;
    Node* right;
    Node* parent;
};
*/

class Solution {
public:
    
    int getDepth(Node* p) {
        int cnt=0;
        
        while(p) {
            ++cnt;
            p=p->parent;
        }
        
        return cnt;
    }
    
    Node* lowestCommonAncestor(Node* p, Node * q) {
        int n1=getDepth(p), n2=getDepth(q);
        // require n1>=n2
        if(n2>n1) return lowestCommonAncestor(q,p);
        
        while(n1>n2) {
            p=p->parent;
            --n1;
        }
        
        while(p!=q) {
            p=p->parent;
            q=q->parent;
        }
        
        return p;
    }  
};
```

## Solution 1 (Python).
```python
# Time: O(N)
# Space: O(1)
"""
# Definition for a Node.
class Node:
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None
        self.parent = None
"""

class Solution:
    
    def depth(self, p: 'Node') -> int:
        cnt = 0
        while p:
            cnt += 1
            p = p.parent
        
        return cnt
    
    def lowestCommonAncestor(self, p: 'Node', q: 'Node') -> 'Node':
        n1, n2 = self.depth(p), self.depth(q)
        if n1 < n2: return self.lowestCommonAncestor(q, p)
        
        while n1 > n2:
            n1 -= 1
            p = p.parent
        
        while p != q:
            p = p.parent
            q = q.parent
        
        return p
```