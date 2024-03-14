# Java Virtual Machine (JVM)
- JVM은 Java가 OS에 구애받지 않고 실행할 수 있게 해주는 자바 가상 머신이다.
- OS를 대신하여 컴파일 된 Java 바이트 코드(.class)를 실행하는 가상 운영체제 역할을 하기 때문에 Java는 플랫폼에 의존적이지 않다.
  > .class 파일은 사람이 쓰는 자바 코드에서 컴퓨터가 읽는 기계어
- 하지만 JVM은 플랫폼에 의존적이기 때문에 OS에 맞는 JVM을 설치해야 한다.

## 특징

- 스택 기반의 가상 머신
- 심볼릭 레퍼런스
- 가비지 컬렉션(GC)
- 기본 자료형을 명확하게 정의하여 플랫폼 독립성 보장

## 실행과정

1. 프로그램이 실행되면 JVM은 OS로부터 이 프로그램이 필요로 하는 메모리를 할당받는다.
   - JVM은 이 메모리를 용도에 따라 여러 영역으로 나누어 관리한다.
2. 자바 컴파일러(javac)가 자바 소스코드(.java)를 읽어들여 자바 바이트코드(.class)로 변환시킨다.
3. Class Loader를 통해 class 파일들을 JVM으로 로딩한다.
4. 로딩된 class 파일들은 Execution engine을 통해 해석된다.
5. 해석된 바이트 코드는 Runtime Data Areas에 배치되어 실질적인 수행이 이루어지게 된다.
6. 이러한 실행과정 속에서 JVM은 필요에 따라 Thread Synchronization과 GC같은 관리작업을 수행한다.

## 구조
1. 클래스 로더 (Class Loader)
2. 실행 엔진 (Execution Engine)
3. 메모리 영역 (Memory Areas)