
## Solution 1 (CPP). Stack
```cpp
// Time: O(N)
// Space: O(N)
class Solution {
public:
    
    string simplifyPath(string path) {
        istringstream is(path);
        
        vector<string> st;
        string t;
        
        while(getline(is,t,'/')) {
            if(t=="" || t==".") continue;
            
            else if(t=="..") {
                if(!st.empty()) st.pop_back();
            }
            
            else {
                st.push_back(t);
            }            
        }
        
        string res;
        for(string& s : st) res+="/"+s;
        
        return res.empty() ? "/" : res;        
    }
      
};
```
