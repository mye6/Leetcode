# HEAD 1
## 2nd HEAD

# you can search for markdown tutorial


## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/two-sum/
// Author: github.com/mye6
// Time: O(N)
// Space: O(N)

class Solution {
public:

    vector<int> twoSum(vector<int>& A, int T) {
        unordered_map<int,int> pos;
        
        for(int i=0; i<A.size(); ++i) {
            if(pos.count(T-A[i]))
                return {pos[T-A[i]],i};
            
            pos[A[i]]=i;
        }
        
        return {};
    }
    
};
```