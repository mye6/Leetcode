
## Solution 1 (CPP). Hash Table + DFS
```cpp
// Time: O(3^M * 4^N); M is #Char with 3 letters and N is #Char with 4 letters
// Space: O(3^M * 4^N)

class Solution {
public:
    
    vector<string> res;
    
    vector<string> m{
        "", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"    
    };
    
    void dfs(string digits, string cur, int pos) {
        if(pos==digits.size()) {
            res.push_back(cur); return;
        }
        
        string& s=m[digits[pos]-'0'];
        for(char c : s) {
            dfs(digits,cur+c,pos+1);
        }
    }
    
    vector<string> letterCombinations(string digits) {
        if(digits.size()==0) return res;
        dfs(digits,"",0);
        return res;
    }
      
};
```
