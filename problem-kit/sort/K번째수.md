# sort

## K번째수

### 문제

[https://programmers.co.kr/learn/courses/30/lessons/42748](https://programmers.co.kr/learn/courses/30/lessons/42748)

### 풀이
```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int length = commands.length;
        int[] answer = new int[length];
        for(int index = 0; index < length; index++) {
            int[] data = new int[array.length];
            for(int i = 0; i < array.length; i++) {
                data[i] = array[i];
            }
            int i = commands[index][0];
            int j = commands[index][1];
            int k = commands[index][2];
            Arrays.sort(data, i - 1, j);
            answer[index] = data[i - 1 + k - 1];
        }
        return answer;
    }
}
```

```java
import java.util.Arrays;
class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];

        for(int i=0; i<commands.length; i++){
            int[] temp = Arrays.copyOfRange(array, commands[i][0]-1, commands[i][1]);
            Arrays.sort(temp);
            answer[i] = temp[commands[i][2]-1];
        }

        return answer;
    }
}
```

### 추가

Arrays.copyOf(original, newLength) 

-> 인자값 : 원본 배열, 복사할 길이

Arrays.copyOfRange(original, from, to)

-> 인자값 : 원본 배열, 복사 시작할 위치, 복사 끝낼 위치 

으로도 해결가능하다.

값에 의한 복사이므로 복사된 배열에서 값을 바꿔도 원본 배열의 값이 바뀌지 않는다.
