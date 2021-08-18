
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(N)
class Solution {
public:
    
    int subarraySum(vector<int>& A, int k) {
        unordered_map<int,int> mp;
        mp[0]=1;
        
        int sum=0, res=0;
        for(int a : A) {
            sum+=a;
            
            if(mp.count(sum-k)) res+=mp[sum-k];
            ++mp[sum];
        }
        
        return res;
    }
      
};
```

## Solution 1 (Python).
```python
# Time: O(N)
# Space: O(N)
class Solution:
    
    def subarraySum(self, A: List[int], k: int) -> int:
        count = collections.Counter()
        count[0] = 1
        cur, res = 0, 0
        
        for a in A:
            cur += a
            res += count[cur-k]
            count[cur] += 1
        
        return res
```