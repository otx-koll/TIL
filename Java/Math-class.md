# Math 클래스
- java.Lang 패키지에 포함된 클래스
- 수학과 관련된 작업들을 처리할 수 있는 클래스
- Math 클래스의 모든 메소드는 static으로 구현되어 있으므로 따로 인스턴스를 생성하지 않고도 바로 사용 가능하다.

## 메소드
메소드|타입|설명
|-|-|-|
랜덤값(0~1사이)<br>Math.random()|static double random()|0.0 이상 1.0 미만의 범위에서 임의의 double형 값을 하나 생성하여 반환함
절대값<br>Math.abs(param)|static double abs(double a)<br>static double abs(float a)<br>static double abs(int a)<br>static double abs(long a)<br>|전달된 값이 음수이면 그 값의 절댓값을 반환하며, 전달된 값이 양수이면 인수를 그대로 반환함
Math.ceil(param)|static double ceil(double a)|전달된 double형 값의 소수 부분이 존재하면 소수 부분을 무조건 올리고 반환함
Math.floor(param)|static double floor(double a)|전달된 double형 값의 소수 부분이 존재하면 소수 부분을 무조건 버리고 반환함
Math.round(param)|static long round(double a)<br>static int round(float a)|전달된 값을 소수점 첫째 자리에서 반올림한 정수를 반환함
Math.rint(param)|static double rint(double a)|전달된 double형 값과 가장 가까운 정수값을 double형으로 반환함
Math.max(param1, param2)|static double max(double a, double b)<br>static float max(float a, float b)<br>static long max(long a, long b)<br>static int max(int a, int b)|전달된 두 값을 비교하여 큰 값을 반환함
Math.min(param1, param2)|static double min(double a, double b)<br>static float min(float a, float b)<br>static long min(long a, long b)<br>static int min(int a, int b)|전달된 두 값을 비교하여 작은 값을 반환함
Math.pow(param1, param2)|static double pow(double a, double b)|전달된 두 개의 double형 값을 가지고 제곱 연산을 수행하여, ab을 반환함
Math.sqrt(param)|static double sqrt(double a)|전달된 double형 값의 제곱근 값을 반환함
Math.sin(param)<br>Math.cos(param)<br>Math.tan(param)|static double sin(double a)<br>static double cos(double a)<br>static double tan(double a)|전달된 double형 값에 해당하는 각각의 삼각 함숫값을 반환함

## Reference

https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html

http://www.tcpschool.com/java/java_api_math
