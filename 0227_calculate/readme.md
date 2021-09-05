
## Solution 1 (CPP). Hash Table
```cpp
// Time: O(N); N is the number of words, W is the average length of word
// Space: O(1)
class Solution {
public:
    
    int n;
    
    long parseNum(string& s, int& i) {
        long num=0;
        
        while(i<n) {
            if(isdigit(s[i])) num=num*10+s[i]-'0';
            else if(s[i]!=' ') return num;
            ++i;
        }
        
        return num;
    }
    
    int calculate(string s) {
        n=s.size();
        
        int i=0;
        long res=0, num=parseNum(s,i), sign=1;
        
        while(i<n) {            
            if(s[i]=='+' || s[i]=='-') {
                res+=sign*num;
            
                sign=(s[i]=='+' ? 1 : -1);
                num=parseNum(s,++i);    
            }
            else if(s[i]=='*') {
                num*=parseNum(s,++i);
            }
            else if(s[i]=='/') {
                num/=parseNum(s,++i);
            }            
        }
        
        res+=sign*num;
        return res;
    }
      
};
```
