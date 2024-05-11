### Question-1

- [Count Digits](https://www.geeksforgeeks.org/problems/count-digits5716/1)

- topic - `maths`

- #### Approach

  1. The method `evenlyDivides` takes an integer `N` as input and returns the count of digits of `N` that evenly divide `N`.
  2. It initializes two variables, `count` and `temp`.

  - `count` is used to store the count of digits that evenly divide `N`.
  - `temp` is a temporary variable initialized with the value of `N`.

  3. It enters a while loop that continues as long as `temp` is greater than 0.

  4. Inside the loop:

  - It extracts the last digit of `temp` using the modulo operator `%` and assigns it to the variable `lastNum`.
  - It checks if `lastNum` is not equal to 0 and if the remainder of `N` divided by `lastNum` is equal to 0. If both conditions are true, it increments the `count` variable.

  5. After checking the last digit, it updates the value of `temp` by dividing it by 10, effectively removing the last digit.

  6. The loop continues until `temp` becomes 0.

  7. Finally, it returns the value of `count`, which represents the count of digits of `N` that evenly divide `N`.

- #### Code

```java
    class Solution{
    static int evenlyDivides(int N){
       int count = 0;
        int temp = N;
        while(temp>0){
            int lastNum = temp % 10;
            if(lastNum != 0 && N % lastNum == 0){
                count++;
            }
            temp = temp /10;
        }
        return count;
    }
}
```

### Question-2

- [Palindrome Number](https://leetcode.com/problems/palindrome-number/description/)

- topic - `maths`

- #### Approach

  - `isPalindrome` method:

    1. The method `isPalindrome` takes an integer `x` as input and returns a boolean value indicating whether `x` is a palindrome or not.

    2. It first checks if `x` is negative. If `x` is negative, it immediately returns `false` because negative numbers cannot be palindromes.

    3. If `x` is non-negative, it calls the `reverseNum` method to reverse `x` and assigns the reversed number to `reversedNum`.

    4. It then returns `true` if `reversedNum` is equal to `x`, indicating that `x` is a palindrome, and `false` otherwise.

  - `reverseNum` method:

    1. The method `reverseNum` takes an integer `N` as input and returns the reverse of `N`.

    2. It initializes two variables, `temp` and `finalVal`.

    - `temp` is a temporary variable initialized with the value of `N`.
    - `finalVal` is used to store the reversed number.

    3. It enters a while loop that continues as long as `temp` is greater than 0.

    4. Inside the loop:

    - It extracts the last digit of `temp` using the modulo operator `%` and assigns it to the variable `lastNum`.
    - It updates `finalVal` by multiplying it by 10 and adding `lastNum`. This effectively builds the reversed number digit by digit.
    - It updates the value of `temp` by dividing it by 10, effectively removing the last digit.

    5. The loop continues until `temp` becomes 0.

    6. Finally, it returns the value of `finalVal`, which represents the reverse of the input number `N`.

- #### Code

```java
    class Solution {
    public boolean isPalindrome(int x) {
        if(x<0){
            return false;
        }
        int reversedNum = reverseNum(x);
        return reversedNum == x;
    }
    static int reverseNum(int N){
        int temp = N;
        int finalVal = 0;
        while(temp>0){
            int lastNum = temp % 10;
            finalVal = finalVal * 10 + lastNum;
            temp = temp /10;
        }
        return finalVal;
    }
}
```

### Question-3

- [Check Armstrong](https://www.naukri.com/code360/problems/check-armstrong_589?leftPanelTabValue=PROBLEM)

- topic - `maths`

- #### Approach

1. The program starts by importing the `Scanner` class, which is used for getting user input.

2. The `Main` class is defined, which contains the `main` method, the entry point of the program.

3. Inside the `main` method:

   - A `Scanner` object named `in` is created to read input from the standard input stream (`System.in`).
   - An integer variable `num` is declared and assigned the value entered by the user using `in.nextInt()`.
   - Another integer variable `temp` is declared and assigned the value of `num`. This is done to preserve the original value of `num` for later comparison.
   - An integer variable `sum` is declared and initialized to 0. This variable will hold the sum of each digit raised to the power of the number of digits in the input number.
   - An integer variable `length` is declared and assigned the length of the input number converted to a string using `Integer.toString(num).length()`. This is done to determine the number of digits in the input number.

4. A `while` loop is used to iterate through each digit of the input number (`num`):

   - Inside the loop, the remainder (`rem`) of dividing `num` by 10 (i.e., the last digit of `num`) is calculated using the modulus operator `%`.
   - The sum is updated by adding the result of raising `rem` to the power of `length` using `Math.pow(rem, length)`.
   - The last digit is removed from `num` by integer division (`num /= 10`), which effectively shifts the number to the right, removing the last digit.

5. After the loop, the program checks if the original input number (`temp`) is equal to the calculated sum (`sum`):

   - If they are equal, it means the input number is an Armstrong number (a number that is equal to the sum of its own digits raised to the power of the number of digits). In this case, it prints `true`.
   - If they are not equal, it means the input number is not an Armstrong number. In this case, it prints `false`.

6. The program terminates.

- #### Code

```java
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
		int num = in.nextInt();
		int temp = num;
		int sum = 0;
		int length = Integer.toString(num).length();
		while(num > 0){
            int rem = num % 10;
            sum = (int) (sum + Math.pow(rem,length));
            num /= 10;
        }
		if(temp == sum){
			System.out.println(true);
		}else{
			System.out.println(false);
		}
	}
}

```
