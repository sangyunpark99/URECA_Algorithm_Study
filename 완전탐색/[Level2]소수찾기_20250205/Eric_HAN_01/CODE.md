``` java
package a0207;

import java.util.HashSet;

public class A1_Solution {
    private char [] arr;
    private boolean[] check;
    private HashSet<Integer> set;

    public int solution(String number) {
        arr = number.toCharArray();
        check = new boolean[number.length()];
        set = new HashSet<>();

        dfs("",0);
        return set.size();
    }

    private void dfs(String str, int depth) {
        if (depth == check.length) {
            if(str.equals("")){
                return;
            }
            int temp = Integer.parseInt(str);
            if(isPrime(temp)){
                set.add(temp);
            }
            return;
        }

        for (int i = 0; i < arr.length; i++) {
            if(!check[i]){
                check[i] = true;
                dfs(str + arr[i], depth + 1);
                check[i] = false;
                dfs(str, depth + 1);
            }

        }

    }

    private boolean isPrime(int num) {
        if (num < 2) return false;
        for (int i = 2; i < num; i++) { //아니 왜? 제곱이 안돼? ㅁㄴ아리ㅓ니ㅏㅇ러ㅏㅣㄴㅁ어린ㅁㅇㄹ
            if (num % i == 0) {
                return false;
            }
        }
        return true;
    }
}

``` 
![스크린샷 2025-02-11 오전 10.01.24.png](%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202025-02-11%20%EC%98%A4%EC%A0%84%2010.01.24.png)
