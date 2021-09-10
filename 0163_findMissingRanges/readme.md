
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(1)

class Solution {
public:
    
    string range(int s, int e) {
        return s==e ? to_string(s) : to_string(s)+"->"+to_string(e);
    }    
    
    vector<string> findMissingRanges(vector<int>& A, int lower, int upper) {
        int n=A.size();
        
        vector<string> res;
        
        long prev=(long)lower-1;
        for(int i=0; i<=n; ++i) {
            int cur=(i==n ? (long)upper+1 : A[i]);
            
            if(cur-1>=prev+1) res.push_back(range(prev+1,cur-1));
            
            prev=cur;
        }
        
        return res;
    }
  
};
```
