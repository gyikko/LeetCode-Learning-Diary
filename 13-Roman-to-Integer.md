# 13. Roman to Integer

- Date: 02/19/2021 
- Language: Java
- [Question Link](https://leetcode.com/problems/roman-to-integer/)
- Rather simple question. No need to use any data structures, just pure logic.

```java
class Solution {
    public int romanToInt(String s) {
        int length = s.length();
        int result = 0;
        char previous = 'a';
        
        for(int i=0; i<length; i++){
            char c = s.charAt(i);
            result += translate(c);
            if(c=='V' && previous=='I'){
                result -= 2;
            }
            if(c=='X' && previous=='I'){
                result -= 2;
            }
            if(c=='L' && previous=='X'){
                result -= 20;
            }
            if(c=='C' && previous=='X'){
                result -= 20;
            }
            if(c=='D' && previous=='C'){
                result -= 200;
            }
            if(c=='M' && previous=='C'){
                result -= 200;
            }
            previous = c;
        }
        return result;
    }
    
    public int translate(char c){
        if(c == 'I'){
            return 1;
        } else if(c == 'V'){
            return 5;
        } else if(c == 'X'){
            return 10;
        } else if(c == 'L'){
            return 50;
        } else if(c == 'C'){
            return 100;
        } else if(c == 'D'){
            return 500;
        } else if(c == 'M'){
            return 1000;
        }
        
        return 0;
    }
}
```

- Runtime: 3 ms (>99.91%)
- Memory Usage: 38.9 MB (<93.85%)
- Utilized: Pure logic
