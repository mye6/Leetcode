
## Solution 1 (CPP). Two Pointers
```cpp
// Time: O(N)
// Space: O(1)

class Solution {
public:

    void merge(vector<int>& A, int m, vector<int>& B, int n) {
        int k=m+n-1, i=m-1, j=n-1;
        
        while(i>=0 && j>=0) {
            if(A[i]>B[j]) A[k--]=A[i--];
            else A[k--]=B[j--];
        }
        
        while(i>=0) A[k--]=A[i--];
        while(j>=0) A[k--]=B[j--];        
    }
	
};
```
