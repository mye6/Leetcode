
## Solution 1 (CPP).
```cpp
// Time: O(N)
// Space: O(N)
class Solution {
public:
    
    struct Log{
        int id;
        string type;
        int time;
    };
    
    Log parse(string& s) {
        istringstream is(s);
        
        string s1, s2, s3;
        getline(is,s1,':');
        getline(is,s2,':');
        getline(is,s3,':');
        
        return Log{stoi(s1),s2,stoi(s3)};
    }
    
    vector<int> exclusiveTime(int n, vector<string>& logs) {
        vector<int> times(n,0);
        stack<Log> st;
        
        for(string& log : logs) {
            Log item=parse(log);
            
            if(item.type=="start") {
                st.push(item);
            }
            else {
                assert(item.id==st.top().id);
                Log start=st.top(); st.pop();
                int id=item.id;
                int duration=item.time-start.time+1;
                
                times[id]+=duration;
                if(!st.empty()) times[st.top().id]-=duration;
            }
        }
        
        return times;
    }
    
    
};
```
