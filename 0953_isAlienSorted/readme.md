
## Solution 1 (CPP). Hash Table
```cpp
// Time: O(NW)
// Space: O(26)

class Solution {
public:
    
    
    bool isAlienSorted(vector<string>& words, string order) {
        vector<int> ord(26,0);
        for(int i=0; i<order.size(); ++i)
            ord[order[i]-'a']=i;
        
        for(string& w : words) {
            for(char& c : w) {
                c='a'+ord[c-'a'];
            }
        }
        
        for(int i=0; i<words.size()-1; ++i) {
            if(words[i]>words[i+1]) return false;
        }
        
        return true;
    }
      
};
```
