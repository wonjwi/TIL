# Git 실행취소 하는 방법

> 2021년 8월 1일 - git add, commit, push 취소하기
>
> - git pull, git status, git branch 습관화 하자.....
> - git은 commit도 reset도 취소가 된다^^
> - 너무 겁먹지 말고 하되, 늘 조심하고 조심하자!!!

## git add 취소하기

- 실수로 `git add *` 명령으로 모든 파일을 Staging Area에 넣은 경우
- Staging Area에 넣은 파일 또는 폴더를 다시 빼고 싶은 경우

```bash
# add한 파일 전체 취소
$ git reset HEAD

# add한 파일 중 특정 파일만 취소
$ git reset HEAD <file>
```

## git commit 취소하기

- 특정 파일을 빼먹었다는 등의 이유로 이미 완료한 commit을 취소하고 싶은 경우

```bash
# commit을 취소하고 해당 파일들은 staged 상태로 워킹 디렉터리에 보존
$ git reset --soft HEAD^

# commit을 취소하고 해당 파일들은 unstaged 상태로 워킹 디렉터리에 보존
$ git reset --mixed HEAD^
$ git reset HEAD^ # default 값은 위와 동일
$ git reset HEAD~2 # 마지막 2개의 commit 취소

# commit을 취소하고 해당 파일들은 unstaged 상태로 워킹 디렉터리에서 삭제
$ git reset --hard HEAD^
```

- reset 명령 사용 시 옵션에 관련해서 주의하기 ⭐️

  - **--soft** : index 보존 (add, staged 상태), 워킹 디렉터리의 파일 보존.
  - **--mixed** : index 취소 (add하기 전, unstaged 상태), 워킹 디렉터리의 파일 보존 **(default)**
  - **--hard** : index 취소 (add하기 전, unstaged 상태), 워킹 디렉터리의 파일 삭제

- 워킹 디렉터리를 원격 저장소의 마지막 commit 상태로 되돌리기

  - 단, *원격 저장소에 있는 마지막 commit 이후의 워킹 디렉터리와 add 했던 파일 모두 사라지므로* 주의할 것!

```bash
$ git reset --hard HEAD
```

### commit message 수정하기

- commit message를 잘못 적어서 수정하고 싶은 경우

```bash
$ git commit --amend
$ git commit --amend -m "commit message"
```

## git push 취소하기

1. 워킹 디렉터리에서 commit을 되돌리기

```bash
# 가장 최근의 commit을 취소
$ git reset HEAD^

# 저장된 HEAD 변경 이력 확인
$ git reflog
$ git log -g # reflog와 commit 함께 확인

# 원하는 시점으로 워킹 디렉터리 되돌리기
$ git reset HEAD@{이동할 번호}
$ git reset <commit id>
```
  

2. 되돌려진 상태에서 다시 commit 하기

```bash
$ git commit -m "commit message"
```

3. 원격 저장소에 강제로 push 하기

```bash
# 경고를 무시하고 강제로 push 하기
$ git push origin <branch name> -f
$ git push origin +<branch name>
```

- local 내용을 remote에 강제로 덮어쓰기 하게 되므로 주의하기 ⭐️
  - *되돌아간 commit 이후의 모든 commit 정보가 사라지기 때문에* 주의해야 함
  - 특히, 협업 프로젝트에서는 동기화 문제 발생할 수 있으므로 **꼭!!!** 팀원과 상의 후 진행하기

## Reference

- https://gmlwjd9405.github.io/2018/05/25/git-add-cancle.html
- http://ohyecloudy.com/pnotes/archives/1994/
- http://git-scm.com/docs/git-reset
- http://git-scm.com/docs/git-reflog
- http://git-scm.com/docs/git-commit
