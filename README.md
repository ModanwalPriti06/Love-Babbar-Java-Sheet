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
