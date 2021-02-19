# 1. Two Sum

- Date: 02/18/2021 
- Language: Java
- [Question Link](https://leetcode.com/problems/two-sum/)

### Approach 1
Brutal solution -> loop in loop
- Time complexity: `O(n^2)`

### Approach 2
Use `HashMap` to store keys (elements in the array) and values (elements' index).
Find another key to make the sum with current key is equal to target is faster in
`HashMap`. The result will be the values based on the keys.
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map <Integer, Integer> map = new HashMap<>();
        for(int i=0; i<nums.length; i++){
            map.put(nums[i],i);
        }
        
        for(int i=0; i<nums.length; i++){
            int a = nums[i];
            int b = target-a;
            if(map.containsKey(b) && map.et(b)!=i){
                return new int[]{i, map.get(b)};
            }
        }
        
        throw new IllegalArgumentException("no result");
    }
}
```

- Runtime: 2 ms (>31.66%)
- Memory Usage: 39.1 MB (<61.96%)
