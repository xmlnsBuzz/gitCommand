# git config 관련 명령

## alias (약자명령) 만들기

'alias'는 '별칭' 또는 '별명'이란 뜻이다. 명령의 전체 또는 일부를 약자로 만들 수 있다.

### 전역(global)에 지정할 경우

전역이란 현재 사용하는 working directory(WD)는 물론이고 다른 WD에도 만든 약자가 적용된다. 즉, --global option을 써서 전역지정을 하면 git이 설치된 곳 어디서든 적용된다.

* commit을 cm이라는 약자로 만든다.

> git config **--global** alias.cm commit

* 위의 alias로 약자를 만든 후의 사용예

> _git cm -m "alias로 약자 만들기"_

### --global 옵션없이 working directory(Local)에만 지정할 경우

> git config alias.cm commit

## alias로 지정한 약자 목록 보는 방법

* 전역 Alias 목록 보기
> git config **--global** --get-regexp alias

* 지역 Alias 목록 보기
> git config **--local** --get-regexp alias

* 전역 및 지역 Alias 목록 보기
> git config --get-regexp alias

git config --global alias.nccommit 'commit -a --allow-empty-message -m ""'
