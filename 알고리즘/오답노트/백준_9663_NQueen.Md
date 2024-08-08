# 백준 [9663] N-Queen


### 🍰 문제 설명
🧸 [문제 바로가기](https://www.acmicpc.net/problem/9663)

퀸이 서로를 공격할 수 없는 위치에 놓는 경우의 수<br/>

### 🥨 접근 방식

1. 퀸의 움직임을 생각해볼 것
2. 2차원 배열로 체스판을 구현할 것

### 🍪 틀린 이유
1. 2차원 배열로 하다보니 빠진 로직이 있었던 것 같다.

### 🧁 올바른 접근 방식 및 해결 방식

1. 퀸은 상하좌우 및 대각선으로 거리 제한 없이 한 방향으로 이동이 가능
2. 1차원 배열로 Index를 열, 원소 값을 행이라고 생각하기
3. 퀸을 놓을 수 있는 위치라면 퀸을 놓고 다음 퀸 위치 찾기 (재귀호출)
4. 행을 다 채웠다면 경우의 수를 하나 올리기


```java
 private static void nQueen(int cnt){
        if(cnt == N) {
            count++;
            return;
        }

        for (int i=0; i<N; i++){
            map[cnt] = i;
            if(Possible(cnt)) {
                nQueen(cnt+1);
            }
        }
    }
```
> 퀸을 놓은 재귀 함수 <Br/>
> 행을 다 채우면 한 가지 경우의 수를 완성 한것 <Br/>
> 퀸을 놓을 수 있다면 놓고 다음 자리를 탐색


```java

    private static boolean Possible(int col) {
        for(int i=0; i<col; i++) {
            if(map[col] == map[i]) {
                return false;
            }

            else if(Math.abs(col-i) == Math.abs(map[col] - map[i])){
                return false;
            }
        }
        return true;
    }

```

> 퀸을 놓을 수 있는 곳인지 확인하는 함수 <br/>
> 같은 행에 퀸을 놓을 수 없음 <br/>
> 열의 차와 행의 차가 같을 경우 대각선에 놓여있 는 것이므로 불가능