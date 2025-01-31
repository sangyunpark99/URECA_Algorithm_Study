```java
import java.io.*;
import java.util.*;

class Solution {
    
    private static List<String>[] adj;
    private static boolean[] visited;
    private static HashMap<String, Integer> info = new HashMap<>();
    
    public int solution(String begin, String target, String[] words) {
        
        
        adj = new ArrayList[words.length+1];
        for(int i = 0; i < words.length+1; i++) {
            adj[i] = new ArrayList<>();
        }
        
        init(begin, words);
        
        visited = new boolean[words.length+1];
        
        
        
        
        return bfs(begin, target, words);
    }
    
    private static boolean isCorrect(String word, String comp) {
        
        int cnt = 0;
        
        for(int i = 0; i< word.length() ; i++) {
           if(word.charAt(i) != comp.charAt(i)) cnt++;   
        }
        
        if(cnt > 1) return false;
        
        return true;
        
        
    }
    
    private static void init(String begin, String[] words) {
        
        for(int i = 0; i < words.length; i++) {
            
            if(isCorrect(begin, words[i])) {
                adj[0].add(words[i]);
            }
        
        }
        
        for(int i = 0; i<words.length; i++) {
            
            for(int j = 0; j<words.length; j++) {
                
                if(i == j) continue;
                
                if(isCorrect(words[i], words[j])) {
                    adj[i+1].add(words[j]);
                }
            
            }
        }
        
        info.put(begin, 0);
        
        for(int i = 0; i<words.length; i++) {
            info.put(words[i], i+1);
        }
        
    }
    
    private static int bfs(String begin, String target, String[] words) {
        
        Queue<Word> q = new ArrayDeque<>();
        
        q.offer(new Word(begin, 0));
        visited[0] = true;
        
        while(!q.isEmpty()) {
            
            Word curr = q.poll();
            
            if(curr.w.equals(target)) {
                return curr.cnt;
            }
            
            int idx = info.get(curr.w);
            
            for(String s : adj[idx]) {
                if(!visited[info.get(s)]){
                    visited[info.get(s)] = true;
                    q.offer(new Word(s, curr.cnt+1));
                }
            }
            
            
        }
        
        return 0;
        
        
    }
    
    private static class Word {
        
        private String w;
        private int cnt;
        
        private Word(String w, int cnt) {
            this.w = w;
            this.cnt = cnt;
        }
        
    }
    
    
}
```
