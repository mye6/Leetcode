
## Solution 1 (CPP). Hash Table
```cpp
// Time: O(NW); N is the number of words, W is the average length of word
// Space: O(NW)
class Solution {
public:    
    
    string encode(string& s) {
        string t;
        
        for(int i=0; i<s.size()-1; ++i) {
            int d=s[i+1]-s[i];
            d=(d+26)%26;
            t+=to_string(d)+",";            
        }
        
        return t;
    }    
    
    vector<vector<string>> groupStrings(vector<string>& S) {
        unordered_map<string,vector<string>> mp; // encode->{s}
        
        for(string& s : S) {
            string t=encode(s);
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
