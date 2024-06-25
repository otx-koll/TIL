## wget
wget은 인터넷에서 파일을 다운로드 하기 위한 명령줄 유틸리티이다. HTTP, HTTPS, FTP 등 다양한 네트워크 프로토콜을 지원하며 Unix와 유사한 운영체제에서 널리 사용된다.

### 주요 기능
- 느리거나 블안정한 네트워크 연결 처리
- 실패한 다운로드 재시도
- 중단된 다운로드 재개
- 재귀적으로 파일을 다운로드
- 특정 파일 유형을 필터링
- 다운로드 속도 제한
- 다운로드 디렉토리를 지정하는 옵션 제공

### 설치
```bash
sudo apt update && sudo apt install wget
```

### 사용예시 및 옵션

1. 단일 파일 다운로드

```bash
wget http://example.com/path/to/file.txt
```

2. 특정 디렉토리에 파일 다운로드 

```bash
wget -P /path/to/directory http://example.com/path/to/file.txt
```

1. 다른 이름으로 파일 다운로드

```bash
wget -O new_file_name.txt http://example.com/path/to/file.txt
```

4. 중단된 다운로드 재개

```bash
wget -c http://example.com/path/to/file.txt
```

5.  다운로드 속도 제한

속도 제한 예시 : 100KB/s의 경우 100k 작성

```bash
wget --limit-rate=100k http://example.com/path
```

6. 여러 파일 다운로드

URL 목록이 포함된 텍스트 파일을 만들고 -i 또는 --input 파일 옵션을 사용

```bash
wget http://example.com/path/to/file1.txt
http://example.com/path/to/file2.txt

# 다른 방법) URL이 포함된 텍스트 파일(예: urls.txt)을 만듦

sudo vi /path/urls.txt
# http://example.com/path/to/file1.txt
# http://example.com/path/to/file2.txt

# -i 옵션을 사용하여 파일을 다운로드한다.

wget -i urls.txt
```

7. 재귀적으로 파일 다운로드

```bash
wget -r http://example.com/path/to/website
```

8. 재귀 깊이 제어

wget에서 재귀 깊이 제어는 지저된 URL에서 파일이나 웹 페이지를 다운로드할 때 명령이 따라야 하는 최대 수준 수를 나타낸다. 

```bash
wget -r -l 1 http://example.com/path/to/website
```

9. 특정 파일 형식만 다운로드

-A 또는 --accept 옵션 다음 쉼표로 구분된 파일 확장자 목록 작성

```bash
wget -r -A .jpg,.png http://example.com/path/to/website
```

10. 특정 파일 형식 제외

-R 또는 --reject 옵션 다음 쉼표로 구분된 파일 확장자 목록 작성

```bash
wget -r -R .jpg,.png http://example.com/path/to/website
```

11. 지정된 디렉토리에서만 파일 다운로드

--include-directories 또는 --exclude-directories 옵션 다음 쉼표로 구분된 파일 확장자 목록 작성

```bash
wget -r --include-directories=dir1,dir2 http://example.com/path/to/website
```

12.  상대 링크만 따르기

기본적으로 wget은 절대 링크과 상대 링크를 모두 따른다. 상대 링크만 따라갈시 --no-parent 옵션을 사용한다.

```bash
wget -r --no-parent http://example.com/path/to/website
```

13. 재시도 횟수 제어

-tires 또는 -t 옵션 뒤에 원하는 재시도 횟수 작성

```bash
wget --tries=5 http://example.com/path/to/file.txt
```

14. 시간 초과 설정

--timeout 또는 -T 옵션 뒤에 원하는 시간 초과 값(초)을 작성

```bash
wget --timeout=10 http://example.com/path/to/file.txt
```