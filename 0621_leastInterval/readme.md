
## Solution 1 (CPP). Hash Table
```cpp
// Time: O(N)
// Space: O(N)

class Solution {
public:
    
    // N==3: AB**A:   max( (2-1)*(3+1)+1, 3)=5
    // N==1: ABACAC:  max( (3-1)*(1+1)+1, 6)=6
    
    int leastInterval(vector<char>& T, int N) {
        unordered_map<char,int> count;
        
        int M=0;
        for(char c : T) {
            M=max(M,++count[c]);
        }
        
        int res=(M-1)*(N+1);
        for(auto& [c, cnt] : count) {
            if(cnt==M) ++res;
        }
        
        if(res>T.size()) return res;
        
        return T.size();        
    }
  
};
```
