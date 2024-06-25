문득 apt와 apt-get 차이가 궁금해졌다.

## apt vs apt-get

apt와 apt-get은 모두 명령줄 도구로 둘 중 아무거나 써도 상관없으나 apt를 사용하면 더 예쁘고 추가적인 정보를 출력해준다. 하지만 script를 작성할 때는 apt-get를 사용하는 것이 유리하다.

apt-get은 오래전부터 존재해왔고 더 많은 옵션이 존재하기에 안정적이고 호환성이 높다. 

### apt
- 현재 프로세스의 진행을 보기좋게 백분율로 표시
- 업그레이드해야 하는 패키지 목록 나열
- apt-get, apt-cache 및 dpkg -l의 기능 결합
  - apt-get : 패키지 설치, 업데이트 및 제거
  - apt-cache : 패키지 조회
  - dpkg : 시스템에 설치된 패키지 조회
- apt와 apt-get 명령과의 구문 비교
   
명령어|apt-get, apt-ache, dkpg 명령어|설명
-|-|-
apt update|apt-get update|Refreshes repository index
apt install \[package]|apt-get install \[package]|Install a package
apt upgrade|apt-get upgrade|Upgrade available package updates
apt remove \[package]|apt-get remove\[package]|Remove a package
apt purge \[package]|apt-get purge \[package]|Remove a package with configuration
apt autoremove|apt-get autoremove|Remove unnecessary dependencies
apt full-upgrade|apt-get dist-upgrade|Update all packages and remove unnecessary dependencies
apt search \[package]|apt-cache search \[package]|Search for a package
apt show \[package]|apt-cache show \[package]|Show package details
apt policy|apt-cache policy|Show active repo information
apt policy \[package]|apt-cache policy \[package]|Show installed and available package version
apt list --installed|dpkg --list|Show installed package

- 새 명령어

명령어|설명
-|-
apt list|List installed packages and upgradable packages
apt edit-sources|Edits sources list