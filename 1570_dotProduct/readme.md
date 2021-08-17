
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(N)
class SparseVector {
public:
    
    vector<pair<int,int>> v;
    
    SparseVector(vector<int> &A) {
        for(int i=0; i<A.size(); ++i) {
            if(A[i]!=0) {
                v.push_back({i,A[i]});
            }
        }
    }
    
    int dotProduct(SparseVector& other) {
        // the two vectors (v) may be of different lengths
        int i=0, j=0, n=v.size(), m=other.v.size(), res=0;
        auto& v1=v;
        auto& v2=other.v;
        
        while(i<n && j<m) {
            if(v1[i].first<v2[j].first) {
                ++i;
            }   
            else if(v1[i].first>v2[j].first) {
                ++j;
            }
            else {
                res+=v1[i].second*v2[j].second;
                ++i; ++j;
            }
        }
        
        return res;
    }
    
};
```

## Solution 1 (Python).
```python
# Time: O(N)
# Space: O(N)
class SparseVector:
    def __init__(self, A: List[int]):
        self.mp = {}
        for i, n in enumerate(A):
            if n != 0: self.mp[i] = n
    
    def dotProduct(self, other: 'SparseVector') -> int:
        res = 0
        for j, n in other.mp.items():
            if j in self.mp:
                res += n * self.mp[j]
        
        return res
```