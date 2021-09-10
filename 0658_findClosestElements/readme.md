
## Solution 1 (CPP).
```cpp
// Time: O(logN)
// Space: O(1)

class Solution {
public:
    
    vector<int> findClosestElements(vector<int>& A, int k, int x) {
        int l=0, r=A.size()-k;
        
        while(l<r) {
            int mid=l+(r-l)/2;
            if(x-A[mid] > A[mid+k]-x) l=mid+1;
            else r=mid;            
        }
        
        return vector<int>(A.begin()+l, A.begin()+l+k);
    }
    
};
```
