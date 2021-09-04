
## Solution 1 (CPP). DFS
```cpp
// Time: O(N*2^N)
// Space: O(N*2^N)
class Solution {
public:
    
    unordered_map<string,vector<string>> dp;
    
    vector<string> combine(vector<string>& prev, string& b) {
        for(string& p : prev) {
            p+=" "+b;
        }
        
        return prev;
    }
    
    vector<string> wordBreak(string s, unordered_set<string>& dict) {
        if(dp.count(s)) return dp[s];
        
        vector<string> res;
        if(dict.count(s)) res.push_back(s);  // full string
        
        for(int i=1; i<s.size(); ++i) {
            string a=s.substr(0,i), b=s.substr(i);
            
            if(dict.count(b)) {
                auto prev=wordBreak(a,dict);
                auto ans=combine(prev,b);
                res.insert(res.end(),ans.begin(),ans.end());                
            }            
        }
        
        return dp[s]=res;
    }    
    
    vector<string> wordBreak(string s, vector<string>& wd) {
        unordered_set<string> dict(wd.begin(),wd.end());
        return wordBreak(s,dict);
    }
    
};
```
140. Word Break II