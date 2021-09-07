
## Solution 1 (CPP). Stack
```cpp
// Time: O(N)
// Space: O(N)
class Solution {
public:
    
    TreeNode* str2tree(string s) {
        stack<TreeNode*> st;
        
        int n=s.size();
        
        for(int i=0; i<n; ++i) {
            // 1. '(': skip
            if(s[i]=='(') continue;
            
            // 2. digit OR -: get the number, create a new node
            else if(isdigit(s[i]) || s[i]=='-') {    // OR
                int sign=1, v=0;
                if(s[i]=='-') { sign=-1; ++i; }
                while(i<n && isdigit(s[i])) {
                    v=v*10 + s[i++]-'0';
                }
                --i;
                TreeNode* t = new TreeNode(sign*v);
                st.push(t);
            }
            
            // 3. ')' retrieve node from stack and append
            else if(s[i]==')') {
                TreeNode* t = st.top(); st.pop();
                TreeNode* p = st.top();
                p->left==nullptr ? p->left=t : p->right=t;
            }            
        }
        
        return st.empty() ? nullptr : st.top();
    }  
};
```
