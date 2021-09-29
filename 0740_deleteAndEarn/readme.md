
## Solution 1 (CPP). Hash Table + Dynamic Programming
```cpp
// Time: O(N)
// Space: O(N)

class Solution {
public:
    
    int deleteAndEarn(vector<int>& A) {
        int N=10001;
        
        vector<int> values(N,0);
        for(int a : A) values[a]+=a;
        
        int take=0, skip=0;
        for(int i=0; i<N; ++i) {
            int take0=take, skip0=skip;
            skip=max(skip0, take0);
            take=skip0+values[i];
        }
        
        return max(skip,take);
    }

};
```
