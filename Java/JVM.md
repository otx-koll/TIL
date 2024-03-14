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


## 구조
1. 클래스 로더 (Class Loader)
2. 실행 엔진 (Execution Engine)
3. 메모리 영역 (Memory Areas)