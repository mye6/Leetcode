## Solution 1.
Use a hash map to track the mapping from number to index.
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

## Solution 2.
Sort and then use two pointers.
```cpp
// OJ: https://leetcode.com/problems/two-sum/
// Author: github.com/mye6
// Time: O(NlogN)
// Space: O(N)
class Solution {
public:
    
    vector<int> twoSum(vector<int>& A0, int T) {
        int n=A0.size();
        
        vector<vector<int>> A;
        for(int i=0; i<n; ++i) {
            A.push_back({A0[i],i});
        }
        
        sort(A.begin(), A.end());
        
        int l=0, r=n-1;
        while(l<r) {
            int sum=A[l][0]+A[r][0];
            
            if(sum==T) return {A[l][1],A[r][1]};
            else if(sum<T) ++l;
            else --r;
        }
        
        return {};
    }
    
};
```

