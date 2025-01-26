```java
class Solution {
    
    static int[] Numbers;
    static int Target;
    
    public int solution(int[] numbers, int target) {
        
        Numbers = numbers;
        Target = target;

        return dfs(0, 0);
    }
    
    private int dfs(int curValue, int curIdx) {
        
        int answer = 0;
        
        if(curIdx == Numbers.length) {
            
            if(curValue == Target) {
                answer++;        
            }
            
            return answer;
        }
        
        answer = dfs(curValue + Numbers[curIdx], curIdx+1) + dfs(curValue - Numbers[curIdx], curIdx+1);
        
        return answer;
    }
}
```

