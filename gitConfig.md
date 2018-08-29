# git config 관련 명령

## alias (약자명령) 만들기

### 전역(global)에 지정할 경우

* commit을 cm이라는 약자로 만든다.

> git config **--global** alias.cm commit

* 위의 alias로 약자를 만든 후의 사용예

> _git cm -m "alias로 약자 만들기"_

### working directory에만 지정할 경우

> git config alias.cm commit

## alias로 지정한 약자 목록 보는 방법

* 전역 Alias 목록 보기
> git config **--global** --get-regexp alias

* 지역 Alias 목록 보기
> git config **--local** --get-regexp alias

* 전역 및 지역 Alias 목록 보기
> git config --get-regexp alias

git config --global alias.nccommit 'commit -a --allow-empty-message -m ""'