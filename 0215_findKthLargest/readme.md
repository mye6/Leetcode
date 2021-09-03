
## Solution 1 (CPP). Priority Queue
```cpp
// Time: O(NlogK)
// Space: O(K)
class Solution {
public:
    int findKthLargest(vector<int>& A, int k) {
        priority_queue<int,vector<int>,greater<int>> pq;
        
        for(int a : A) {
            pq.push(a);
            if(pq.size()>k) pq.pop();
        }
        
        return pq.top();
    }
      
};
```


## Solution 2 (CPP). Quick Select
```cpp
// Time: O(N)~O(N^2)
// Space: O(1)
class Solution {
public:
    int quickSelect(vector<int>& A, int k, int l, int r) {
        int pivot=A[r], j=l;
        
        for(int i=l; i<r; ++i) {
            if(A[i]>pivot) swap(A[j++], A[i]);
        }
        
        int q=j-l+1;
        
        if(q==k) return pivot;
        
        else if(q<k) return quickSelect(A,k-q,j,r-1);
        else return quickSelect(A,k,l,j-1); 
    }
    
    int findKthLargest(vector<int>& A, int k) {
        return quickSelect(A,k,0,A.size()-1);    
    }
      
};
```

