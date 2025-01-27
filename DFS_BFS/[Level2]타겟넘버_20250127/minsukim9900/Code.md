```java
class Solution {
    
    private static int[] result;
    private static int[] nums;
    private static int cnt, compNum;
    
    public int solution(int[] numbers, int target) {
        nums = numbers;
        compNum = target;
        result = new int[nums.length];
        
        dfs(0);
        return cnt;
    }
    
    private static void dfs(int depth){
    
    if(depth == nums.length){
        
        if(isTrue()){
            cnt++;
        }
        
        
    }else{
        
        for(int i = 0; i<2; i++) {
            
            result[depth] = i;
            dfs(depth+1);
            
        }
        
    }
    
}

private static boolean isTrue(){
    int sum = 0;
    
    for(int i = 0; i<result.length; i++){
        
        if(result[i] == 0){
            sum -= nums[i];
        }else{
            sum += nums[i];
        }
        
    }
    
    if(sum == compNum) return true;
    return false;
    
}
}
```
