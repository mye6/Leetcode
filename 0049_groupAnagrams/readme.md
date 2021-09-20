
## Solution 1 (CPP). Hash Table + Sorting (can also do counting)
```cpp
// Time: O(NWlogW)
// Space: O(NW)

class Solution {
public:
    
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string,vector<string>> mp;
        
        for(string& s : strs) {
            string t=s;
            sort(t.begin(), t.end());
            mp[t].push_back(s);
        }
        
        vector<vector<string>> res;
        for(auto& kv : mp) {
            res.push_back(kv.second);
        }
        
        return res;
    }
    
};
```
