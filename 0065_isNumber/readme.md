
## Solution 1 (CPP). Iteration
```cpp
// Time: O(N)
// Space: O(1)
class Solution {
public:
    
    
    bool isNumber(string s) {
        int n=s.size(), i=0, digits=0, dots=0;
        
        // 1. skip spaces
        while(i<n && s[i]==' ') ++i;
        
        // 2. skip '+'/'-'
        if(s[i]=='+' || s[i]=='-') ++i;
        
        // 3. digits or dots
        while(i<n && ( isdigit(s[i]) || s[i]=='.' ) ) {
            isdigit(s[i]) ? ++digits : ++dots;
            ++i;
        }
        if(digits==0 || dots>1) return false;
        
        // 4. e/E
        if(tolower(s[i])=='e') {
            ++i; // skip it
            
            if(s[i]=='+'||s[i]=='-') ++i;
            
            digits=0;
            while(i<n && isdigit(s[i])) {
                ++digits;
                ++i;
            }
            if(digits==0) return false;
        }
        
        // 5. skip the tailing spaces ' '
        while(i<n && s[i]==' ') ++i;
        
        return i==n;
    }  
};
```
