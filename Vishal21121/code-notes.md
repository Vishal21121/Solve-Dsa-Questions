## Arrays

### Question-1

- [Count Frequency in a range](https://www.codingninjas.com/studio/problems/count-frequency-in-a-range_8365446?leftPanelTab=0)

- topic - `arrays` `HashMap`

- #### Approach
    - Initialised the map with element of the nums array as key and occurrence as the value.
    - Iterated the nums array and checked whether the element is there in map if yes then increase the count by one and if not then make it `one`.
    - Then iterate from 1 to n and check whether the ith number is there in the map if yes then store the occurrence in the array `arr` and if not then store zero in the array `arr` at that index.

- #### Code
```java
    import java.util.HashMap;

    public class Solution {
        public static int[] countFrequency(int n, int x, int []nums){
        HashMap<Integer,Integer> map = new HashMap<>();
            for(int i=0;i<n;i++){
                map.put(nums[i],map.getOrDefault(nums[i], 0)+1);
            }
            int[] arr = new int[n];
            for(int i=1;i<=n;i++){
                if(map.containsKey(i)){
                    arr[i-1] = map.get(i);
                }else{
                    arr[i-1] = 0;
                }
            }
            return arr;
        }
    }
```

### Question-2

- [Sum of second largest in even position and second smallest number in odd position](https://prepinsta.com/accenture-coding-question-2/)

- topic - `arrays`

- #### Approach
    - Initialised large, secLarge with `Integer.MIN_VALUE`, small and secSmall with `Integer.MAX_VALUE` value
    - Iterated till the array length and checked if the position is even or odd
    - If even then check whether the number is greater than large if yes then assign secLarge with large value and assign large with `arr[i]`
    - If odd then check whether the number is smaller than small if yes then assign secSmall with smalll value and assign small with `arr[i]`
    - Finally return the sum of `secLarge` and `secSmall`.

- #### Code
```java
    public class SumOfSecondSmallestAndSecondLargest {
    public static void main(String[] args) {
        int[] arr = new int[]{1,8,0,2,3,5,6};
        System.out.println(sum(arr));
    }
    static int sum(int[] arr){
        int large=Integer.MIN_VALUE,secLarge=Integer.MIN_VALUE, small=Integer.MAX_VALUE, secSmall=Integer.MAX_VALUE;
        for(int i=0;i<arr.length;i++){
            if(i%2==0){
                if(arr[i]>large){
                    secLarge = large;
                    large = arr[i];
                }else if(arr[i]>secLarge && arr[i]!=large){
                    secLarge = arr[i];
                }
            }else{
                if(arr[i]<small){
                    secSmall = small;
                    small = arr[i];
                }else if(arr[i]<secSmall && arr[i]!=small){
                    secSmall = arr[i];
                }
            }
        }
        return secLarge + secSmall;
    }
}

```

> Note: The time complexity of the above approach is O(n) + O(n) which is O(2n) ignoring the constant it is O(n)

### Question-3

- [Terms Of AP](https://www.codingninjas.com/studio/problems/terms-of-ap_9065116?challengeSlug=ninja-slayground)

- topic - `arrays`

- #### Approach
    - Initialised `count = 0`, `j=1` and created and array `arr` with the size of x (as we have to store the x elements which are not divisble by 4)
    - Iterated while loop until count becomes x and checked if the number in the series is divisible 4 if not then add the number in the array and increase the count
    - finally return this array.

- #### Code
```java
    import java.util.* ;
    import java.io.*; 
    public class Solution {
        public static int[] termsOfAP(int x){
            int count = 0;
            int j = 1;
            int[] arr = new int[x];
            while(count!=x){
                if((3*j+2)%4!=0){
                    arr[count] = 3*j+2;
                    count++;
                }
                j++;
            }
            return arr;
        }
    }

```
### Question-4

- [Selection Sort](https://www.codingninjas.com/studio/problems/selection-sort_624469?leftPanelTab=0)

- topic - `arrays` `sorting`

- #### Approach
    - we need to itearate for n-1 pass where (n= array's length)
    - In each iteration we will find the min number index from the array start=i to end=n-1 and then we will swap the min number with the i index.
    - So after each iteration we will have sorted array towards the left of i index.
  ![img.png](img.png)

- #### Code
```java
    import java.util.Arrays;

    public class SelectionSort {
      public static void main(String[] args) {
        int[] arr = new int[]{5};
        selectionsort(arr,arr.length);
        System.out.println(Arrays.toString(arr));
      }
      static void selectionsort(int[] arr, int n){
        for(int i=0;i<n-1;i++){
          int minIndex = minIndex(arr,i,n);
          int temp = arr[minIndex];
          arr[minIndex] = arr[i];
          arr[i] = temp;
        }
      }
      static int minIndex(int[] arr, int start, int end){
        int minIndex = start;
        for(int i=start;i<end;i++){
          if(arr[i]<arr[minIndex]){
            minIndex = i;
          }
        }
        return minIndex;
      }
    
    }


```

#### Note:
- **Time complexity: O(N2)**, (where N = size of the array), for the best, worst, and average cases. 
- **Space Complexity: O(1)**,

> Reason: If we carefully observe, we can notice that the outer loop, say i, is running from 0 to n-2 i.e. n-1 times, and for each i, the inner loop j runs from i to n-1. For, i = 0, the inner loop runs n-1 times, for i = 1, the inner loop runs n-2 times, and so on. So, the total steps will be approximately the following: (n-1) + (n-2) + (n-3) + ……..+ 3 + 2 + 1. The summation is approximately the sum of the first n natural numbers i.e. (n*(n+1))/2. The precise time complexity will be O(n2/2 + n/2). Previously, we have learned that we can ignore the lower values as well as the constant coefficients. So, the time complexity is O(n2). Here the value of n is N i.e. the size of the array.

### Question-5

- [Bubble Sort](https://www.codingninjas.com/studio/problems/bubble-sort_624380)

- topic - `arrays` `sorting`

- #### Approach
   - Iterated the array for n-1 passes (n=array length)
   - Used the second loop to iterate the array till second last element of the unsorted part of the array.
   - boolean swap variable is used to check whether the array is sorted or not if the array is sorted then we do not have to run the second loop for every pass so in the first pass no swapping occurs then it means that array is sorted hence break the loop.
   - for dry run and more detailed explanation [visit](https://takeuforward.org/data-structure/bubble-sort-algorithm/)

- #### Code
```java

public class Solution {
  public static void bubbleSort(int[] arr, int n) {
    boolean swap = false;
    for(int i=1;i<n;i++){
      swap = false;
      for(int j=0;j<=n-1-i;j++){
        if(arr[j]>arr[j+1]){
          int temp = arr[j];
          arr[j] = arr[j+1];
          arr[j+1]=temp;
          swap = true;
        }

      }
      if(!swap){
        break;
      }
    }
  }

}
```

#### Note:
- Time complexity
    - O(n^2) for worst and average case
    - O(n) for best case ( and it happens when array is sorted )
- Space Complexity
  - O(1)

### Question-6

- Insertion Sort

- topic - `arrays` `sorting`

- #### Approach
  - Iterate for n pass where n is the length of the array.
  - Iterate from ith element towards the left in inner loop while checking that j-1 element should be smaller than jth element if not then go inside the loop and swap until the jth element is at the correct index.

- #### Code
```java
import java.util.Arrays;

public class InsertionSort {
    public static void main(String[] args) {
        int[] arr = new int[]{1,2,3,4,5};
        insertionSort(arr,arr.length);
        System.out.println(Arrays.toString(arr));
    }
    static void insertionSort(int[] arr,int n){
        for(int i=0;i<n;i++){
            int j=i;
            while(j>0 && arr[j-1]>arr[j]){
                int temp = arr[j];
                arr[j] = arr[j-1];
                arr[j-1] = temp;
                j--;
            }
        }
    }
}

```

#### Note:
- Time complexity
  - O(n^2) for worst and average case
  - O(n) for best case ( if the array is sorted )
- Space complexity
  - O(1) 




