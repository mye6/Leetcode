
## Solution 1 (CPP). Two Pointers
```cpp
// Time: O(N)
// Space: O(1)
class Solution {
public:
    
    int trap(vector<int>& A) {
        int l=0, r=A.size()-1;
        
        int res=0, maxLeft=0, maxRight=0;
        
        while(l<r) {
            if(A[l]<=A[r]) {
                if(A[l]>=maxLeft) maxLeft=A[l];
                else res+=maxLeft-A[l];
                
                ++l;
            }
            else {
                if(A[r]>=maxRight) maxRight=A[r];
                else res+=maxRight-A[r];
                
                --r;
            }
        
        }
        
        return res;
    }
    
};
```
