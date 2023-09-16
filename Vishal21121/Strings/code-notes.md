### Question-1

<!-- question name within [] and link within () -->

- [Defanging an IP Address](https://leetcode.com/problems/defanging-an-ip-address/description/)

- topic - `string`

- #### Approach

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
