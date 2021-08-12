## git add 취소(파일 상태를 unstage로 변경)

```bash
git reset HEAD [file]
```

- 파일 명이 없으면 add한 파일 전체를 취소한다

```bash
git reset
```

## git commit 취소

```bash
git reset --soft HEAD^
git reset --mixed HEAD^ 
git reset HEAD^
git reset HEAD~2 
git reset --hard HEAD^
```

- `git reset —soft HEAD^` : commit 취소 후, 해당 파일을 staged 상태로 보존
- `git reset --mixed HEAD^` : commit 취소 후, 해당 파일을 unstaged 상태로 보존
- `git reset HEAD^` : 위와 동일
- `git reset HEAD~2` : 마지막 2개의 commit 취소
- `git reset --hard HEAD^` : commit 취소 후, 해당 파일을 unstaged 상태로 삭제