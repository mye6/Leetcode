
## Solution 1 (CPP).
```cpp
// Time: O(logM + logN)
// Space: O(logM + logN)

class Solution {
public:
    
    
    int getkth(vector<int>& s, int l1, int r1,
               vector<int>& l, int l2, int r2, int k) {
        if(r1-l1>r2-l2) return getkth(l,l2,r2, s,l1,r1, k);
                
        if(r1==l1) return l[l2+k-1];       // bc1. no s
        if(k==1) return min(s[l1],l[l2]);  // bc2. only the min
                
        int i=min(r1-l1,k/2), j=min(r2-l2,k/2);
        
        if(s[l1+i-1]>l[l2+j-1]) return getkth(s,l1,r1,l,l2+j,r2,k-j);        
        else return getkth(s,l1+i,r1,l,l2,r2,k-i);        
    }    
    
    double findMedianSortedArrays(vector<int>& A, vector<int>& B) {
        int m=A.size(), n=B.size();
        int l=(m+n+1)/2, r=(m+n+2)/2;
        
        return (getkth(A,0,m,B,0,n,l) + getkth(A,0,m,B,0,n,r))/2.0;
    }
    
    
};
```
