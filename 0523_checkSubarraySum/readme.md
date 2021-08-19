
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(N)
class Solution {
public:
    bool checkSubarraySum(vector<int>& A, int k) {
        unordered_map<int,int> pos;
        pos[0]=-1;
        
        int cur=0, n=A.size();
        for(int i=0; i<n; ++i) {
            cur+=A[i];
            
            if(k>0) cur%=k;
            
            if(pos.count(cur) && i-pos[cur]>=2)
                return true;
            
            if(!pos.count(cur)) pos[cur]=i;
        }
        
        return false;
    }
    
};
```

## Solution 1 (Python).
```python
# Time: O(N)
# Space: O(N)
class Solution:
    
    def checkSubarraySum(self, A: List[int], k: int) -> bool:
        mp = {0: -1}
        
        sum = 0        
        for i, n in enumerate(A):
            sum += n
            if k != 0: sum %= k
            
            if sum not in mp:
                mp[sum] = i
            else:
                if i - mp[sum] >= 2:
                    return True
        
        return False
```