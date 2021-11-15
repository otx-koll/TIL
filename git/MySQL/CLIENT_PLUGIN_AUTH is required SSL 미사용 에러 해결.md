### CLIENT_PLUGIN_AUTH is required : SSL 미사용 에러

mysql-connector-java 버전을 낮추거나 mysql 버전 업그레이드 진행이 필요하다.

또는 url 에 파라미터 추가 (& 에러 발생시 &amp; 로 대체)
```
verifyServerCertificate=false&useSSL=false
```
