``` java
import java.io.*;
import java.util.*;

class Solution {
    
    private static int[] high;
    private static int[] low;
    
    public int solution(int[][] sizes) {
        
        int n = sizes.length;
        
        high = new int[n];
        low = new int[n];
        
        classify(sizes);
        Arrays.sort(high);
        Arrays.sort(low);
        
        return high[n-1] * low[n-1];
    }
    
    private static void classify(int[][] sizes) {
        
        for(int i = 0; i < sizes.length; i++) {
            int r = sizes[i][0];
            int c = sizes[i][1];
            
            high[i] = Math.max(r, c);
            low[i] = Math.min(r, c);
            
        }
        
    }
    
   
}
```
![스크린샷 2025-02-03 091941](https://github.com/user-attachments/assets/50a91867-4644-4c57-97c5-95ee9e94b374)
