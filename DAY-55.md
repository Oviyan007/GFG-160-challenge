
💡 Day 55 Problem: Count the Number of Possible Triangles

🧠 Approach:
1️⃣ Sort the Array:

Start by sorting the array. This ensures we can leverage the triangle property efficiently.
2️⃣ Triangle Property:

For a triangle to be valid, the sum of any two sides must be greater than the third side.
3️⃣ Two-Pointer Technique:

Fix the largest side of the triangle (arr[k]) by iterating from the end of the array.
Use two pointers (i and j):
i starts at the beginning of the array.
j starts just before k.
Check if arr[i] + arr[j] > arr[k]:
If true, all pairs between i and j form valid triangles with arr[k]. Add (j - i) to the count and decrement j.
If false, increment i to increase the sum.

**code**

    class Solution {
    // Function to count the number of possible triangles.
    static int countTriangles(int arr[]) {
        // code here
        int res=0;
        Arrays.sort(arr);
        for(int i=0;i<arr.length;i++){
            for(int j=i+1;j<arr.length;j++){
                int lo=j+1,hi=arr.length;
                int target=arr[i]+arr[j];
                while(lo<hi){
                    int mid=lo+(hi-lo)/2;
                    if(arr[mid]<target){
                        lo=mid+1;
                    }
                    else{
                        hi=mid;
                    }
                }
                int cnt=lo-j-1;
                res+=cnt;
            }
        }
        return res;
    }
    }
