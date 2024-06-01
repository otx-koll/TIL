ubuntu 버전 22.04

[IntellJ Community Edition의 리눅스 버전 다운받기](https://www.jetbrains.com/ko-kr/idea/download/#section=linux)

다운 받은 파일을 ubuntu로 옮기고 압축을 풀어준다.

```bash
mv ideaIC-2024.1.2.tar.gz /home/test
cd /home/test
tar -xvzf ideaIC-2024.1.2.tar.gz
```

압축이 풀리면 아래 명령어로 실행시 intellJ가 실행된다.

```bash
cd idea-IC-241.17011.79/bin/
.idea.sh
```
alias를 이용하고싶다면 `~/.bashrc`를 편집하여 alias를 추가하고 `source ~/.bashrc` 로 등록한다.

```bash
alias intelliJ=<ABSOULTE_INSTALL_PATH>/bin/idea.sh
```
