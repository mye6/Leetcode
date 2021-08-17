
## Solution 1 (CPP).
```cpp
// Time: O(M+N)
// Space: O(1)
class Solution {
public:
    
    int leftMostColumnWithOne(BinaryMatrix &bm) {
        auto dim=bm.dimensions();
        int m=dim[0], n=dim[1], i=0, j=n-1;
        
        int res=-1;
        while(i<m && j>=0) {
            if(bm.get(i,j)==0) {
                ++i;
            }
            else {
                res=j;
                --j;
            }            
        }
        
        return res;
    }
      
};
```

## Solution 1 (Python).
```python
# Time: O(M+N)
# Space: O(1)
class Solution:
    def leftMostColumnWithOne(self, bm: 'BinaryMatrix') -> int:
        m, n = bm.dimensions()
        
        i, j, res = 0, n-1, -1
        while i < m and j >= 0:
            if bm.get(i,j) == 1:
                res = j
                j -= 1
            else:
                i += 1
        
        return res
```