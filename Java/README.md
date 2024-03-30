# Java Programming
- 교재 : 자바프로그래밍입문(박종은, 이지퍼블리싱)
- OS : ubuntu

## 목차

[시작](#시작)

[변수와 자료형](#변수와-자료형)

## 시작
- 프로그램 : 컴퓨터에게 일을 시키는 명령의 집합
- 컴파일(compile) : 컴퓨터가 이해할 수 있는 언어(기계어)로 번역하는 것
    - 사람이 이해하기 쉬울수록 고급 언어, 컴퓨터가 이해하기 쉬울수록 저급 언어

### 자바를 사용하는 이유

- **플랫폼에 영향을 받지 않으므로 다양한 환경에서 사용할 수 있다**
   - 플랫폼(platform) : 프로그램이 실행되는 환경
   - 자바에서 파일을 만들고 컴파일하면 `.class`파일이 생성된다. 이 파일은 바이트 코드라고 하는데 완벽한 실행 파일이 아니므로 [자바 가상 머신(JVM)](/Java/JVM.md)이 필요하다.
 - **객체 지향 언어이므로 유지보수가 쉽고 확장성이 좋다**
   - 객체 지향 프로그래밍 : 여러 객체의 협력을 통해 프로그램을 구현하는 것
 - **프로그램이 안정적이다**
   - 동적 메모리 수거를 프로그래머가 하지 않고 [가비지 컬렉터(GC)](/Java/Garbage-Collection.md)를 이용하므로 메모리를 효율적으로 관리할 수 있다.
 - **풍부한 기능을 제공하는 오픈 소스이다**
   - 자료 구조, 네트워크, 입출력, 예외 처리 등에 최적화된 알고리즘 라이브러리를 제공하는 자바 개발 키드(JDK)가 있다.

<details>
<summary><b>개발 환경 설치</b></summary>
<div markdown="1">

1. 설치
```bash
sudo apt-get update
sudo apt-get upgrade

# Java11 설치
sudo apt-get install openjdk-11-jdk
```

2. 설치 확인
```bash
# 설치 확인
java -version
openjdk version "11.0.22" 2024-01-16
OpenJDK Runtime Environment (build 11.0.22+7-post-Ubuntu-0ubuntu222.04.1)
OpenJDK 64-Bit Server VM (build 11.0.22+7-post-Ubuntu-0ubuntu222.04.1, mixed mode, sharing)

# 설치 확인
javac -version
javac 11.0.22
```

3. 환경설정
```bash
# ~/.profile 열기
$ sudo gedit ~/.profile

# ~/.profile 파일에 설정 추가
# JAVA_HOME settings
export JAVA_HOME=$(dirname $(dirname $(readlink -f $(which java))))
export PATH=$PATH:$JAVA_HOME/bin

# 현재 실행중인 shell에 즉시 적용
$ source ~/.profile

# 설정 확인
$ echo $JAVA_HOME
/usr/lib/jvm/java-11-openjdk-am64
```

4. Java 삭제 (필요한 경우)
```bash
sudo apt-get purge openjdk*
```

</div>
</details>

## 변수와 자료형

- 비트(bit) : 0 또는 1로 표현할 수 있는 최소 단위
- 바이트(byte) : 8비트가 모이면 1바이트
