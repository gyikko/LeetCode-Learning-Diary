# 14. Longest Common Prefix

- Date: 02/20/2021 
- Language: Java
- [Question Link](https://leetcode.com/problems/reverse-integer/)


```java
  class Solution {
      public int reverse(int x) {
          long result = 0;

          while(x!=0){
              result = result *10 + x%10;
              x /=10;
          }
          if(result < Integer.MIN_VALUE || result > Integer.MAX_VALUE){
              return 0;
          }
          return (int)result;
      }
  }
```

- Runtime: 1 ms (>100%)
- Memory Usage: 36 MB (<83.26%)
- Utilized: Math logic
