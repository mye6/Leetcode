
## Solution 1 (CPP). Hash Table
```cpp
// Time: get O(logN); set O(logN)
// Space: O(lN)

class TimeMap {
public:
    
    unordered_map<string, map<int,string>> mp;  // key->{time,value}
    
    TimeMap() { }
    
    void set(string key, string value, int timestamp) {
        mp[key][timestamp]=value;
    }
    
    string get(string key, int timestamp) {        
        auto it=mp.find(key);
        if(it==mp.end()) return "";
        
        auto& mp2=mp[key];        
        auto it2=mp2.upper_bound(timestamp);
        
        if(it2==mp2.begin()) return "";
        return prev(it2)->second;
    }
      
};
```
