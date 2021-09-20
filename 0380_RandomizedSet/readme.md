
## Solution 1 (CPP). Hash Table
```cpp
// Time: O(1)
// Space: O(N)

class RandomizedSet {
public:
    
    vector<int> A;
    unordered_map<int,int> pos;
    
    RandomizedSet() { }
    
    bool insert(int val) {
        if(pos.count(val)) return false;
        
        pos[val]=A.size();
        A.push_back(val);
        return true;
    }
    
    bool remove(int val) {
        if(!pos.count(val)) return false;
        
        int back=A.back();
        int idx=pos[val];
        
        A[idx]=back;
        pos[back]=idx;
        
        A.pop_back();
        pos.erase(val);
        return true;
    }
    
    /** Get a random element from the set. */
    int getRandom() {
        return A[rand()%A.size()];
    }
};
```
