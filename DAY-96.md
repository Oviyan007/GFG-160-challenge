**Code**

    class Solution {
    static int squareDis(int[] point){
        return point[0]*point[0]+point[1]*point[1];
    }
    public int[][] kClosest(int[][] points, int k) {
        // Your code here
        PriorityQueue<int[]> maxHeap =new PriorityQueue<>((a,b) -> squareDis(b)-squareDis(a));
        for(int[] point:points){
            if(maxHeap.size()<k){
                maxHeap.offer(point);
            }else{
                if(squareDis(point)< squareDis(maxHeap.peek())){
                    maxHeap.poll();
                    maxHeap.offer(point);
                }
            }
        }
        int [][] res=new int[k][2];
        int index=0;
        while(!maxHeap.isEmpty()){
            int[] point=maxHeap.poll();
            res[index][0]=point[0];
            res[index][1]=point[1];
            index++;
        }
        return res;
    }
    }
