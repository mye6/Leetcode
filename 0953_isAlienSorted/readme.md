
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(1)
class Solution {
public:
    bool isAlienSorted(vector<string>& words, string order) {
        vector<int> ord(26,0);
        for(int i=0; i<26; ++i) {
            ord[order[i]-'a']=i;
        }
        
        for(string& w : words) {
            for(char& c : w) {
                c='a'+ord[c-'a'];
            }
        }
        
        for(int i=0; i<words.size()-1; ++i) {
            if(words[i]>words[i+1]) return false;
        }
        
        return true;
    }  
};
```

## Solution 1 (Python).
```python
# Time: O(N)
# Space: O(1)
class Solution:
    
    def isAlienSorted(self, words: List[str], order: str) -> bool:
        mp = {c : i for i, c in enumerate(order)}
        words = [[mp[c] for c in w] for w in words]
        return all( w1<=w2 for w1, w2 in zip(words, words[1:]) )
```