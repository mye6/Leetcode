
## Solution 1 (CPP). Hash Table
```cpp
// Time: O(N)
// Space: O(N)

class UndergroundSystem {
public:
    
    unordered_map<int,pair<string,int>> ins; // id->{station,t}
    unordered_map<string,pair<int,int>> outs; // route->{totalTime,count}    
    UndergroundSystem() { }
    void checkIn(int id, string stationName, int t) {
        ins[id]={stationName, t};
    }    
    void checkOut(int id, string stationName, int t) {
        auto& [s0, t0]=ins[id];
        string key=s0+"_"+stationName;
        outs[key].first+=(t-t0);
        ++outs[key].second;
        ins.erase(id); // optimization
    }    
    double getAverageTime(string startStation, string endStation) {
        auto& [totalTime, count]=outs[startStation+"_"+endStation];
        return (double)(totalTime)/count;
    }
    
};
```
