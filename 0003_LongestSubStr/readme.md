

## Solution 1 (CPP).
Use a hash map to track the mapping from number to index.
```cpp
// OJ: https://leetcode.com/problems/longest-substring-without-repeating-characters/
// Author: github.com/mye6
// Time: O(N)
// Space: O(C) where C is the range of character set

class Solution {
public:
    
    
    int lengthOfLongestSubstring(string s) {
        int n=s.size();
        
        vector<int> last(256,-1);
        
        int left=-1, res=0;
        for(int i=0; i<n; ++i) {
            left=max(left, last[s[i]]);
            res=max(res,i-left);
            
            last[s[i]]=i;
        }
        
        return res;
    }  
};
```


## Solution 1 (PYTHON).
Use a hash map to track the mapping from number to index.
```python
// OJ: https://leetcode.com/problems/two-sum/
// Author: github.com/mye6
// Time: O(N)
// Space: O(1)

# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution(object):
    
    
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        dummy=tail=ListNode(0)
        c=0
        
        while l1 or l2 or c:
            if l1:
                c+=l1.val
                l1=l1.next
            if l2:
                c+=l2.val
                l2=l2.next
            
            tail.next=ListNode(c%10)
            tail=tail.next
            c//=10
            
        return dummy.next
```
