**problem:Trapping Rain Water**

If we consider a subarray arr[left...right], we can decide the amount of water either for arr[left] or arr[right] if we know the left max (max element in arr[0...left-1]) and right max (max element in arr[right+1...n-1].
If left max is less than the right max, then we can decide for arr[left]. Else we can decide for arr[right]
If we decide for arr[left], then the amount of water would be left max - arr[left] and if we decide for arr[right], then the amount of water would be right max - arr[right].



**code**

    class Solution {
    public int maxWater(int arr[]) {
        // code here
        int left=1;
        int right=arr.length-2;
        int lMax=arr[left-1];
        int rMax=arr[right+1];
        int res=0;
        while(left<=right){
            if(rMax <= lMax){
                res += Math.max(0,rMax - arr[right]);
                rMax = Math.max(rMax, arr[right]);
                right -= 1;
            }else{
                res += Math.max(0,lMax - arr[left]);
                lMax = Math.max(lMax, arr[left]);
                left += 1;
                
            }
        }
        return res;
        
    }
    }
