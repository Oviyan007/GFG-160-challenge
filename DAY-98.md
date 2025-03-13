**Code**




    class Solution {
    public ArrayList<Double> getMedian(int[] arr) {
        PriorityQueue<Integer> leftMaxHeap=new PriorityQueue<>((a,b)->b - a);
        PriorityQueue<Integer> rightMinHeap=new PriorityQueue<>();
        ArrayList<Double> res=new ArrayList<>();
        for(int i=0;i<arr.length;i++){
            leftMaxHeap.add(arr[i]);
            int temp=leftMaxHeap.poll();
            rightMinHeap.add(temp);
            if(rightMinHeap.size() > leftMaxHeap.size()){
                temp=rightMinHeap.poll();
                leftMaxHeap.add(temp);
            }
            double median;
            if(leftMaxHeap.size() != rightMinHeap.size())
                median=leftMaxHeap.peek();
            else
                median=(leftMaxHeap.peek() + rightMinHeap.peek())/2.0;
            res.add(median);
        }
        return res;
        
        // code here
    }
    }
