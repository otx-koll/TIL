동적계획법의 핵심이 되는 기술이다. 한 번 계산한 결과를 캐시(Cache)에 저장해두었다가 같은 값이 입력되면 저장해둔 결과 값을 다시 꺼내씀으로써 중복 계산을 방지할 수 있는 기법이다.

## 구현
대표적으로 피보나치를 구할 때 
```java
static int[] arr = new int[100]; // 저장해둘 배열 선언

static int fib(int n) {
	if (n <= 1) {
		return n;
	}
	if (arr[n] != 0) {
		return arr[n];
	}
	arr[n] = fib(n - 1) + fib(n - 2);
	return arr[n];
}
```
재귀를 이용하기보단 메모이제이션을 이용하여 구하는 것이 시간이 확 줄어든다. **(시간복잡도 : O(n))**