Git으로 커밋한 모든 것은 언제나 복구 가능하다. 삭제한 브랜치나 `--amend`옵션으로 다시 커밋한 것도 복구할 수 있다. 하지만 커밋하지 않은 것은 절대로 되돌릴 수 없다. 
## 파일 상태를 Unstage로 변경

```bash
git reset HEAD <file>
```

- 파일 명이 없으면 add한 파일 전체를 취소한다

```bash
git reset
```

## commit 취소

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
## Modified 파일 되돌리기
최근 commit한 버전으로 되돌리는 방법
```shell
git checkout -- <file>
```
원래 파일로 덮어썼기 때문에 수정한 내용은 전부 사라진다. 
