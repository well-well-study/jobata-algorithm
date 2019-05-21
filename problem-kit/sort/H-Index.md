# sort

## H-Index

### 문제

[https://programmers.co.kr/learn/courses/30/lessons/42747](https://programmers.co.kr/learn/courses/30/lessons/42747)

### 풀이
```java
import java.util.ArrayList;
import java.util.Collections;

class Solution {
    public int solution(int[] citations) {
        int answer = 0;
        ArrayList<Integer> arrayList = new ArrayList<>();
        for (int i : citations) {
            arrayList.add(i);
        }
        Collections.sort(arrayList);
        Collections.reverse(arrayList);
        for (int i = 0; i < arrayList.size() + 1; i++) {
            if(i == arrayList.size()) {
                answer = i;
            } else if (arrayList.get(i) <= i){
                answer = i;
                break;
            }
        }
        return answer;
    }
}
```

```java
import java.util.*;

class Solution {
    public int solution(int[] citations) {
        Arrays.sort(citations);

        int max = 0;
        for(int i = citations.length-1; i > -1; i--){
            int min = (int)Math.min(citations[i], citations.length - i);
            if(max < min) max = min;
        }

        return max;
    }
}
```

### 추가

if (citations.Min() >= citations.Length)
return citations.Length;
