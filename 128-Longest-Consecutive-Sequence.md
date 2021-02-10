# 128. Longest Consecutive Sequence

- Date: 02/09/2021 
- Language: Java
- [Question Link](https://leetcode.com/problems/longest-consecutive-sequence/)
- Since the question require `O(n)` solution. `for-loop` in `for-loop` should not be considered. So, we need a data structure
to store the elements.
### Approach 1
1. Use `HashSet` to store the elements.
2. Search `HashSet` for next consecutive element. If exists, search next one & extend length. If not exist, check if the current 
sequence is the longest & decide the result.

```java
        Set<Integer> set = new HashSet<Integer>();
        
        for(int num:nums){
            set.add(num);
        }
        
        int result = 0;
        for(int num:nums){
            int currNum = 0;
            int currRes = 0;
            if(!set.contains(num-1)){
                currNum = num;  // head of the current sequence
                currRes = 1;
            }
            
            while(set.contains(currNum+1)){  // check for next consecutive element
                currNum = currNum + 1;
                currRes ++;
            }
            
            result = Math.max(result, currRes);
        }
        
        return result;
```

- Runtime: 4 ms (>55.53%)
- Memory Usage: 39.1 MB (<82.45%)
- Utilized: HashSet

### Approach 2
1. Use `HashTable`
