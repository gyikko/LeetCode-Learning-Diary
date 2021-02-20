# 7. Reverse Integer

- Date: 02/19/2021 
- Language: Java
- [Question Link](https://leetcode.com/problems/reverse-integer/)
- Rather simple question. No need to use any data structures, just pure math logic.

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
