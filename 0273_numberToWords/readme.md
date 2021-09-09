
## Solution 1 (CPP). Recursion
```cpp
// Time: O(logN)
// Space: O(logN)

class Solution {
public:
    
    vector<string> below100{
        "", "", "Twenty", "Thirty", "Forty", "Fifty", "Sixty",
        "Seventy", "Eighty", "Ninety"
    };
    
    vector<string> below20{
        "", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight",
        "Nine", "Ten", "Eleven", "Twelve", "Thirteen", "Fourteen",
        "Fifteen", "Sixteen", "Seventeen", "Eighteen", "Nineteen",
    }; 

    const int bn=1000000000;
    const int mn=   1000000;
    const int th=      1000;
    const int hd=       100;
    const int tn=        10;
    
    string tostr(int num) {
        int d;
        
        if(num>=bn) {
            d=num/bn;
            return tostr(d) + " Billion" + tostr(num-d*bn);
        }
        if(num>=mn) {
            d=num/mn;
            return tostr(d) + " Million" + tostr(num-d*mn);
        }
        if(num>=th) {
            d=num/th;
            return tostr(d) + " Thousand" + tostr(num-d*th);
        }
        if(num>=hd) {
            d=num/hd;
            return tostr(d) + " Hundred" + tostr(num-d*hd);
        }
        else if(num>=20) {
            d=num/tn;
            return " "+below100[d]+tostr(num-d*tn);
        }
        else if(num>=1) {
            return " " + below20[num];
        }
        else {
            return "";
        }
        
    }    
    
    string numberToWords(int num) {
        if(num==0) return "Zero";
        return tostr(num).substr(1);
    }
  
};
```
