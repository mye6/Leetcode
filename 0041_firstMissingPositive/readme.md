
## Solution 1 (CPP). Hash Table + Index Sorting
```cpp
// Time: O(N)
// Space: O(1)

class Solution {
public:

    
    int firstMissingPositive(vector<int>& A) {
        int n=A.size();
                
        for(int i=0; i<n; ++i) {
            while(1<=A[i] && A[i]<=n && A[A[i]-1]!=A[i])
                swap(A[i], A[A[i]-1]);
        }
        
        for(int i=0; i<n; ++i) {
            if(A[i]!=i+1) return i+1;
        }
        
        return n+1;
    }
      
};
```
