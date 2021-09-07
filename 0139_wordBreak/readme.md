
## Solution 1 (CPP). Dynamic programming
```cpp
// Time: O(N^2)
// Space: O(N)
class Solution {
public:
    
    bool wordBreak(string s, vector<string>& wd) {
        int n=s.size();
        unordered_set<string> dict(wd.begin(), wd.end());
        vector<bool> dp(n+1,false);
        
        dp[0]=true;
        for(int i=1; i<=n; ++i) {
            for(int j=0; j<i; ++j) {
                if(dp[j] && dict.count(s.substr(j,i-j)) ) {
                    dp[i]=true;
                    break;
                }
            }
        }
        
        return dp[n];
    }
      
};
```
