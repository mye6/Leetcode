
## Solution 1 (CPP). Hash Table
```cpp
// Time: O(N)
// Space: O(1)

class Solution {
public:
    
    unordered_map<char,int> m{
        {'I',1},{'V',5},{'X',10},{'L',50},
        {'C',100},{'D',500},{'M',1000}
    };
    
    int romanToInt(string s) {
        int n=s.size();
        
        int res=0;
        for(int i=n-1; i>=0; --i) {
            res+=m[s[i]];
            if(i<n-1 && m[s[i]]<m[s[i+1]]) res-=2*m[s[i]];
        }
        
        return res;
    }
      
};
```
