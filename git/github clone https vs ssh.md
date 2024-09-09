## https

- push나 pull 할 때 인증 요구할 수 있다.
  - git에서 제공하는 credential 저장소의 기능을 이용하면 계정 정보 캐싱해뒀다가 **자동으로 입력되게 가능**
  - 위 기능을 사용하지않더라도 mac에선 keychain 시스템, whndows에서는 windows credential store(자격증명관리자)를 통해 각각 계정정보 저장하기때문에 매번 로그인 할 필요가 없다.
- 연결 설정 간단
- 엄격한 환경에서도 사용 가능
  - 방화벽
  - 프록시 설정

### 연결방법

```bash
git clone https://github.com/test/test.git
```

#### 오류

링크를 그냥 붙혀넣기하면 `fatal: protocol 'https' is not supported`에러가 뜬다.

찾아보면 인터넷에서 복사한 텍스트를 콘솔에 바로 붙여넣기 하지 말라는건데 해당 에러 메시지를 긁어서 복사하고 그냥 메모장에 붙혀넣어보면 `fatal: protocol 'https' is not supported`라 뜬다.

https 앞에 안보이던 네모칸이 뜨는데 이거 때문에 알 수 없는 프로토콜이라는 에러가 난 것이다.

그래서 그냥 처음부터 끝까지 타이핑하니까 정상적으로 작동했다.

## ssh

- 한 번 설정 후 인증을 요구하지 않는다.
- ssh 키 생성 및 설정 해야 한다.
  - github 계정에 공개 키 등록
  - 개인 키 : 로컬 컴퓨터
  - 공개 키 : github에 등록
- 한 번 설정하면 안전한 연결 가능 

### 연결방법

[링크 참고](/git/generating-ssh-key-adding.md)



