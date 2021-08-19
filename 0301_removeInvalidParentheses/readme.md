
## Solution 1 (CPP).
```cpp
// Time: O(2^N)
// Space: O(N)
class Solution {
public:
    vector<string> res;
    
    bool valid(string s) {
        int cnt=0;
        
        for(char c : s) {
            if(c=='(') ++cnt;
            else if(c==')') --cnt;
            
            if(cnt<0) return false;
        }
        
        return cnt==0;
    }
    
    void dfs(string s, int l, int r, int pos) {
        if(l==0 && r==0) {
            if(valid(s)) res.push_back(s);
            return;
        }
        
        for(int i=pos; i<s.size(); ++i) {
            if(i!=pos && s[i]==s[i-1]) continue;
            
            if(s[i]=='(' || s[i]==')') {
                string cur=s; cur.erase(i,1);
                if(l>0 && )
            }
        }
        
    }
    
    vector<string> removeInvalidParentheses(string s) {
        int l=0, r=0;
        for(char c : s) {
            if(c=='(') ++l;
            else if(c==')') {
                if(l==0) ++r;
                else --l;
            }
        }
        
        dfs(s,l,r,0);
        return res;
    }  
};
```

## Solution 1 (Python).
```python
# Time: O(2^N)
# Space: O(N)
class Solution:
    def removeInvalidParentheses(self, s: str) -> List[str]:
        def isValid(s):
            stack = []
            for i in range(len(s)):
                if( s[i] == '(' ):
                    stack.append( (i,'(') )
                elif( s[i] == ')' ):
                    if(stack and stack[-1][1] == '('):
                        stack.pop()
                    else:
                        stack.append( (i,')') )         # pushing invalid close braces also
            return len(stack) == 0, stack
        
        
        def dfs(s, l, r):
            visited.add(s)
            if l == 0 and r == 0 and isValid(s)[0]:  res.append(s)
            for i, c in enumerate(s):
                if c != '(' and c != ')': continue                                    
                if (c == '(' and l == 0) or (c == ')' and r == 0): continue
                if s[:i]+s[i+1:] not in visited:
                    dfs( s[:i] + s[i+1:], l-(c=='('), r-(c==')') )
        
        stack = isValid(s)[1]
        l = sum([1 for val in stack if val[1] == "("]) # num of left braces
        r = len(stack) - l
        
        res, visited = [], set()
        dfs(s, l, r)
        return res
```