
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(1)
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& A) {
        int n=A.size();
        
        vector<int> res(n,1);
        int l=1, r=1;
        for(int i=0; i<n; ++i) {
            res[i]*=l; res[n-1-i]*=r;
            l*=A[i]; r*=A[n-1-i];
        }
        
        return res;
    }  
};
```

## Solution 1 (Python).
```python
# Time: O(N)
# Space: O(1)
class Solution:
    
    def productExceptSelf(self, A: List[int]) -> List[int]:
        res = [1 for _ in A]
        
        l, r = 1, 1
        for i in range(len(A)):
            res[i] *= l
            res[-1-i] *= r
            l *= A[i]
            r *= A[-1-i]
        
        return res
```