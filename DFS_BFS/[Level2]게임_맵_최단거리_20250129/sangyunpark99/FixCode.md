```java
import java.util.*;

class Solution {
    
    private int[][] Maps;
    private int[][] visited;
    private int[] dy = {-1,0,1,0};
    private int[] dx = {0,1,0,-1};
    private int n;
    private int m;
    
    public int solution(int[][] maps) {
        Maps = maps;
        n = maps.length;
        m = maps[0].length;
        visited = new int[n][m];

        bfs();
        
        return visited[n-1][m-1] == 0 ? -1 : visited[n-1][m-1];
    }
    
    public void bfs() {
        int startY = 0;
        int startX = 0;
        visited[startY][startX] = 1;
        
        Queue<int[]> queue = new LinkedList<>();
        queue.add(new int[]{0,0});
        
        while(!queue.isEmpty()) {
            int[] curPosition = queue.poll();
            int curY = curPosition[0];
            int curX = curPosition[1];
            
            for(int i = 0; i < 4; i++) {
                int ny = curY + dy[i];
                int nx = curX + dx[i];
                
                if(ny < 0 || ny >= n || nx < 0 || nx >= m || Maps[ny][nx] == 0 || visited[ny][nx] != 0) continue;
                
                visited[ny][nx] = visited[curY][curX] + 1;
                
                queue.add(new int[]{ny, nx});   
            }
        }
    }
}
```
### 오답 노트
이전 코드에선 조건문을 아래와 같이 해주고, Math.min을 사용해서 지속적으로 최솟값을 갱신해주는 방식을 사용했다.  
```java
 if(ny < 0 || ny >= n || nx < 0 || nx >= m || Maps[ny][nx] == 0 || visited[ny][nx] != Integer.MAX_VALUE) continue;v
```
이렇게 해줄 필요가 없다.  
```
A->B->D->E
0    1    2     3

A->C->E
0    1    2
```
이 경우를 예시로 들면 BFS내부 로직의 Queue에 들어가는 순서는 다음과 같다.
[A,B,C,D,E,E] E지점을 도착지점이라 가정했을 때, E지점에 먼저 도착한 순간 visited의 값은 변경된다.  
bfs에서 방문 조건은 한번도 방문하지 않을때만 가능하다. 아래와 같은 조건문 때문이다. 이말은 곧 visited가 갱신되는 시점이 최단경로라는 의미를 가진다.  
```java
visited[ny][nx] != 0
```
