# Love Babbar Java Sheet

### Find kth smallest element from array :
```
import java.util.*;

public class Main {
    public static int kthMax(TreeMap<Integer,Integer> mp, int k){
        int freq=0;
        for(Map.Entry it: mp.entrySet()){
            freq+= (int)it.getValue();
            if(freq>=k){
                return (int)it.getKey();
            }
        }
        return 0;
    }
    public static void main(String[] args) {
        int[] arr = {12, 3, 4, 15, 7, 6, 8};
        int k=3;
        int n=arr.length;
        TreeMap<Integer,Integer> mp=new TreeMap<>();
        for(int i=0;i<n;i++){
            mp.put(arr[i], mp.getOrDefault(arr[i], 0) + 1); 
        }
        int ans=kthMax(mp,k);
        System.out.print(ans);
    }
}

```
### Reverse a Array :
```
 public static int kthMax(int[] arr, int n){
    int i=0;
    int j=arr.length-1;
    while(i<j){
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
        i++;
        j--;
     }    
 }
```
### Find kth max element from array :

We use priority queue because according to prioroty we do (FIFO) and use max Heap. In max Heap which element is max that element delete first means out first. But In java here implement minHeap. 

If you pass a comparator to the constructor , then It will be convert from minHeap to maxHeap in java.
```
PriorityQueue<Integer> pq= new PriorityQueue<>(Collections.reverseOrder());
```
Here reverseOrder is a function who return your comparator. Who return reverse order of comparatorof natural ordering of integer (ascending order).


```
import java.util.*;

public class Main {
    public static int kthMax(int[] arr, int k){
       PriorityQueue<Integer> pq=new PriorityQueue<>();
       for(int i=0;i<k;i++){
           pq.add(arr[i]);
       }
       for(int i=k;i<arr.length;i++){
          if(pq.peek()<arr[i]){                         // firstly make min heap size 3, like 12, 3, 4 then compare min heap peak element
              pq.poll();                                // is < than arr[i] then pop minheap peak and add arr[i] in minhead
              pq.add(arr[i]);                           // Last pop minheap peak element 
          }
       }
       return pq.peek();
    }
    public static void main(String[] args) {
        int[] arr = {12, 3, 4, 15, 7, 6, 8};
        int k=3;
        int ans=kthMax(arr,k);
        System.out.print(ans);
        
    }
}

```
