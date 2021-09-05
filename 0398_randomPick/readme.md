
## Solution 1 (CPP). Reservoir sampling
```cpp
// Time: O(N)
// Space: O(N)
class Solution {
public:
    
    vector<int> A;
    
    Solution(vector<int>& A) : A(A) { }
    
    int pick(int T) {
        int n=A.size();
        
        int k=0, x=-1;
        for(int i=0; i<n; ++i) {
            if(A[i]!=T) continue;
            
            ++k;
            int r=rand()%k;
            if(r==0) x=i;
        }
        
        return x;
    }
      
};
```
