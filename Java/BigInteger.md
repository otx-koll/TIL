int의 메모리 범위를 벗어나게 되면 모두 0으로 출력이 된다. 웬만하면 잘 벗어나진 않지만 항상 최악의 상황을 고려해야하므로 무한으로 들어갈 가능성이 있다면 BigInteger 클래스를 사용하는 것이 좋다.

# BigInteger
문자열 형태로 이루어져 있어 숫자의 범위가 무한하기 때문에 어떠한 숫자든 담을 수 있다.

## 사용법
### 선언
```java
import java.math.BigInteger;

BigInteger bigNumber = new BigInteger("10010");
```

### 연산
```java
BigInteger bigNumber1 = new BigInteger("100000");
BigInteger bigNumber2 = new BigInteger("10000");

bigNumber1.add(bigNumber2)); // 덧셈
bigNumber1.subtract(bigNumber2)); // 뺄셈
bigNumber1.multiply(bigNumber2)); // 곱셈
bigNumber1.divide(bigNumber2)); // 나눗셈
bigNumber1.remainder(bigNumber2)); // 나머지(%)
```

### 형 변환
```java
BigInteger bigNumber = BigInteger.valueOf(100000); //int -> BigIntger

int int_bigNum = bigNumber.intValue(); //BigIntger -> int
long long_bigNum = bigNumber.longValue(); //BigIntger -> long
float float_bigNum = bigNumber.floatValue(); //BigIntger -> float
double double_bigNum = bigNumber.doubleValue(); //BigIntger -> double
String String_bigNum = bigNumber.toString(); //BigIntger -> String
```

### 두 수 비교
```java
BigInteger bigNumber1 = new BigInteger("100000");
BigInteger bigNumber2 = new BigInteger("1000000");

// 맞으면 0 틀리면 -1
int compare = bigNumber1.compareTo(bigNumber2);
```



