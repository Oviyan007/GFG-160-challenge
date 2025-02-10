Day 76 of GFG 160 Challenge: program to calculate pow(b, e)

Approach:

The idea is to use Divide and Conquer and recursively bisect e in two equal parts. There are two possible cases:
If e is even: power(b, e) = power(b, e / 2) * power(b, e / 2);
If e is odd: power(b, e) = b * power(b, e / 2) * power(b, e / 2);

**code**

      class Solution {
    double power(double b, int e) {
        // code here
        if(e==0)
            return 1;
        if(e<0)
            return 1/power(b,-e);
        double temp=power(b,e/2);
        if(e%2==0)
            return temp*temp;
        else
            return b*temp*temp;
    }
    }
