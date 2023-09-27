# GitHub SSH Key 생성 및 등록


## SSH 키가 필요한 이유

로컬 개발 환경에서 Git을 단독으로 사용한다면 SSH가 없어도 무방하지만, 안전하게 외부 Git 서버에서 코드를 clone하거나 Push하려면 SSH 프로토콜을 사용한다. 

*SSH*는 인터넷이나 네트워크를 통해 연결되어 있는 컴퓨터에 **안전하게 연결해주는 프로토콜**이다. 사용자나 패스워드 등 여러가지 인증 방법을 지원하지만 보통 편리성과 안전성 면에서 공개키 인증 방식을 많이 사용한다.

**공개키 인증 방식을 사용하려면 공개키와 개인키를 한 쌍 만들어야 한다.** 공개키는 접속하고자 하는 서버에 등록해놓는 용도로 사용한다. 사용자는 개인키를 통해 SSH에 접속하고, 연결 요청을 받은 SSH서버에선 서버에 등록된 공개키 중에서 요청 받은 개인키 정보와 일치되는 공개키가 있는지 찾는다. 없다면 서버 접속에 실패하고, 있다면 인증에 성공하고 서버에 접속이 된다.

공개키는 외부에 공개되어도 괜찮지만 **개인키는 반드시 나만 접근할 수 있도록 안전하게 보관해야한다.** 

## SSH 공개키와 개인키 만들기

SSH 키를 만들기 전에 이미 키가 만들어져 있는지 확인한다. 키를 그냥 추가로 생성하면 기존 키가 덮어씌워질 수도 있다.

```bash
$ cd ~/.ssh
$  ls
...
```
먼저 ~/.ssh 디렉터리로 이동하여 ls를 실행해 id_ed25519와 id_ed25519.pub 혹은 id_rsa와 id_rsa.pub 파일쌍이 있는지 확인한다. 파일이 존재한다면 이미 키를 생성했던 것이다. 다른 이름으로 만들어서 사용해도 가능하지만, 개인키의 위치를 따로 지정해줘야해서 불편하다.

위 파일들이 없다면 ssh-keygen으로 생성한다. 생성 방법은 아래와 같다.

```bash
$ ssh-keygen -t ed25519 -C "your_email@example.com"
```
-C 옵션의 your_email\@example.com은 자신의 이메일로 변경한다. 만약 ed25519 방식으로 동작하지 않는다면 아래와 같이 RSA로 옵션을 변경하여 SSH 키를 생성한다.

```bash
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

명령어를 실행하여 키를 만들어본다.

```bash
$ ssh-keygen -t ed25519 -C "otx-koll@gmail.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/Users/lainyzine/.ssh/id_ed25519):
```
첫 번째로 저장하고자하는 위치를 물어본다. 나는 기본값을 사용하려하기에 Enter를 누른다.

```bash
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
```
다음으로 SSH 키에 대한 비밀번호를 추가로 지정할지 물어본다. 없이 사용하려면 Enter를 두 번 입력한다. (비밀번호는 나중에 지정가능하지만, GitHub에서는 공식적으로 패스워드 설정을 권장하고 있다.)

```bash
Your identification has been saved in /Users/lainyzine/.ssh/id_ed25519.
Your public key has been saved in /Users/lainyzine/.ssh/id_ed25519.pub.
The key fingerprint is:
SHA256:MRR2EWPjezAxwlrxCgfqjq43CJjtZVl8Heo5YU/912I otx-koll@gmail.com
The key's randomart image is:
+--[ED25519 256]--+
|      ..*oXo     |
|     . +o*.=     |
|    ...o+o=o     |
|   .  +o=+o+.    |
|.o  .o +S=. ..  .|
|+ .o+   + ..  E o|
|.o.o.    .   . o |
|..+              |
|.o..             |
+----[SHA256]-----+
```
SSH 키가 생성되었다. 개인키는 /Users/lainyzine/.ssh/id_ed25519에, 공개키는 /Users/lainyzine/.ssh/id_ed25519.pub에 저장되었다. RSA 방식으로 키를 생성하면 기본 파일 이름은 id_rsa, id_rsa.pub이 된다.

실제로 키가 잘 생성되어 있는지 개인키를 출력해본다.

```bash
$ cat id_ed25519
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmU333AAEb55uZQAAAAAAAAABAAAAMwAAAAtzc2gtZW
QyNTUxOQAAACDoOnBaZyx9IjcgU6666n28Qz6LwTPYHZRW0/H9IGT+QAAAKAHVs1tB1bN
bQAAAAtzc2gtZWQyNTUxOQAAACDoOnBaZyxeajc17UAPTn28Qz6LwTPYHZRW0/H9IGT+Q
AAAEBbytj4mVV9QBnssl9TRW4N2p3frl95UFpQtnRn5sDkKeg6cFpnLH0iNyBQDGc9Ofbx
DPovBM9gdlFbT8f0gZP5AAAAFnlvdXJfZW1haWxAZXhhbXBsZS5jb20BAgMEBQYH
-----END OPENSSH PRIVATE KEY-----
```

이번에는 공개키를 출력해본다. 이 내용을 GitHub에 등록해주어야한다.

```bash
$ cat id_ed25519.pub
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIOg6cFpnLH0iNyBQDGc9OfbxDPovBM9gdlFbT8f0gZP5 your_email@example.com
```

텍스트가 깨지지 않도록 [명령어를 통해 복사하기](../Terminal/clipboard%20copy&paste.md)를 추천한다.

## 공개키를 GitHub 계정에 등록하기

GitHub에 로그인 후 오른쪽 상단의 프로필을 클릭하고 Settings 메뉴로 이동한다. SSH and GPG keys 메뉴를 선택한다. 

![SSH 키 등록 폼](./img/add%20new%20ssh%20key.png)

Title 필드에는 등록하려는 키의 이름을 입력한다.

Key 필드에는 앞에서 복사한 공개키를 그대로 입력한다. 줄바꿈이나 다른 문자가 들어가면 안된다. KeyType은 그대로 둔다.

이제 등록한 키가 잘 동작하는지 확인해본다.

## SSH 접속 설정

확인하기에 앞서 SSH 접속 설정을 해줄 것이다. ~/.ssh/config 파일에 아래 내용을 추가하거나, 파일이 없다면 생성한 후 아래 내용을 추가한다.

```bash
Host github.com
  IdentityFile ~/.ssh/id_ed25519
  User git
```

아래 명령어로 GitHub에 접속 테스트를 해볼 수 있다.

```bash
$ ssh -T git@github.com
Enter passphrase for key '/home/hs/.ssh/id_ed25519':
Hi otx-koll! You've successfully authenticated, but GitHub does not provide shell access.
```

## GitHub에 SSH 키로 접속 테스트

```bash
$ git clone git@github.com:otx-koll/TIL.git
Cloning into 'TIL'...
Enter passphrase for key '/home/hs/.ssh/id_ed25519':
warning: You appear to have cloned an empty repository.
$ ls
TIL
```


 