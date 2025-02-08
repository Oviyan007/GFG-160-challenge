Day 74 of GFG 160 Challenge: LRU Cache Implementation
🔹 Problem Statement
Design a Least Recently Used (LRU) Cache that supports get(key) and put(key, value) operations in O(1) time.

get(key) → Return the value if the key exists, otherwise return -1.
put(key, value) → Insert or update the value of the key. If the cache reaches capacity, remove the least recently used key before inserting.

🔹 Efficient Approach: HashMap + Doubly Linked List
Data Structures Used: ✔ HashMap (key → node) → To access nodes in O(1) time.




**code**

    class LRUCache {
    // Constructor for initializing the cache capacity with the given value.
    private int capacity;
    private Map<Integer,Integer> cacheMap;
    private LinkedList<Integer>lruList;
    LRUCache(int capacity) {
        // code here
        this.capacity=capacity;
        this.cacheMap=new HashMap<>();
        this.lruList=new LinkedList<>();
    }

    // Function to return value corresponding to the key.
    public  int get(int key) {
        // your code here
        if(!cacheMap.containsKey(key)){
            return -1;
        }
        lruList.remove(Integer.valueOf(key));
        lruList.addFirst(key);
        return cacheMap.get(key);
    }

    // Function for storing key-value pair.
    public  void put(int key, int value) {
        // your code here
        if(cacheMap.containsKey(key)){
            cacheMap.put(key,value);
            lruList.remove(Integer.valueOf(key));
        }
        else{
            if(cacheMap.size()>=capacity){
                int leastUsedKey=lruList.removeLast();
                cacheMap.remove(leastUsedKey);
            }
            cacheMap.put(key,value);
        }
        lruList.addFirst(key);
    }  
    }
