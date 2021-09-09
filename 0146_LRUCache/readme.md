
## Solution 1 (CPP). Hash Table
```cpp
// Time: O(N)
// Space: O(N)

class LRUCache {
public:
    
    int capacity;
    unordered_map<int,int> data;
    
    list<int> keys;
    unordered_map<int,list<int>::iterator> pos;
    
    void use(int key) {
        if(pos.count(key)) {
            keys.erase(pos[key]);
            pos.erase(key);            
        }
        else if(keys.size()==capacity) {
            int back=keys.back();
            
            data.erase(back);
            keys.pop_back();
            pos.erase(back);            
        }
        
        keys.push_front(key);
        pos[key]=keys.begin();        
    }    
    
    LRUCache(int capacity) : capacity(capacity) { }
    
    int get(int key) {
        if(!data.count(key)) return -1;
        
        use(key);
        return data[key];
    }
    
    void put(int key, int value) {
        use(key);
        data[key]=value;
    }
  
};
```
