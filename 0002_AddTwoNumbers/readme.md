# [2. Add Two Numbers (Medium)](https://leetcode.com/problems/add-two-numbers/)

<p>You are given two <b>non-empty</b> linked lists representing two non-negative integers. The digits are stored in <b>reverse order</b> and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.</p>

<p>You may assume the two numbers do not contain any leading zero, except the number 0 itself.</p>

<p><b>Example:</b></p>

<pre><b>Input:</b> (2 -&gt; 4 -&gt; 3) + (5 -&gt; 6 -&gt; 4)
<b>Output:</b> 7 -&gt; 0 -&gt; 8
<b>Explanation:</b> 342 + 465 = 807.
</pre>


**Related Topics**:  
[Linked List](https://leetcode.com/tag/linked-list/), [Math](https://leetcode.com/tag/math/)

**Similar Questions**:
* [Multiply Strings (Medium)](https://leetcode.com/problems/multiply-strings/)
* [Add Binary (Easy)](https://leetcode.com/problems/add-binary/)
* [Sum of Two Integers (Easy)](https://leetcode.com/problems/sum-of-two-integers/)
* [Add Strings (Easy)](https://leetcode.com/problems/add-strings/)
* [Add Two Numbers II (Medium)](https://leetcode.com/problems/add-two-numbers-ii/)
* [Add to Array-Form of Integer (Easy)](https://leetcode.com/problems/add-to-array-form-of-integer/)

## Solution 1 (CPP).
Use a hash map to track the mapping from number to index.
```cpp
// OJ: https://leetcode.com/problems/two-sum/
// Author: github.com/mye6
// Time: O(N)
// Space: O(1)

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    
    
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode dummy(-1), *tail=&dummy;
        
        int c=0;
        while(l1 || l2 || c>0) {
            if(l1) {
                c+=l1->val;
                l1=l1->next;
            }
            if(l2) {
                c+=l2->val;
                l2=l2->next;
            }

            ListNode* p = new ListNode(c%10);
            c/=10;
            
            tail->next=p;
            tail=tail->next;
        }
        
        return dummy.next;
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
