
## Solution 1 (CPP). Stack
```cpp
// Time: O(N)
// Space: O(N)
class Solution {
public:
    
    string removeDuplicates(string s) {
        int k=2;
        
        vector<pair<int,char>> st{{0,'#'}};
        
        for(char c : s) {
            if(c!=st.back().second)
                st.push_back({1,c});
            
            else if(++st.back().first==k)
                st.pop_back();            
        }
        
        string res;
        for(auto& [cnt, c] : st)
            res.append(cnt,c);
        
        return res;
    }
      
};
```
