# 동적 계획법(DP : Dynamic Programming)
- 큰 문제를 작은 문제로 나누어 그 답을 저장해두고 재활용하여 푸는 문제이다.
- 일반적으로 재귀를 사용할 시 동일한 작은 문제들이 여러번 반복되어 비효율적일 수 있다. 그러나 작은 문제의 결과 값을 저장해두고 재사용한다면 앞에 계산된 값을 반복할 필요가 없어지기 때문에 계산 속도를 높일 수 있다.

## 사용 조건
1. Overlapping Subprobelms(중복 부분 문제)
   - 동일한 작은 문제가 반복되는 경우
   - 문제가 반복되지 않는다면 재사용이 불가능하니 문제가 중복되지 않을 경우 사용할 수 없다.
2. Optimal Substructure(최적 부분 구조)
   - 작은 문제의 최적 결과 값을 구한 후, 그것을 이용하여 큰 문제의 최적 결과를 낼 수 있는 경우
   - 같은 문제는 구할 때 마다 정답이 같다.

## 구현 단계
1. 문제를 하위 문제로 쪼개기
2. 하위 문제를 재귀적으로 해결
3. 결과를 저장 (메모이제이션)
4. 저장된 결과를 이용하여 큰 문제를 해결

## 종류
1. Bottom-up
   - 작은 문제부터 큰 문제까지 차례대로 해결해 나가는 방식
   - 반복문을 사용하여 작은 문제들을 해결하고, 결과를 배열 등에 저장하여 나중에 동일한 문제가 발생했을 때 다시 계산하지 않고 저장된 값을 사용하여 시간을 절약한다.
 
```markup
Bottom-up 방식으로 피보나치 수열 계산하기

1. memo\[0]과 memo\[0\1]은 초기값으로 설정
2. i가 2부터 n까지 반복문을 통해 memo[i] = memo[i-1] + memo[i-2]로 값을 계산하고 저장 (메모이제이션)
3. 이를 통하여 n번째 항의 값을 반환
```
```java
public int fibonacci(int n) {
    if (n <= 1) {
        return n;
    }
    int[] memo = new int[n+1];
    memo[0] = 0;
    memo[1] = 1;
    for (int i = 2; i <= n; i++) {
        memo[i] = memo[i-1] + memo[i-2];
    }
    return memo[n];
}
```

2. Top-down
   - 큰 문제를 작은 문제로 나누어 해결하는 방식
   - 재귀 함수를 사용하여 문제를 작은 문제로 쪼개고, 중복 계산을 피하기 위해 이전 결과 값을 저장하는 메모이제이션을 활용한다.

```markup
Top-down 방식으로 피보나치 수열 계산하기

- dp 배열을 메모이제이션용으로 사용하여 이전의 결과 값을 저장하고 중복 계산을 방지 (메모이제이션)
- n이 1보다 작거나 같은 경우 n을 반환, 그 외의 경우 fib(n-1)과 fib(n-2)를 더한 값을 dp 배열에 저장한 후 반환
```
```java
public class TopDownDP {
    static int[] dp = new int[100];

    public static int fib(int n) {
        if (n <= 1) {
            return n;
        }
        if (dp[n] != 0) { // 메모이제이션
            return dp[n];
        }
        dp[n] = fib(n - 1) + fib(n - 2);
        return dp[n];
    }
}
```

> 단순 재귀를 통해 피보나치 수열을 구하는 경우

```java
public static int RecursionFb(int n) {
    if (n <= 1) {
        return n;
    } else {
        return RecursionFb(n - 1) + RecursionFb(n - 2);
    }
}
```

### Divide and Conquer(분할 정복)와 차이점

분할 정복은 분할된 하위 문제가 동일하게 중복이 일어나지 않는 경우에 쓰고, 동일한 중복이 일어나면 동적 프로그래밍을 쓴다.
