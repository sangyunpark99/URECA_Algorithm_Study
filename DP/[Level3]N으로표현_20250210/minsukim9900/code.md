``` java
import java.io.*;
import java.util.*;

class Solution {
    
    private static Set<Integer>[] dp = new Set[9];
    
    public int solution(int N, int number) {
        
        for(int i = 1; i<=8; i++) {
            dp[i] = new HashSet<>();
        }
        
        int tmp = 0;
        for(int i = 0; i<8; i++) {
            tmp = tmp * 10 + N;
            dp[i+1].add(tmp);
        }
        
        for(int i = 2; i<=8; i++) {
            for(int j = 1; j<i; j++) {
                
                int idx = i - j;
                
                for(int x : dp[j]) {
                    for(int y : dp[idx]) {
                        
                        dp[i].add(x + y);
                        dp[i].add(x - y);
                        dp[i].add(x * y);
                        if(y != 0){
                         dp[i].add(x / y);   
                        }
                        
                    }
                }
                
            }
            
        }
        
        for(int i = 1; i<=8; i++) {
            if(dp[i].contains(number)) return i;
        }
        
        
        return -1;
        
    }
}
```
[img.png](img.png)