
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(1)
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* next;

    Node() {}

    Node(int _val) {
        val = _val;
        next = NULL;
    }

    Node(int _val, Node* _next) {
        val = _val;
        next = _next;
    }
};
*/

class Solution {
public:
    
    Node* insert(Node* head, int x) {
        // 1. empty head
        if(head==nullptr) {
            head=new Node(x);
            head->next=head;
            return head;
        }
        // 2. find the proper pos
        Node *cur=head, *nxt=head->next;
        while(!(cur->val<=x && x<=nxt->val)
          &&  !(cur->val>nxt->val && cur->val<=x)
          &&  !(cur->val>nxt->val && x<=nxt->val)) {
            
            cur=nxt;
            nxt=nxt->next;
            
            if(cur==head) break;
        }
        
        cur->next=new Node(x, nxt);
        
        return head;
    }
    
};
```
