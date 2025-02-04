```java
import java.io.*;
import java.util.*;

class Solution {
    
    private static int N, M;
    private static char[] charArr;
    private static Set<Integer> nums = new HashSet<>();
    private static int visited;
    private static char[] result;
    
    public int solution(String numbers) {
        
        charArr = dividing(numbers);
        N = numbers.length();
        
        for(int i = 1; i <= charArr.length; i++) {
            
            M = i;
            visited = 0;
            result = new char[M];
            StringBuilder sb = new StringBuilder();
            dfs(0, sb);
            
        }
        
        int answer = nums.size();
        return answer;
    }
    
    private static void dfs(int depth, StringBuilder sb) {
        
        if(depth == M) {
            if(isPrime(sb.toString())) {
                nums.add(Integer.parseInt(sb.toString()));
            }
            
        }else {
            for(int i = 0; i < N; i++) {
                
                if((visited & (1<<i)) == 0) {
                    visited |= (1<<i);
                    dfs(depth+1, sb.append(charArr[i]));
                    visited ^= (1<<i);
                    sb.deleteCharAt(depth);
                } 
                
            }
        }
        
    }
    
    private static boolean isPrime(String str) {
        int num = Integer.parseInt(str);
        
        if(num <= 1) return false;
        
        for(int i = 2; i<num; i++) {
            if(num % i == 0) return false;
        }
        
        return true;
        
    }
    
    
    private static char[] dividing(String numbers) {
        
         char[] charArr = new char[numbers.length()];
        for(int i = 0; i<numbers.length(); i++) {
            charArr[i] = numbers.charAt(i);
        }
        
        return charArr;
        
    }
}

```
