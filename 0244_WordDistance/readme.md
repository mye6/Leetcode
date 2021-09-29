
## Solution 1 (CPP). Hash Table
```cpp

class WordDistance {
public:
    
    unordered_map<string,vector<int>> mp;
    
    WordDistance(vector<string>& ws) {
        for(int i=0; i<ws.size(); ++i) {
            mp[ws[i]].push_back(i);
        }
    }
    
    int shortest(string word1, string word2) {
        auto& v1=mp[word1];
        auto& v2=mp[word2];
        int i=0, j=0, m=v1.size(), n=v2.size();
        int d=INT_MAX;
        
        while(i<m && j<n) {
            d=min(d,abs(v1[i]-v2[j]));
            if(v1[i]<v2[j]) ++i;
            else ++j;
        }
        
        return d;
    }
      
};
```
