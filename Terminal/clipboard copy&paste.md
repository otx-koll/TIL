xclipe을 설치해야 한다.

```bash
sudo apt-get install xclip
```

### 클립보드에 복사하기

```bash
cat file | xclip -selection clipboard
```

### 클립보드에서 붙여넣기

```bash
xclip -o -selection clipboard > file
```