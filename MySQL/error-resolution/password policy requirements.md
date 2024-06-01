```bash
mysql ERROR 1819 (HY000): Your password does not satisfy the current policy requirements
```
패스워드 정책 위반 시 발생하는 에러이다.

## 해결 방법

1. password validation을 제거하는 것으로 간단히 해결 할 수 있다.

```bash
$ mysql -u root -p
Enter password:
mysql> uninstall plugin validate_password;
Query OK, 0 rows affected (0.08 sec)
```

2. 현재 적용된 패스워드 정책을 바꾸거나 정책에 맞추기

현재 적용된 패스워드 정책 보기 >> 

```bash
mysql> SHOW VARIABLES LIKE 'validate_password%';
```

**정책 해석**
ㅤ|ㅤ
-|- 
validate_password.check_user_name|패스워드에 user_id가 들어가는가?<br>{ ON: 불가능, OFF: 가능 }
validate_password.length|패스워드 길이 >= value
validate_password.mixed_case_count|패스워드 안 대소문자 >= value
validate_password.number_count|패스워드 안 숫자 >= value
validate_password.policy|Low \|\| Medium \|\| Strong<br>(보안 설정 시 지정한 값)
validate_password.special_char_count|패스워드 안 특수문자 >= value

MySQL 5.x와 8.x 버전의 변수명이 다르다.

- 5.x -> validate_password_*
  8.x -> validate_password.*

**정책을 변경하는 방법**

```bash
mysql> SET GLOBAL [정책명]=[VALUE]; 

/* EX */
mysql> SET GLOBAL validate_password.policy=LOW; // MEDIUM -> LOW
```

[ ]을 제외하고 원하는 값 명시해주기



