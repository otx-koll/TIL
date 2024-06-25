## Version
Ubuntu 22.04

## 설치 방법

업데이트
```bash
sudo apt update
```

wget 아직 설치되지 않은 경우라면 설치
```bash
sudo apt install wget
```

chrome의 안정적인 최신 패키지 다운로드
```bash
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

최근 다운로드한 패키지 설치
```bash
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

업데이트
```bash
sudo apt update
```
```bash
sudo apt upgrade
```

제거
```bash
sudo apt purge google-chrome-stable
```