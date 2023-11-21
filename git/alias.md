## git alias 추가
복잡한 명령들을 축약하여 사용할 수 있다. alias를 등록하려면 아래와 같다.

```bash
git config -옵션 alias.{alias 이름} '{alias를 지정할 명령어}'
```

지정할 명령어에 공백이 포함되어 있다면 작음 따옴표로 묶어줘야한다.

아래는 alias를 만드는 예이다.

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

직접 gitconfig 파일을 수정할 수도 있다.

- global 옵션이라면 `open ~/.gitconfig`
- local 옵션이라면 `해당 디렉토리 -> 숨겨진 파일 보기 -> .git -> config 파일`

```bash
[alias]
    co = checkout
    br = branch
    ci = commit
    st = status 
```

이런식으로 들어가있다.

## alias 목록 보기

터미널에서 보고 싶다면

```bash
# global
git config --global --get-regexp alias

# local
git config --local --get-regexp alias
git config --get-regexp alias
```

local에만 들어가있다면 --global로 했을 때 아무것도 안나온다.

## alias 삭제

```bash
git config --옵션 --unset alias.{alias 이름}
```

```bash
# global
git config --global --unset alias.st
 
# local
git config --local --unset alias.st
git config --unset alias.st
```

## alias에서 셸 명령어

위처럼 사용할 수도 있지만 셸 명령어를 사용한다면 더욱 활용할 수 있다. 느낌표로 시작하는 alias는 셸 스크립트로 작동한다.

예를 들어 Hello World를 찍어본다.

```bash
git config alias.test '!echo Hello World'
```
실행하면 Hello World가 출력된다.

```bash
$ git test
Hello World
```

또 다른 예를 들어보자. 머지된 로컬 브랜치 삭제를 한다면

```bash
git branch --merged | grep -v "master\|develop" | xargs git branch -D
```
이렇게 길게 해야하지만 alias로 등록한다면 편해진다.

```bash
git config alias.db '!git branch --merged | grep -v \"master\\|develop\" | xargs git branch -d'
```

`git db`만 입력하면 머지된 로컬 브랜치들이 삭제된다.