
## Solution 1 (CPP). Hash Table
```cpp
// Time: O(1)
// Space: O(N)

class LFUCache {
public:
    
    int capacity, len, minFreq;
    
    unordered_map<int,pair<int,int>> data; // key to {value,freq}
    
    unordered_map<int,list<int>> keys;
    unordered_map<int,list<int>::iterator> pos;    
    
    LFUCache(int capacity) : capacity(capacity), len(0) { }
    
    int get(int key) {
        if(!data.count(key)) return -1;
                
        auto& [val, freq]=data[key];
        
        keys[freq].erase(pos[key]);        
        ++freq;                
        keys[freq].push_front(key);
        pos[key]=keys[freq].begin();
                
        if(keys[minFreq].empty()) ++minFreq;
        
        return val;        
    }
    
    void put(int key, int value) {
        if(capacity<=0) return;
        
        int val=get(key);
        if(val!=-1) {
            data[key].first=value; return;
        }
        
        if(len>=capacity) {
            int oldKey=keys[minFreq].back();
            data.erase( oldKey );
            pos.erase( oldKey );
            keys[minFreq].pop_back();
            --len;
        }
        
        data[key]={value,1};
        keys[1].push_front(key);
        pos[key]=keys[1].begin();
        minFreq=1;
        ++len;        
    }
    
};

```
