```java
import java.io.*;
import java.util.*;

class Solution {
    
    private static int[][] map = new int[102][102];
    private static boolean[][] visited;
    private static int[][] delta = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}, {-1, -1}, {-1, 1}, {1, -1}, {1, 1}};
    private static int cnt;
    
    public int solution(int[][] rectangle, int characterX, int characterY, int itemX, int itemY) {
        
        for(int i =0; i < rectangle.length; i++) {
            
            for(int x = rectangle[i][0] * 2; x <= rectangle[i][2] * 2; x++ ) {
                for(int y = rectangle[i][1] * 2; y <= rectangle[i][3] * 2; y++) {
                    map[x][y] = 1;
                }
            }
            
        }
        
       
        
        changeOutline();
        
        bfs(characterX*2, characterY*2, itemX*2, itemY*2);
        return cnt / 2;
    }
    
    private static void changeOutline() {
        
        Queue<int[]> q = new ArrayDeque<>();
        q.offer(new int[] {0, 0});
        visited = new boolean[102][102];
        
        while(!q.isEmpty()) {
            
            int[] curr = q.poll();
            
            for(int i = 0; i < 8; i++) {
                
                int nr = curr[0] + delta[i][0];
                int nc = curr[1] + delta[i][1];
                
                
                if(nr >= 0 && nr < 102 && nc >= 0 && nc < 102 && visited[nr][nc] == false) {
                    
                    if(map[nr][nc] == 1){
                        
                        map[nr][nc] = 2;
                        
                        
                    } 
                    else{
                        q.offer(new int[] {nr, nc});
                    }
                    visited[nr][nc] = true;
                    
                }
                
            }
            
        }
        
    }
    
    private static void bfs(int sx, int sy, int ex, int ey) {
        
        visited = new boolean[102][102];
        
        Queue<int[]> q = new ArrayDeque<>();
        q.offer(new int[]{sx, sy, 0});
        
        while(!q.isEmpty()) {
            
            int[] curr = q.poll();
            
            if(curr[0] == ex && curr[1] == ey) {
                cnt = curr[2];
                return;
            }
            
                
            for(int i = 0; i<4; i++) {

                int nr = curr[0] + delta[i][0];
                int nc = curr[1] + delta[i][1];

                if(nr >= 0 && nr < 102 && nc >= 0 && nc < 102 && !visited[nr][nc] && map[nr][nc] == 2) {


                    visited[nr][nc] = true;
                    q.offer(new int[]{nr, nc, curr[2] + 1});

    

                }

            }
                
            
        }
        
    }
    
}
```
