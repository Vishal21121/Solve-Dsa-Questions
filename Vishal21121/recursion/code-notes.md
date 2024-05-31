# Recursion

### Question-1

- [Find minimum and maximum element in an array](https://practice.geeksforgeeks.org/problems/find-minimum-and-maximum-element-in-an-array4428/1)

- topic - `recursion`

- #### Approach

  1. The code defines a `Pair` class with two long integer fields, `first` and `second`, for storing the minimum and maximum values.
  2. The `Compute` class contains the main logic to find the minimum and maximum values in the given array.

  3. `getMinMax` is a static method that takes an array `a` of long integers and its length `n` as input and returns a `Pair` with the minimum and maximum values.
  4. The method initializes an array `arr` with initial values `Integer.MIN_VALUE` and `Integer.MAX_VALUE`. These are used as initial placeholders for minimum and maximum values.
  5. It then calls the recursive method `getValue` to update the minimum and maximum values in the `arr` array.

  6. `getValue` is a recursive method that iterates through the array and updates the minimum and maximum values in the `ans` array.

  7. The base case for the recursion is when `index` equals `n`, indicating that all elements in the array have been processed.

  8. In each recursive call, the method checks if the element at the current index is greater than the current maximum (stored in `ans[0]`) and updates it if necessary.

  9. Similarly, it checks if the element at the current index is smaller than the current minimum (stored in `ans[1]`) and updates it if necessary.

  10. The recursion continues until all elements have been processed, and the final `ans` array contains the minimum and maximum values.

  11. Finally, the `getMinMax` method returns a `Pair` object with the minimum and maximum values found during the recursive process.

  In summary, the code recursively searches for the minimum and maximum values in the array and returns them as a `Pair` object.

- #### Code

```java
    //User function Template for Java

/*
 class Pair
{
    long first, second;
    public Pair(long first, long second)
    {
        this.first = first;
        this.second = second;
    }
} */

class Compute
{
    static Pair getMinMax(long a[], long n)
    {
        //Write your code here
        long[] arr = {Integer.MIN_VALUE, Integer.MAX_VALUE};
        getValue(a,n,0,arr);
        return new Pair(arr[1],arr[0]);
    }
    static void getValue(long[] arr, long n, int index, long[] ans){
        if(index==n){
            return ;
        }
        if(arr[index] > ans[0]){
            ans[0] = arr[index];
        }
        if(arr[index]<ans[1]){
            ans[1] = arr[index];
        }
        getValue(arr,n,index+1,ans);
    }
}
```

### Question-2

- [Print 1 To N Without Loop](https://www.geeksforgeeks.org/problems/print-1-to-n-without-using-loops-1587115620/1)

- topic - `recursion`

- #### Approach

1. **Method `printNos(int N)`**:

   - Invokes the helper method `printNosHelper` with parameters `N` and `1`.

2. **Method `printNosHelper(int n, int count)`**:

   - **Base Case**: If `count` exceeds `n`, the recursion stops (returns).
   - **Recursive Case**:
     - Print the current value of `count` followed by a space.
     - Recursively call `printNosHelper` with `count` incremented by 1.

3. **Recursive Printing**:

   - The `printNosHelper` method prints numbers from `1` to `N` recursively.

4. **Execution Flow**:
   - Start with `count` as 1.
   - Print the current `count`.
   - Increase `count` by 1 and call the helper method again until `count` exceeds `N`.

This approach uses recursion to print numbers from 1 to N sequentially.

- #### Code

```java
    class Solution
    {

        public void printNos(int N){
            printNosHelper(N,1);
        }

        public void printNosHelper(int n, int count){
            if(count>n){
                return;
            }
            System.out.print(count+ " ");
            printNosHelper(n,count+1);
        }
    }

```

### Question-3

- [Print GFG n times](https://www.geeksforgeeks.org/problems/print-gfg-n-times/1)

- topic - `recursion`

- #### Approach

1. Class Definition: The code defines a class named Solution.

2. printGfg Method:
   1. Signature: void printGfg(int N)
   2. This method is the entry point for printing "GFG ".
   3. It takes an integer N as input.
   4. It calls the printer method with the value of N and an initial index of 1.
3. printer Method:
   1. Signature: void printer(int num, int index)
   2. This method is responsible for printing "GFG " recursively.
   3. It takes two parameters: num, the total number of times to print, and index, the current index.
   4. It checks if the current index is greater than num. If so, it returns, terminating the recursion.
   5. Otherwise, it prints "GFG " and recursively calls itself with index+1.

- #### Code

```java
   class Solution {

    void printGfg(int N) {
       printer(N,1);
    }

    void printer(int num, int index){
        if(index>num){
            return;
        }
        System.out.print("GFG ");
        printer(num,index+1);
    }
}
```
