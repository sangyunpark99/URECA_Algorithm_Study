``` java
class Solution {
    public int[] solution(int brown, int yellow) {
        int[] answer = new int[2];

        for(int i = 3; i <= (brown + yellow); i++) {
            int length = (brown + yellow) / i;
            if((length - 2) * (i - 2) == yellow) {
                answer[0] = length;
                answer[1] = i;
                break;
            }
        }

        return answer;
    }
}
```
![스크린샷 2025-02-11 오후 4.14.17.png](%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202025-02-11%20%EC%98%A4%ED%9B%84%204.14.17.png)
