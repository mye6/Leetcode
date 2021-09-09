
## Solution 1 (CPP). Binary Search
```cpp
// Time: O(logN)
// Space: O(1)
class Solution {
public:
    
    
    // #missing: (A[mid]-l+1)-(mid-0+1)=A[mid]-mid-1 (l==1)
    // at (l-1), missing x==A[l-1]-(l-1)-1=A[l-1]-l
    // kth missing val: A[l-1]+k-x=k+l
    
    int findKthPositive(vector<int>& A, int k) {
        int l=0, r=A.size();              // [l,r)     
        
        while(l<r) {
            int mid=l+(r-l)/2;
            
            if(A[mid]-mid-1>=k) r=mid;   // [l,mid)
            else l=mid+1;                // [mid+1, r)
        } // A[l]-l-1>=k the smallest l
        
        return l+k;
    }
  
};
```
