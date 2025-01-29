```java
import java.io.*;
import java.util.*;

class Solution {
    
    private static int[][] delta = {{-1,0},{1,0},{0,-1},{0,1} };
    
    public int solution(int[][] maps) {
        int n = maps.length;
        int m = maps[0].length;
        int answer = bfs(maps, n, m);
        return answer;
    }
    
    private static int bfs(int[][] maps, int n, int m) {
        
        int[][] visited = new int[n][m];
        
        Queue<int[]> q = new ArrayDeque<>();
        visited[0][0] = 1;
        q.offer(new int[]{0, 0, 1});
        
        while(!q.isEmpty()) {
            
            int[] curr = q.poll();
            
            if(curr[0] == n-1 && curr[1] == m-1) {
                return curr[2];
            }
            
            
            for(int i = 0; i < 4; i++) {
                
                int nr = curr[0] + delta[i][0];
                int nc = curr[1] + delta[i][1];
                
                if(nr >= 0 && nr < n && nc >= 0 && nc < m && maps[nr][nc] == 1 && visited[nr][nc] == 0) {
                    
                    visited[nr][nc] = curr[2]+1;
                    q.offer(new int[] {nr, nc, curr[2]+1});
                    
                }
                
            }
            
            
        }
        
        return -1;
        
    }
}
```

