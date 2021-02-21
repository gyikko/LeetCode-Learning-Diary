# 13. Roman to Integer

- Date: 02/19/2021 
- Language: Java
- [Question Link](https://leetcode.com/problems/roman-to-integer/)

### Approach 1
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

### Approach 2
- Use HasMap to do the calculation. Change the calculating logic for 4, 9, 40, 90, 400, 900 situations.
```java
  class Solution {
      public int romanToInt(String s) {
          Map <Character, Integer> calculator = new HashMap<>();
          calculator.put('I', 1);
          calculator.put('V', 5);
          calculator.put('X', 10);
          calculator.put('L', 50);
          calculator.put('C', 100);
          calculator.put('D', 500);
          calculator.put('M', 1000);

          int length = s.length();
          int result = 0;

          for(int i=0; i<length; i++){
              if((i+1<length) && (calculator.get(s.charAt(i)) < calculator.get(s.charAt(i+1)))){
                  result -= calculator.get(s.charAt(i));
              } else {
                  result += calculator.get(s.charAt(i));         
              }
          }        
          return result;
      }
  }
```
