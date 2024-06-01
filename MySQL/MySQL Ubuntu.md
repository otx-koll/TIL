## MySQL 서버 설치
```bash
sudo apt update
sudo apt install mysql-server
```
설치 후 버전 체크
```bash
$ mysql -- version
mysql  Ver 8.0.36-0ubuntu0.22.04.1 for Linux on x86_64 ((Ubuntu))
```

## MySQL 보안 설정
MySQL 보안 스크립트를 실행한다.
```bash
sudo mysql_secure_installation
```
이 스크립트는 여러 보안 옵션을 설정하며, 루트 암호를 재설정하고 익명 사용자를 삭제하는 등의 작업을 수행한다.

```bash
$ sudo mysql_secure_installation

Securing the MySQL server deployment.

Connecting to MySQL using a blank password.
The 'validate_password' component is installed on the server.
The subsequent steps will run with the existing configuration
of the component.

Skipping password set for root as authentication with auth_socket is used by default.
If you would like to use password authentication instead, this can be done with the "ALTER_USER" command.
See https://dev.mysql.com/doc/refman/8.0/en/alter-user.html#alter-user-password-management for more information.

```

1. 익명 사용자 삭제 여부 : y
```bash
By default, a MySQL installation has an anonymous user,
allowing anyone to log into MySQL without having to have
a user account created for them. This is intended only for
testing, and to make the installation go a bit smoother.
You should remove them before moving into a production
environment.

Remove anonymous users? (Press y|Y for Yes, any other key for No) : y
```
2. root 사용자의 원격 접속 허용 여부
```bash
Normally, root should only be allowed to connect from
'localhost'. This ensures that someone cannot guess at
the root password from the network.

Disallow root login remotely? (Press y|Y for Yes, any other key for No) : n
```
3. test database 삭제 여부
```bash
By default, MySQL comes with a database named 'test' that
anyone can access. This is also intended only for testing,
and should be removed before moving into a production
environment.

Remove test database and access to it? (Press y|Y for Yes, any other key for No) : y
```
4. 권한 테이블 다시 로드
```bash
Reloading the privilege tables will ensure that all changes
made so far will take effect immediately.

Reload privilege tables now? (Press y|Y for Yes, any other key for No) : y
```

## MySQl 서비스 관리
MySQL 서버를 시작, 중지 및 재시작 하는 방법
```bash
sudo systemctl start mysql     # MySQL 서버 시작
sudo systemctl stop mysql      # MySQL 서버 중지
sudo systemctl restart mysql   # MySQL 서버 재시작
sudo systemctl status mysql    # MySQL 서버 상태 확인
```

## MySQL 접속

```bash
sudo mysql -u root -p
```
```bash
$ sudo mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 18
Server version: 8.0.35-0ubuntu0.22.04.1 (Ubuntu)

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

## MySQL 사용자 및 데이터베이스 생성
```sql
use mysql;
```

```sql
# 새로운 사용자 생성
CREATE USER '새사용자'@'localhost' IDENTIFIED BY '비밀번호';

# 모든 권한 부여 (관리자 권한)
GRANT ALL PRIVILEGES ON *.* TO '새사용자'@'localhost' WITH GRANT OPTION;

# 변경사항 적용
FLUSH PRIVILEGES;

# 새로운 데이터베이스 생성
CREATE DATABASE 새데이터베이스;

# 생성한 데이터베이스 사용
USE 새데이터베이스;

# 계정 생성 및 권한 부여 확인
SHOW GRANTS FOR '사용자'@'호스트';
```

## root 계정 비번 재설정
```bash
sudo mysql -u root
```
```sql
ALTER USER 'root'@'localhost' IDENTIFIED BY '비밀번호';

FLUSH PRIVILEGES;
```

## 외부 접속 허용

```bash
sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
```
bind-address, mysqlx-bind-address 모두 0.0.0.0으로 변경 후 :wq로 저장
```bash
mysqlx-bind-address : 0.0.0.0
bind-address : 0.0.0.0
```
mysql 재시작
```bash
sudo service mysql restart
```
