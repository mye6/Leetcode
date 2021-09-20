
## Solution 1 (CPP). Hash Table + BFS
```cpp
// Time: O(N*26^W)
// Space: O(N)

class Solution {
public:
    
    int ladderLength(string s, string e, vector<string>& words) {
        unordered_set<string> dict(words.begin(), words.end());
        
        if(!dict.count(e)) return 0;
        
        queue<string> q; q.push(s);
        
        int steps=1;     // the steps includes itself
        while(!q.empty()) {
            int len=q.size();
            
            while(len--) {
                string word=q.front(); q.pop();
                
                // iterate all possible words, i.e. per i, per char
                for(int i=0; i<word.size(); ++i) {
                    string word2=word;
                    
                    for(char c='a'; c<='z'; ++c) {
                        word2[i]=c;
                        if(word2==e) return steps+1;
                        
                        if(!dict.count(word2)) continue;
                        q.push(word2);
                        dict.erase(word2);
                    }                    
                }
            }
            
            ++steps;
        }
        
        return 0;
    }
      
};
```
