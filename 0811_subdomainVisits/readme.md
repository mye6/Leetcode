
## Solution 1 (CPP). Hash Table
```cpp
// Time: O(NW)
// Space: O(N)

class Solution {
public:
       
    vector<string> subdomainVisits(vector<string>& S) {        
        // 1. extract and count all domains
        unordered_map<string,int> count;
        
        for(string& s : S) {
            int pos=s.find(' ');
            int n=stoi(s.substr(0,pos));
            
            string w=s.substr(pos+1);
            count[w]+=n;
            
            for(int i=0; i<w.size(); ++i) {
                if(w[i]=='.')
                    count[w.substr(i+1)]+=n;
            }
        }
        
        // 2. record result
        vector<string> res;
        for(auto& [w, n] : count) {
            res.push_back(to_string(n) + " " + w);
        }
        
        return res;
    }
    
    
};
```
