# 정규표현식(Regex)
문자열 데이터 중에서 원하는 조건(패턴)과 일치하는 문자열 부분을 찾아내기 위해 사용하는 것이다. 입력값이 정해진 형식에 맞는지 검증해야 할 때 정규표현식을 사용하면 좋다.

## 정규식 기호
### 기본 기호
기호|설명|예시
-|-|-
**.** |임의의 문자 1개를 의미|
**^**|문장의 시작<br>\[]괄호 안에 있다면 일치하지 않는 부정의 의미로 쓰인다|**^a** : a로 시작하는 단어<br>**[\^a]** : a가 아닌 철자인 문자 1개
**$**|문장의 끝. 특정 문자열로 끝난다|**a$** : a로 끝나는 단어
**[]**|[] 괄호 안의 문자가 있는지를 확인한다|**\[ab][cd]** : a,b중 한 문자와 c,d중 한 문자<br>→ ac ad bc bd 
**\[^]**|[] 대괄호 안에 ^ 문자가 있으면, 제외를 뜻한다<br>- 대괄호 안에 ^ 가 쓰이면 제외의 뜻<br>- 대괄호 밖에 ^ 가 쓰이면 시작점의 뜻|**\[^a-z]** : 알파벳 소문자 a부터 z까지를 제외한 모든 문자
**-**|사이의 문자 혹은 숫자를 의미|**\[a-z]** : 알파벳 소문자 a부터 z까지 하나<br>**\[a-z0-9]** : 알파벳 소문자 전체,0~9 중 한 문자
**\|**|또는|**\[a\|b]** : a 혹은 b
**()**|그룹|**01(0\|1)** : 01뒤에 0 또는 1이 들어간다<br>→ 010(o), 011(o), 012(x)
**{}**|개수|**a{3}b** : a가 3번 온 후 b가 온다<br>→ aab(x), aaab(o), aaaab(o)
**\b**|공백, 탭, ",", "/" 등을 의미한다|**apple\b** : apple뒤에 공백 탭등이 있다<br>→ apple juice (o), apple\.com (x)
**\B**|\b의 부정<br>공백 탭등이 아닌 문자인 경우 매치한다|**apple\B**<br>→ apple\.com (o)
**\d**|0~9 사이의 숫자<br>\[0-9]와 동일|
**\D**|\d의 부정<br>숫자가 아닌 어떤 문자, \[^0-9]와 동일|
**\s**|공백, 탭|
**\S**|공백, 탭이 아닌 문자|
**\w**|알파벳 대소문자+숫자+"_"<br>\[a-zA-Z_0-9]와 동일|
**\W**|\w의 부정<br>\[^a-zA-Z_0-9]

### 수량 기호
기호|설명|예시
-|-|-
**?**|없거나 있거나 (zero or one)|**a1?** : 1이 최대 한개만 있거나 없을수도 있다<br>→ a(o), a1(o), a11(x), a111(x)
**\***|없거나 있거나 많거나 (zero or more)|**a1\*** : 1이 있을수도 없을수도 있다<br>→ a(o), a1(o), a11(o), a111(o)
**+**|하나 또는 많이 (one or more)|**a1*** : 1이 1개 이상있다<br>→ a(x), a1(o), a11(o), a111(o)
**{n}**|n개 있다|**a{3}** : a가 3개 있다<br>→ aa(x), aaa(o), aaaa(x), aaaaaaa(x)
**{n, m}**|n개 이상 m개 이하. 최소, 그리고 최대|**a{3,5}** : a가 3개 이상 5개 이하 있다<br>→ aa(x), aaa(o), aaaa(o), aaaaaaa(x)
**{n,}**|n개 이상. 최소|**a{3,}** : a가 3개 이상 있다<br>→ aa(x), aaa(o), aaaa(o), aaaaaaa(o)

### 그룹 범위 기호
기호|설명
-|-
**()**|그룹 및 캡쳐
**(?\:)**|찾지만 그룹에 포함 안됨
**(?=)**|=앞 문자를 기준으로 전방 탐색
**(?<=)**|=뒤 문자를 기준으로 후방 탐색

### 자주 사용되는 표현식
정규 표현식|설명
-|-
**^\[a-zA-Z0-9]*$**|공백없는 숫자와 대소문자
**^\[a-zA-Z0-9 ]*$**|공백포함 숫자와 대소문자
**^\[가-힣]*$**|한글
**\\w+@\\w+\\.\\w+(\\.\\w+)?**|E-Mail
**^\d{2,3}-\d{3,4}-\d{4}$**|전화번호
**^01(?:0\|1\|\[6-9])-(?:\d{3}\|\d{4})-\d{4}$**|휴대전화번호
**\d{6} \- \[1-4]\d{6}**|주민등록번호
**^\d{3}-\d{2}$**|우편번호

## 정규식 문법
### String 정규식 문법
정규식 메서드|설명
-|-
**boolean matches(String regex)**|정규식에 매칭되는 값이 있는지 확인
**String replaceAll(String regex, String replacement)**|정규식 regex와 매치되는 모든 문자열을 replacement 문자열로 바꾼 문자열을 반환
**String[] split(String regex)**|정규식과 매치되는 문자열을 기준으로 분할

### regex 패키지 클래스
자바에서는 정규 표현식을 다루는 클래스인 `java.util.regex`패키지를 제공한다. 패키지의 클래스중에서 주로 Pattern 클래스와 Matcher 클래스가 사용된다.

#### Pattern 클래스
문자열을 정규표현식 패턴 객체로 변환해주는 역할을 한다. 일반 클래스처럼 공개된 생성자를 제공하지 않는다. 정규식 패턴 객체를 생성하려면 `complie()` 정적 메소드를 호출해야 한다. 

```java
String patternString = "^[0-9]*$";
Pattern pattern = Pattern.compile(patternString);
```
또는 `matches()`메소드를 바로 사용하여 정규식 검증을 할 수도 있다.

```java
String txt1 = "123123";
String txt2 = "123이것은숫자입니다00";

boolean result = Pattern.matches("^[0-9]*$", txt1);
System.out.println(result); // true

boolean result2 = Pattern.matches("^[0-9]*$", txt2);
System.out.println(result2); // false
```

Pattern 클래스 메서드|설명
-|-
**compile(String regex)**|정규표현식 패턴을 작성
**matches(String regex, CharSequence input)**|정규표현식 패턴과 문자열이 일치하는지 체크<br>일치하면 true, 일치하지 않는 경우 false를 리턴<br>전체 문자열과 완벽히 일치해야함
**asPredicate()**|문자열을 일치시키는 데 사용할 수 있는 술어 작성
**pattern()**|컴파일된 정규표현식을 String 형태로 반환
**split(CharSequence input)**|문자열을 주어진 인자값 CharSequence 패턴에 따라 분리

#### Matcher 클래스
필터링 된 결과값들을 지니고 있다. Pattern 클래스와 마찬가지로 생성자가 없다. Pattern객체의 `matcher()` 메소드를 호출해서 얻는다.

Matcher 클래스 메서드|설명
-|-
**find( )**|패턴이 일치하는 경우 true, 불일치하는 경우 false<br>(여러개가 매칭되는 경우 반복실행하면 일치하는 부분 다음부터 이어서 매칭됨)
**find(int start)**|start 위치 이후부터 매칭검색
**start( )**|매칭되는 문자열의 시작위치 반환
**start(int group)**|지정된 그룹이 매칭되는 시작위치 반환
**end( )**|매칭되는 문자열 끝위치의 다음 문자위치 반환
**end(int group)**|지정된 그룹이 매칭되는 끝위치의 다음 문자위치 반환
**group( )**|매칭된 부분을 반환
**group(int group)**|그룹화되어 매칭된 패턴중  group 번째 부분 반환
**groupCount( )**|괄호로 지정해서 그룹핑한 패턴의 전체 개수 반환
**matches( )**|패턴이 전체 문자열과 일치할 경우 true<br>(일부 문자열이 아닌 전체 문자열과 완벽히 일치 해야한다)

#### 정규식 플래그
고급 검색을 위한 전역 옵션을 설정할 수 있도록 지원하는 기능이다. 패턴을 주는 방법은 기호를 조합하거나 패턴 상수를 주는 방법이 있다.

```java
// 정규식 기호로 전달
Pattern.compile("(?i)([a-z]+)")

// 상수로 전달
Pattern.compile("(^.*$)", Pattern.CASE_INSENSITIVE)
```

Pattern 플래그 상수|기호|설명
-|-|-
**Pattern.CANON_EQ**|None|표준화된 매칭 모드를 활성화합니다.이 모드가 켜지면 a를 나타내는 유니코드 "\u00E5"와 a와 상단고리 유니코드를 쓴 "a\u030A"를 같다고 매칭합니다.
**Pattern.CASE_INSENSITIVE**|(?i)|대소문자를 구분하지 않습니다.
**Pattern.COMMENTS**|(?x)|공백과 주석이 무시됩니다. 주석은 \#부터 그 행 끝까지 입니다.
**Pattern.MULTILINE**|(?m)|다중행 모드를 사용여 모든 ^와 $가 인식됩니다. 기본값은 입력값 전체를 하나의 시작과 끝으로 인식합니다.
**Pattern.DOTALL**|(?s)|.가 개행문자 까지 포함하는 모든 문자로 매칭됩니다.
**Pattern.LITERAL**|None|입력의 메타문자와 이스케이프된 문자를 일반 문자로 취급합니다. CASE_INSENSITIVE와 UNICODE_CASE는 기능이 유지됩니다.
**Pattern.UNICODE_CASE**|(?u)|이 모드가 활성화 되면 대소문자 매칭이 유니코드 표준을 따릅니다. 기본은 US-ASCII 문자 집합을 따릅니다.
**Pattern.UNIX_LINES**|(?d)|^와 $를 처리시 UNIX 개행을 사용합니다.

> **예외처리**를 하고싶다면 `PatternSyntazException`로 해주면 된다.

### 정규식 테스트 사이트
http://regexr.com/

## Reference

https://docs.oracle.com/javase/7/docs/api/java/util/regex/Pattern.html

https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EC%A0%95%EA%B7%9C%EC%8B%9DRegular-Expression-%EC%82%AC%EC%9A%A9%EB%B2%95-%EC%A0%95%EB%A6%AC

https://hitomis.tistory.com/68
