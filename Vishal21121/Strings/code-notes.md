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
