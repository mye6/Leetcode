
## Solution 1 (CPP).
```cpp
// Time: O(N^2 * 4^(N-1)) -> O(4^(N-1))
// Space: O(N^2)
class Solution {
public:
    
    vector<string> res;
    
    void dfs(string& s, int T, int pos, long pv, long cv, string r) {
        if(pos==s.size() && cv==T)  {
            res.push_back(r); return;
        }
        
        for(int len=1; len<=s.size()-pos; ++len) {
            string t=s.substr(pos,len);
            if(len>1 && t[0]=='0') continue;
            
            long n=stol(t);
            if(pos==0) {
                dfs(s,T,len,n,n,t); continue;    
            }
            
            dfs(s,T,pos+len,n,cv+n,r+"+"+t);
            dfs(s,T,pos+len,-n,cv-n,r+"-"+t);
            dfs(s,T,pos+len,pv*n,cv-pv+pv*n,r+"*"+t);            
        }
    }    
    
    vector<string> addOperators(string s, int T) {
        dfs(s,T,0,0,0,"");
        return res;        
    }
    
};
```
