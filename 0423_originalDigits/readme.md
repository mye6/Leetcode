
## Solution 1 (CPP). Hash Table
```cpp
// Time: O(N)
// Space: O(N)

class Solution {
public:
    
    string originalDigits(string s) {
        vector<int> count(10,0);
        
        for(char c : s) {
            switch(c) {
                case 'z': ++count[0]; break; // 0
                case 'w': ++count[2]; break; // 2
                case 'u': ++count[4]; break; // 4
                case 'x': ++count[6]; break; // 6
                case 'g': ++count[8]; break; // 8
                case 's': ++count[7]; break; // (6,7)
                case 'f': ++count[5]; break; // (4,5)
                case 'o': ++count[1]; break; // (0, 2, 4, 1)
                case 't': ++count[3]; break; // (2, 8, 3)
                case 'i': ++count[9]; break; // (5, 8, 5, 9) 
            }    
        }
        
        count[7] = count[7] - count[6];
        count[5] = count[5] - count[4];
        count[1] = count[1] - count[0] - count[2] - count[4];
        count[3] = count[3] - count[2] - count[8];
        count[9] = count[9] - count[5] - count[6] - count[8];

        string res;
        for(int i=0; i<10; ++i){
            for(int j=0; j<count[i]; ++j){
                res += to_string(i);
            }
        }       
        
        return res;
    }
    
};
```
