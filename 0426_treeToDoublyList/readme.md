
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(N)
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* left;
    Node* right;

    Node() {}

    Node(int _val) {
        val = _val;
        left = NULL;
        right = NULL;
    }

    Node(int _val, Node* _left, Node* _right) {
        val = _val;
        left = _left;
        right = _right;
    }
};
*/

class Solution {
public:
    
    Node* head=nullptr, *tail=nullptr;
    
    void inorder(Node* root) {
        if(!root) return;
        inorder(root->left);
        
        if(head==nullptr) {
            head=root;
            tail=root;
        }
        else {
            tail->right=root;
            root->left=tail;
            tail=tail->right;
        }
        
        inorder(root->right);
    }
    
    Node* treeToDoublyList(Node* root) {
        if(!root) return root;
        inorder(root);
        
        tail->right=head;
        head->left=tail;
        
        return head;
    }  
};
```

## Solution 1 (Python).
```python
# Time: O(N)
# Space: O(N)
"""
# Definition for a Node.
class Node:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
"""
class Solution:
    
    head = None
    tail = None
    
    def inorder(self, root: 'Node'):
        if not root: return
        
        self.inorder(root.left)
        
        if(not self.head):
            self.head = root
            self.tail = root
        else:
            self.tail.right = root
            root.left = self.tail
            
            self.tail = self.tail.right
        
        self.inorder(root.right)
        
    
    def treeToDoublyList(self, root: 'Node') -> 'Node':
        if not root: return None
        self.inorder(root)
        
        self.tail.right = self.head
        self.head.left = self.tail
        
        return self.head
```