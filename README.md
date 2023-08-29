# Love Babbar Java Sheet

## Find kth smallest element from array :
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

## Reverse a Array :
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
## Find kth max element from array :

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
## Sort an array of 0s, 1s and 2s

```
import java.util.*;

public class Main {
    public static void main(String[] args) {
        int[] arr = {2,0,1,1,2,0,2,0,0,1};
        int zero=0;
        int one=0;
        int two=0;
        int i=0;
        while(i<arr.length){
            if(arr[i]==0){
                zero++;
            }
            else if(arr[i]==1){
                one++;
            }
            else{
                two++;
            }
            i++;
        }
        i=0;
        while(i<zero){
            arr[i]=0;
            i++;
        }
        while(i<zero+one){
            arr[i]=1;
            i++;
        }
        while(i<zero+one+two){
            arr[i]=2;
            i++;
        }
        System.out.print(Arrays.toString(arr));
        
    }
}
```
## Move all negative numbers to beginning and positive to end with constant extra space
```
Input: -12, 11, -13, -5, 6, -7, 5, -3, -6
Output: -12 -13 -5 -7 -3 -6 11 6 5

import java.util.*;
public class Main
{
	public static void main(String[] args) {
	int[] arr= { -12, 11, -13, -5, 6, -7, 5, -3, -6};
// 	System.out.print(Arrays.toString(arr));
	int i=0;
	int j=arr.length-1;
	while(i<=j){
	    if(i<arr.length && arr[i] < 0){
	        i++;
	    }
	    if(j>=0 && arr[j]>=0){
	        j--;
	    }
	    if(i<j){
	        int temp=arr[i];
	        arr[i]= arr[j];
	        arr[j]=temp;
	    }
	}
	System.out.print(Arrays.toString(arr));
	}
}

```
## Union & Intersection of two arrays

```

Input: arr1 -  1 2 3 4 5
       arr2 -	1 2 3

output: 1 2 3 4 5

import java.util.*;
public class Main
{
	public static void main(String[] args) {
	int[] arr1= { 1,2,3,4,5};
	int[] arr2 = {1,2,3};
            HashSet<Integer> hs= new HashSet<>();
            for(int num : arr1){
                hs.add(num);
            }
            for(int num : arr2){
                hs.add(num);
            }
            
            int[] res= new int[hs.size()];
            int i=0;
            for(int num : hs){
                res[i++]=num;
             }
            
      System.out.print(Arrays.toString(res));
   }
 }

```
Intersection of two array
```
Input: arr1 -  1 2 3 4 5
       arr2 -	1 2 3

output: 1 2 3 

import java.util.*;
public class Main
{
	public static void main(String[] args) {
	int[] arr1= { 1,2,3,4,5};
	int[] arr2 = {1,2,3};
    HashSet<Integer> hs= new HashSet<>();
    HashSet<Integer> res= new HashSet<>();
    for(int num : arr1){
        hs.add(num);
    }
    for(int num : arr2){
        if(hs.contains(num)){
            res.add(num);
        }
        
    }
        int[] result = new int[res.size()];
        int i = 0;
        for (int num : res) {
            result[i++] = num;
        }
    
	System.out.print(Arrays.toString(result));
	}
}
```

## Cyclically rotate an array by one
```
import java.util.*;
public class Main
{
	public static void main(String[] args) {
	int[] arr= { 6,2,3,4,5};
	int rotateOne= arr[arr.length-1];
    for (int i = arr.length - 1; i > 0; i--) {
            arr[i] = arr[i - 1];
        }
	arr[0]=rotateOne;
	System.out.print(Arrays.toString(arr));
	}
}
```
## Find largest sum contiguous of array:
```
import java.util.*;
public class Main
{
	public static void main(String[] args) {
    int arr[] = {1,2,3,-2,5};
     int sum=arr[0];
        int maxValue=arr[0];
        for(int i=1;i<arr.length;i++){
           int maxV1 = Math.max(arr[i],sum+arr[i]);
            maxValue= Math.max(maxValue,maxV1);
        }
        System.out.print(maxValue);
	}
}
```

## Minimize the min Heights difference of tower

```
class Solution {
    int getMinDiff(int[] arr, int n, int k) {
        
        Arrays.sort(arr);
        int diff=arr[n-1]-arr[0];
        int min=0;
       int max=0;
        for(int i=1;i<n;i++){
            if(arr[i]-k<0){
                continue;
            }
            max= Math.max(arr[i-1]+k, arr[n-1]-k);
            min= Math.min(arr[0]+k, arr[i]-k);
            diff=Math.min(diff,max-min);
        }
        return diff;
    }
}

Input:
K = 2, N = 4
Arr[] = {1, 5, 8, 10}
Output:
5
Explanation:
The array can be modified as 
{1+k, 5-k, 8-k, 10-k} = {3, 3, 6, 8}. 
The difference between 
the largest and the smallest is 8-3 = 5.

```

## Minimum number of jumps

```
import java.util.*;

public class Main {
    public static void main(String[] args) {
        int[] arr = {2, 3, 1, 1, 4}; // Example array
        int result = minJumps(arr);
        System.out.println("Minimum number of jumps: " + result);
    }
    
    public static int minJumps(int[] arr) {
        if (arr.length <= 1) {
            return 0; // No jumps needed for an array of size 1 or less
        }
        
        if (arr[0] == 0) {
            return -1; // Cannot move from the first element itself
        }
        
        int n = arr.length;
        int jumps = 1;
        int currentReach = arr[0];
        int maxReach = arr[0];
        
        for (int i = 1; i < n; i++) {
            if (i == n - 1) {
                return jumps; // Reached the end of the array
            }
            
            maxReach = Math.max(maxReach, i + arr[i]);
            
            if (i == currentReach) {
                if (maxReach <= currentReach) {
                    return -1; // Cannot proceed further
                }
                jumps++;
                currentReach = maxReach;
            }
        }
        
        return -1; // Could not reach the end of the array
    }
}

```
## Find Duplicate value from an Array

```
import java.util.*;
public class Main
{
	public static void main(String[] args) {
	    int[] nums= {1,2,6,3,2};
		System.out.println("Hello World");
	 HashMap<Integer,Integer> hm=new HashMap<>();

        int count=0;
        for(int i=0;i<nums.length;i++){
            hm.put(nums[i],hm.getOrDefault(nums[i],0)+1);

        }
       for (Map.Entry<Integer, Integer> entry : hm.entrySet()) {
            if (entry.getValue() > 1) {
                System.out.println("Key: " + entry.getKey() + " has duplicate value.");
            }
        }    
	}
}
```
## Merge Two Sorted Array
```
import java.util.*;
public class Main
{
	public static void main(String[] args) {
	    int[] arr1={1, 5, 9, 10, 15, 20};
	    int arr2[] = {2, 3, 8, 13};
	    int n=arr2.length;
	    int m= arr1.length;
	     for (int i = n - 1; i >= 0; i--) {
         
            int j, last = arr1[m - 1];
            for (j = m - 2; j >= 0 && arr1[j] > arr2[i];j--)
                arr1[j + 1] = arr1[j];
 
            // If there was a greater element
            if (last > arr2[i]) {
                arr1[j + 1] = arr2[i];
                arr2[i] = last;
            }
        }
        System.out.print(Arrays.toString(arr1));
        System.out.print(Arrays.toString(arr2));
	
	}
}

```

