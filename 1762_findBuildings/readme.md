
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(1)
class Solution {
public:
    
    vector<int> findBuildings(vector<int>& A) {
        vector<int> res;
        
        for(int i=0; i<A.size(); ++i) {
            while(!res.empty() && A[i]>=A[res.back()])
                res.pop_back();
            
            res.push_back(i);
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
    
    def findBuildings(self, A: List[int]) -> List[int]:
        res = []
        res.append(len(A)-1)
        maxHeight = A[-1]
        n=len(A)
        
        for i in range(n-2, -1, -1):
            if A[i] > maxHeight:
                res.insert(0, i)
                maxHeight = A[i]
        
        return res
```