
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(N)
/**
 * The read4 API is defined in the parent class Reader4.
 *     int read4(char *buf4);
 */

class Solution {
public:
    /**
     * @param buf Destination buffer
     * @param n   Number of characters to read
     * @return    The number of actual characters read
     */
    
    char buf4[4];
    int pos=0, size=0;
    
    int read(char *buf, int n) {
        for(int i=0; i<n; ++i) {            
            if(pos==size) {
                size=read4(buf4);
                pos=0;
                if(size==0) return i;
            }
            buf[i]=buf4[pos++];
        }
        
        return n;
    }
    
    
};
```
