
## Solution 1 (CPP).
```cpp
// Time: intialize: O(N), query: O(logN)
// Space: O(N)
class Solution {
public:
    
    vector<int> psum;
    int tw;
    
    Solution(vector<int>& w) : psum(w) {
        for(int i=1; i<psum.size(); ++i) {
            psum[i]+=psum[i-1];
        }
        tw=psum.back();
    }
    
    int pickIndex() {
        int r=rand()%tw;
        int res=upper_bound(psum.begin(),psum.end(),r)-psum.begin();
        return res;
    }
};

```

## Solution 1 (Python).
```python
# Time: initialize: O(N), query: O(logN)
# Space: O(N)
class Solution:

    def __init__(self, w: List[int]):
        self.w = list(itertools.accumulate(w))
        

    def pickIndex(self) -> int:
        x = random.randint(1, self.w[-1])
        res = bisect.bisect_left(self.w, x)
        return res
```