``` java
import java.io.*;
import java.util.*;

class Solution {
    
    public int solution(int[][] triangle) {
        
            int size = triangle.length;
            
            for (int i = 1; i< size; i++) {
                
                triangle[i][0] += triangle[i-1][0];
                triangle[i][triangle[i].length-1] += triangle[i-1][triangle[i].length-2];
                
                for(int j = 1; j < i; j++) {
                    
                    triangle[i][j] += Math.max(triangle[i-1][j-1], triangle[i-1][j]);
                    
                }
                
            }
            
        
        int max = 0;
        for(int m : triangle[size - 1]) {
            max = Math.max(max, m);
        }
        
        return max;
       
    }
    
    
}
```

[!img.png](img.png)