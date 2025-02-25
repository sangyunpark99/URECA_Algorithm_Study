```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    static int []dx = {-1, 1, 0, 0};
    static int []dy = {0, 0, -1, 1};
    static int [][] visited;
    static int [][] maps;

    public int solution(int[][] maps) {
        this.maps = maps;
        visited = new int[maps.length][maps[0].length];
        bfs(0,0);
        return visited[maps.length - 1][maps[0].length - 1] == 0 ? -1 : visited[maps.length - 1][maps[0].length - 1];
    }

    public void bfs(int row, int col) {
        Queue<int[]> q = new LinkedList<>();
        q.add(new int[]{row, col});
        visited[row][col] = 1;

        while(!q.isEmpty()) {
            int[] cur = q.poll();
            for(int i = 0; i < 4; i++){
                int x = cur[0] + dx[i];
                int y = cur[1] + dy[i];

                if(x < 0 || y < 0 || x >= maps.length || y >= maps[0].length) {
                    continue;
                }

                
                if(maps[x][y] == 1 && visited[x][y] == 0){
                    visited[x][y] = visited[cur[0]][cur[1]] + 1;
                    q.add(new int[]{x, y});
                }
            }

        }

    }
}

```

![스크린샷 2025-02-24 오전 10.48.41.png](%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202025-02-24%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2010.48.41.png)