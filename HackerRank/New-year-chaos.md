## New year chaos
https://www.hackerrank.com/challenges/new-year-chaos/problem

### 정답
- 처음엔 오름차순으로 정렬되어있음 
- 새치기는 2번 이상 할 수 없으며, 만약 그런경우에는 chaos 리턴 
- 처음에는 입력 리스트 index 에서 리스트 value 를 빼줘서 2 이하 차이가 나면 swap 되었다고 단순하게 생각했으나 처리하지 못하는 케이스들이  발생
- 다른 사람의 답 보고 이해했음 
    -  결과적으로 숫자가 뒤에 숫자보다 큰 경우 swap 한걸로 이해하면 됨

```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {

    // Complete the minimumBribes function below.
    static void minimumBribes(int[] q) {
        int bribes_number = 0;
        for (int i = q.length; i < 0; i --) {
            int temp = q[i] - (i + 1);
            if (temp > 2) {
                System.out.println("Too chaotic");
                return;
            } else {
                for(int j = i; j < temp; j++) {
                    if(q[j] > q[i]){
                        bribes_number += 1;
                    }
                }
            }
        }
        
        System.out.println(bribes_number);
    }

    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        int t = scanner.nextInt();
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        for (int tItr = 0; tItr < t; tItr++) {
            int n = scanner.nextInt();
            scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

            int[] q = new int[n];

            String[] qItems = scanner.nextLine().split(" ");
            scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

            for (int i = 0; i < n; i++) {
                int qItem = Integer.parseInt(qItems[i]);
                q[i] = qItem;
            }

            minimumBribes(q);
        }

        scanner.close();
    }
}

```