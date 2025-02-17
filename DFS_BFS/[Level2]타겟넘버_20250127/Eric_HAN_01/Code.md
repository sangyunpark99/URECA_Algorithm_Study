```java
package NM;

public class A0217_1 {
    int answer;

    public int solution(int[] numbers, int target) {

        dfs(0, 0, numbers, target);
        return answer;
    }

    public void dfs(int depth, int sum, int[] numbers, int target) {
        if (depth == numbers.length) {
            if (sum == target) {
                answer++;
            }
            return;
        }
        dfs(depth + 1, sum + numbers[depth], numbers, target);
        dfs(depth + 1, sum - numbers[depth], numbers, target);

    }
}

```
![스크린샷 2025-02-17 오전 9.48.24.png](%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202025-02-17%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%209.48.24.png)