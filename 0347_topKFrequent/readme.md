
## Solution 1 (CPP). Min Heap
```cpp
// Time: O(NlogK)
// Space: O(K)

class Solution {
public:
    
    typedef pair<int,int> pi;
    
    vector<int> topKFrequent(vector<int>& A, int k) {
        unordered_map<int,int> count;
        for(int a : A) ++count[a];
        
        // min pq; {cnt, val}
        priority_queue<pi,vector<pi>, greater<pi>> pq;
        
        for(auto& [val, cnt] : count) {
            pq.push({cnt,val});
            if(pq.size()>k) pq.pop();
        }
        
        vector<int> res;
        while(!pq.empty()) {
            res.push_back(pq.top().second);
            pq.pop();
        }
        
        return res;        
    }
    
};
```



## Solution 2 (CPP). Bucket Sort
```cpp
// Time: O(N)
// Space: O(N)

class Solution {
public:
    
    vector<int> topKFrequent(vector<int>& A, int k) {
        // 1. count A
        unordered_map<int,int> count;
        for(int a : A)
            ++count[a];
        
        // 2. record into bucket
        vector<vector<int>> bucket(A.size()+1);
        for(auto& [a, cnt] : count) {
            bucket[cnt].push_back(a);
        }
        
        // 3. extract
        vector<int> res;
        for(int i=A.size(); i>=1; --i) {
            for(int a : bucket[i]) {
                res.push_back(a);
                if(res.size()==k) return res;
            }
        }
        
        return res;
    }
	
};
```
