
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(1)

class Solution {
public:
    
    void nextPermutation(vector<int>& A) {
        int n=A.size();        
        
        // 1. from right (n-2) to left, find the first one A[i]<A[i+1]
        int i=n-2;
        while(i>=0 && A[i]>=A[i+1]) --i;
        // i==-1 or A[i]<A[i+1]
        
        // 7 3 2 1
        // 1 2 3 7 (reverse)
        if(i==-1) { // no i s.t. A[i]<A[i+1]
            reverse(A.begin(), A.end());
            return;
        }
        
        // 2. from right (n-1) to left, find the first one A[j]>A[i]
        // 7 |2| |3| 1
        // 7 |3| |2| 1 (swap)
        // 7 |3| 1  2  (reverse) 
        int j=n-1;
        while(A[j]<=A[i]) --j;
        
        swap(A[i], A[j]);
        reverse(A.begin()+i+1, A.end());
    }
    
    
};
```
