
## Solution 1 (CPP). Reservoir sampling
```cpp
// Time: O(logN)
// Space: O(1)
class Solution {
public:
    
    int divide(int A, int B) {
        long a=labs(A), b=labs(B);
        if(a<b) return 0;
        
        long res=0;
        while(a>=b) {
            long x=b, p=1;
            
            while(a>(x<<1)) {
                x<<=1; p<<=1;                
            }
            
            a-=x; res+=p;            
        }
        
        if((A<0) ^ (B<0)) res=-res;
        if(res>INT_MAX) return INT_MAX;
        
        return res;
    }
      
};
```
