### Question-1

- [Defanging an IP Address](https://leetcode.com/problems/defanging-an-ip-address/description/)

- topic - `string`

- #### Approach

1. Create a StringBuilder object to store the defanged IP address.
2. Iterate over each character in the input address string.
3. If the current character is not a dot ('.'), append it to the StringBuilder object.
4. If the current character is a dot ('.'), append the string "[.]" to the StringBuilder object.
5. After iterating through all the characters in the input address string, convert the StringBuilder object to a string using the toString() method.
6. Return the defanged IP address string.

- #### Code

```java
    class Solution {
        public String defangIPaddr(String address) {
        StringBuilder builder = new StringBuilder();
        for(int i=0;i<address.length();i++){
            if(address.charAt(i)!='.'){
                builder.append(address.charAt(i));
            }else{
                builder.append("[.]");
            }
        }
        return builder.toString();
        }
}
```

### Question-2

- [Shuffle String](https://google.com)

- topic - `string`

- #### Approach

1. Create a character array array with length n, where n is the length of the indices array.
2. Iterate over the indices array from index 0 to n-1.
3. For each index i, assign the character at index i in the input string s to the corresponding index in the array using indices[i].
4. Convert the array to a string using String.valueOf() method.
5. Return the resulting string.

- #### Code

```java
  class Solution {
    public String restoreString(String s, int[] indices) {
        int n = indices.length;
       char[] array = new char[n];
       for(int i=0;i<n;i++){
           array[indices[i]] = s.charAt(i);
       }
       return String.valueOf(array);
    }
}
```

### Question-3

- [Goal Parser Interpretation](https://leetcode.com/problems/goal-parser-interpretation/description/)

- topic - `string`

- #### Approach

1. Convert the given command string into a character array using toCharArray() method.
2. Create a StringBuilder object to store the modified string.
3. Iterate over each character in the command string using a for loop.
4. If the current character is 'G', append 'G' to the StringBuilder object.
5. If the current character is '(', check the next character:
   - If the next character is ')', append 'o' to the StringBuilder object and increment the loop index by 1.
   - If the next character is 'a', append "al" to the StringBuilder object and increment the loop index by 3.
6. After the loop, convert the StringBuilder object to a string using toString() method and return the modified string.

- #### Code

```java
   class Solution {
    public String interpret(String command) {
       char[] name = command.toCharArray();
       StringBuilder newName = new StringBuilder();
       for(int i=0;i<name.length;i++){
           if(name[i]=='G'){
               newName.append('G');
           }else if (name[i]=='('){
               if(name[i+1]==')'){
                  newName.append('o');
                   i+=1;
               }else if(name[i+1]=='a'){
                   newName.append("al");
                   i+=3;
               }

           }
       }
       return newName.toString();
    }
}
```

### Question-4

- [Sorting the Sentence](https://leetcode.com/problems/sorting-the-sentence/description/)

- topic - `string`

- #### Approach

1. Split the input sentence s into an array of words using space as the delimiter, storing it in the array variable.
2. Create a new array called newArray with the same length as array to store the sorted words.
3. Iterate through each word in the array:
   - Extract the last character of the word using array[i].charAt(array[i].length()-1).
   - Parse the last character as an integer and subtract 1 to get the correct index for the sorted array, storing it in the variable n.
   - Remove the last character from the word using array[i].substring(0,array[i].length()-1).
   - Place the modified word into the newArray at the index n-1.
4. After processing all words, use String.join(" ", newArray) to concatenate the words in the newArray into a single string with space-separated words.
5. Return the sorted sentence.

- #### Code

```java
   class Solution {
    public String sortSentence(String s) {
        String[] array = s.split(" ");
        String[] newArray = new String[array.length];
        for(int i=0;i<array.length;i++){
            int n = Integer.parseInt(String.valueOf(array[i].charAt(array[i].length()-1)));
            newArray[n-1] = array[i].substring(0,array[i].length()-1);
        }
        return String.join(" ",newArray);
    }
}
```

### Question-5

- [Check If Two String Arrays are Equivalent](https://leetcode.com/problems/check-if-two-string-arrays-are-equivalent/description/)

- topic - `string`

- #### Approach

1. The code defines a method called arrayStringsAreEqual that takes two arrays of strings, word1 and word2, as input.

2. It creates two StringBuilder objects, str1 and str2, initialized with the result of joining the strings in word1 and word2, respectively, into a single string without any separators.

3. The code then compares the two resulting strings using the equals method and returns true if they are equal and false otherwise.

4. In essence, the method checks if the concatenation of strings in word1 is equal to the concatenation of strings in word2.

- #### Code

```java
    class Solution {
    public boolean arrayStringsAreEqual(String[] word1, String[] word2) {
        StringBuilder str1 = new StringBuilder(String.join("",word1));
        StringBuilder str2 = new StringBuilder(String.join("",word2));
        return str1.toString().equals(str2.toString());
    }
}
```

### Question-6

- [To Lower Case](https://leetcode.com/problems/to-lower-case/description/)

- topic - `string`

- #### Approach

  - Approach - 1

    1. Input: The code takes a string s as input.

    2. StringBuilder: It initializes a StringBuilder named builder to efficiently build the resulting string.

    3. Loop: It iterates through each character of the input string s using a for loop.

    4. Character Check: Within the loop, it checks if the current character is an uppercase letter (A-Z).

    5. Conversion: If the character is uppercase, it converts it to lowercase by adding 32 to its ASCII value and then appends the lowercase character to the builder.

    6. Appending: If the character is not an uppercase letter, it appends the original character to the builder.

    7. Result: Finally, it returns the resulting string obtained from the builder after processing all characters in the input string.

  - Approach - 2:
    1. Use the builtin string method to convert string to lowercase.

- #### Code

- Approach - 1

  ```java
      class Solution {
      public String toLowerCase(String s) {
          StringBuilder builder = new StringBuilder();
          for(int i=0;i<s.length();i++){
              if(s.charAt(i)>='A' && s.charAt(i)<='Z'){
                  char ch = (char)(s.charAt(i)+32);
                  builder.append(ch);
              }else{
                  builder.append(s.charAt(i));
              }
          }
          return builder.toString();
      }
  }
  ```

- Approach - 2
  ```java
  class Solution {
      public String toLowerCase(String s) {
          return s.toLowerCase();
      }
  }
  ```

### Question-7

- [Determine if String Halves Are Alike](https://leetcode.com/problems/determine-if-string-halves-are-alike/description/)

- topic - `strings`

- #### Approach

1. Calculate the middle index of the input string s.
2. Initialize two counters, count1 and count2, to keep track of the number of vowels in the first and second halves of the string.
3. Iterate through the first half of the string (from index 0 to mid-1):
   - Check each character in this half to see if it is a vowel (both uppercase and lowercase).
   - If a vowel is found, increment count1.
4. Iterate through the second half of the string (from index mid to the end):
   - Check each character in this half to see if it is a vowel (both uppercase and lowercase).
   - If a vowel is found, increment count2.
5. Finally, compare count1 and count2 to determine if the number of vowels in the first half is equal to the number of vowels in the second half.
6. Return true if the counts are equal, indicating that the halves of the string have the same number of vowels, and false otherwise.

- #### Code

```java
    class Solution {
    public boolean halvesAreAlike(String s) {
        int mid = s.length()/2;
        int count1 = 0, count2 = 0;
        for(int i=0;i<mid;i++){
            char ch = s.charAt(i);
            if(ch=='a' || ch=='e' || ch=='i' || ch=='o' || ch=='u' || ch=='A' || ch=='E' ||  ch=='I' || ch=='O' || ch=='U'){
                count1 ++;
            }
        }
        for(int i=mid;i<s.length();i++){
            char ch = s.charAt(i);
            if(ch=='a' || ch=='e' || ch=='i' || ch=='o' || ch=='u' || ch=='A' || ch=='E' ||  ch=='I' || ch=='O' || ch=='U'){
                      count2 ++;
            }
        }
        return count1==count2;
    }
}
```

### Question-8

- [Length of Last Word](https://leetcode.com/problems/length-of-last-word/description/)

- topic - `string`

- #### Approach

1. The code defines a method called lengthOfLastWord that takes a string s as input and returns an integer.

2. It trims the input string s using the trim method. This removes any leading and trailing whitespace from the string.

3. The trimmed string is then split into an array of words using the split method with a space (" ") as the delimiter. This effectively separates the input string into an array of words.

4. The code returns the length of the last word in the array of words. It does this by accessing the last element of the array (at index arr.length-1) and then calculating its length using the length method.

- #### Code

```java
    class Solution {
    public int lengthOfLastWord(String s) {
        String[] arr = s.trim().split(" ");
        return arr[arr.length-1].length();
    }
}
```

### Question-9

- [Number of Strings That Appear as Substrings in Word](https://leetcode.com/problems/number-of-strings-that-appear-as-substrings-in-word/description/)

- topic - `string`

- #### Approach

1. The function numOfStrings takes two parameters: an array of strings patterns and a string word.

2. It initializes a variable count to 0 to keep track of the number of patterns found in the word.

3. It enters a loop that iterates through each element in the patterns array using an index variable i.

4. Inside the loop, it checks if the word contains the current pattern from the patterns array by using the indexOf method. If the pattern is found (i.e., indexOf returns a value not equal to -1), it increments the count variable.

5. Finally, the function returns the value of count, which represents the number of patterns found in the word.

- #### Code

```java
   class Solution {
    public int numOfStrings(String[] patterns, String word) {
        int count = 0;
        for(int i=0;i<patterns.length;i++){
            if(word.indexOf(patterns[i])!=-1){
                count++;
            }
        }
        return count;
    }
}
```

### Question-10

- [Robot Return to Origin](https://leetcode.com/problems/robot-return-to-origin/description/)

- topic - `string`

- #### Approach

1. The code defines a public method named judgeCircle that takes a single argument moves, which is a string representing a sequence of moves.

2. Two integer variables, x and y, are initialized to 0. These variables will be used to track the current position.

3. A for loop iterates through each character in the moves string.

4. Inside the loop, the code checks the current character:

   - If it's 'U', it increments the y variable (moving up).
   - If it's 'D', it decrements the y variable (moving down).
   - If it's 'L', it increments the x variable (moving left).
   - If it's 'R', it decrements the x variable (moving right).

5. After processing all the moves, the code checks if both x and y are equal to 0. If they are, it returns true, indicating that the moves result in returning to the starting position. Otherwise, it returns false.

- #### Code

```java
    class Solution {
    public boolean judgeCircle(String moves) {
        int y = 0, x = 0;
        for(int i=0;i<moves.length();i++){
            if(moves.charAt(i)=='U'){
                y++;
            }else if(moves.charAt(i)=='D'){
                y--;
            }
            if(moves.charAt(i)=='L'){
                x++;
            }else if(moves.charAt(i)=='R'){
                x--;
            }
        }
        if(x==0 && y==0){
            return true;
        }
        return false;
    }
}
```
