### The server time zone value ‘KST’ is unrecognized or represents more than one time zone 에러

```java
The server time zone value ‘KST’ is unrecognized or represents more than one time zone

: The server time zone value ‘KST’ is unrecognized or represents more than one time zone.
You must configure either the server or JDBC driver (via the serverTimezone configuration property)
to use a more specifc time zone value if you want to utilize time zone support.
```
mysql-connector-java 버전 5.1 이후에 나온 버전부터 KST 타임존을 인식하지 못하는 이슈가 있다.

### 💡해결방법

config.xml 에서 url에 serverTimezone을 UTC로 추가한다.

```xml
jdbc:mysql://ip주소 : port번호/DB스키마명?characterEncoding=UTF-8&serverTimezone=UTC
```

만약,
The reference to entity “serverTimezone” must end with the ‘;’ delimiter.  에러가 발생할 경우
& 대신에 &amp;  사용한다.

```xml
jdbc:mysql://ip:port/TestDB?characterEncoding=UTF-8&amp;serverTimezone=UTC
```




