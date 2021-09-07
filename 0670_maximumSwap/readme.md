
## Solution 1 (CPP). Reservoir sampling
```cpp
// Time: O(N)
// Space: O(N)
class Solution {
public:
    
    
    // https://www.youtube.com/watch?v=6hFyHU7BNlI
    // 2 9 9 7
    // ->
    // 9 9 2 7 (find the last one that is greater than 2 and swap it)
    
    int maximumSwap(int num) {
        // 1. convert num to string
        string s=to_string(num);
        
        // 2. record the last pos of each digit
        int n=s.size();
        vector<int> last(10, -1);        
        for(int i=0; i<n; ++i) {
            last[s[i]-'0']=i;
        }
        
        // 3. check from left to right;
        //   if a larger digit exists in later pos than current (>i)
        for(int i=0; i<n; ++i) {
            for(int d=9; d>s[i]-'0'; --d) {
                if(last[d] > i) {
                    swap(s[i], s[last[d]]);
                    return stoi(s);
                }
            }
        }
        
        return num;
    }
    
};
```
