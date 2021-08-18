
## Solution 1 (CPP). Priority Queue
```cpp
// Time: O(NlogK)
// Space: O(K)
class Solution {
public:
    vector<vector<int>> kClosest(vector<vector<int>>& pts, int k) {
        auto cmp=[](vector<int>& a, vector<int>& b) {
            return a[0]*a[0]+a[1]*a[1] < b[0]*b[0]+b[1]*b[1];
        };
        priority_queue<vector<int>,vector<vector<int>>,decltype(cmp)> pq(cmp);
        
        for(auto& p : pts) {
            pq.push(p);
            if(pq.size()>k) pq.pop();
        }
        
        vector<vector<int>> res;
        while(!pq.empty()) {
            res.push_back(pq.top()); pq.pop();
        }
        
        return res;
    }
};
```

## Solution 1 (Python). Priority Queue
```python
# Time: O(NlogK)
# Space: O(K)
class Solution:
    def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
        return heapq.nsmallest(k, points, lambda p: p[0]*p[0]+p[1]*p[1])
```

## Solution 2 (CPP). Quick Sort
```cpp
// Time: O(N)
// Space: O(1)
class Solution {
public:
    
    bool closer(vector<int>& a, vector<int>& b) {
        return a[0]*a[0]+a[1]*a[1] < b[0]*b[0]+b[1]*b[1];
    }
    
    int partition(vector<vector<int>>& pts, int l, int r) {
        auto& pivot=pts[r];
        int j=l;
        
        for(int i=l; i<r; ++i) {
            if(closer(pts[i], pivot)) swap(pts[j++], pts[i]);
        }
        swap(pts[j],pts[r]);
        
        return j;
    }
    
    void sort(vector<vector<int>>& pts, int k, int l, int r) {
        if(l>=r) return;
        
        int p=partition(pts, l, r);
        
        if(p==k) return;
        else if(p<k) sort(pts, k, p+1, r);
        else sort(pts, k, l, p-1);            
    }
    
    vector<vector<int>> kClosest(vector<vector<int>>& pts, int k) {
        sort(pts, k, 0, pts.size()-1);
        return vector<vector<int>>(pts.begin(),pts.begin()+k);
    }  
};
```

## Solution 2 (Python). Quick Sort
```python
# Time: O(N)
# Space: O(1)
class Solution:
    
    def closer(self, p1, p2):
        return p1[0]**2 + p1[1]** 2 <= p2[0]**2 + p2[1]**2
    
    def partition(self, pts, l, r):
        pivot = pts[r]
        a = l
        for i in range(l, r):
            if self.closer(pts[i], pivot):            
                pts[a], pts[i] = pts[i], pts[a]
                a += 1
        
        pts[a], pts[r] = pts[r], pts[a]
        
        return a
    
    def sort(self, pts, k, l, r):
        if l < r:
            p = self.partition(pts, l, r)
            if p == k:
                return
            elif p < k:
                self.sort(pts, k, p+1, r)
            else:
                self.sort(pts, k, l, p-1)
    
    def kClosest(self, pts: List[List[int]], k: int) -> List[List[int]]:
        self.sort(pts, k, 0, len(pts)-1)
        return pts[:k]
```