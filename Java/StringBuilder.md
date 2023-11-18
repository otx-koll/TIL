String은 한 번 생성되면 변경할 수 없다. 덧셈 연산을 자주 사용하게 되면 연결할 때마다 새로운 객체가 생성된다. 그리고 이전에 있던 문자열은 [JVM](/Java/JVM.md)의 [GC](/Java/Garbage-Collection.md)가 처리하게 된다. String 객체끼리 더하는 행위는 메모리 할당과 해제를 발생시키는데, 덧셈 연산이 많아지면 성능적으로 좋지 않다. 이러한 문제를 해결하기 위해 StringBuilder가 등장하게 되었다. 

# StringBuilder

StringBuilder는 변경 가능한 문자열을 만들 수 있다. 문자열끼리 더할 때 새로운 객체를 생성하는게 아닌 기존 데이터에 더하는 방식을 사용하므로 속도도 빠르고 부하가 적다. 따라서 긴 문자열을 더하게 된다면 StringBuffer나 StringBuilder를 사용하는 것이 좋다.

StringBuffer는 멀티쓰레드 환경이라면 사용하는게 좋다.

## 생성자
```java
StringBuilder sb = new StringBuilder(); // 기본 생성자
StringBuilder sb = new StringBuilder(10); // int 타입 값으로 buffer 사이즈 지정
StringBuilder sb = new StringBuilder("aa"); // String 문자열을 인자로 함
```

## 주요 메소드
메소드|설명
-|-
.append()|문자열을 추가
.insert(int offset, String str)|offset 위치에 str을 추가
.replace(int index1, int index2, String str)|첫번째와 두번째 파라미터로 받는 숫자 인덱스에 위치한 문자열을 대체
.substring(int start)<br>.substring(int start, int end)|인덱싱. 파라미터가 하나라면 해당 인덱스부터 끝까지, 두개라면 시작점과 끝점-1 까지 인덱싱
.deleteCharAt(int index)|인덱스에 위치한 문자 하나를 삭제
.delete(int start, int end)|start부터 end-1까지의 문자를 삭제
.toString()|String으로 변환
.reverse()|해당 문자 전체를 뒤집는다
.setCharAt(int index, String s)|index위치의 문자를 s로 변경
.setLength(int len)|현재 문자열보다 길게 조정하면 공백으로 채워짐. 짧게 조정하면 나머지 문자는 삭제
.trimToSize()|문자열이 저장된 char[] 배열 사이즈를 현재 문자열 길이와 동일하게 조정. 공백 사이즈를 제공하는 것이다. 문자열 뒷부분의 공백을 모두 제거함

### See also

https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html
