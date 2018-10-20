# Corey's Git 01

## 중앙집중형 VCS(Version Control System)와 분산형 VCS의 차이점

### 중앙집중형 VCS

Central VCS 중앙집중형 버전관리는 관리하는 모든 데이터가 내 컴퓨터가 아닌 서비스업체(github같은)컴퓨터에 있으므로 인터넷에 연결되어야 버전관리를 할 수 있다. 따라서 데이터가 오가는 시간이 소모된다. 결정적인 단점은 internet에 연결되지 않은 상태에서는 버전관리가 안된다.

![중앙집중형 버전관리](https://git-scm.com/book/en/v2/images/centralized.png)

### Distributed Version Control System

![분산형 버전관리](https://git-scm.com/book/en/v2/images/distributed.png)

git과 같은 분산형 버전관리는 사용자 각자의 working directory에서 local computer(자기 컴퓨터)로 버전을 관리하고 필요시에만 서버에 올리거나 가져오므로 서버와 연결이 끊겨도 지속적으로 작업할 수 있다. 또한 팀원 모두가 같은 버전의 데이터를 가질 수 있어서 만약의 경우 복구가 용이하다.

### git-scm에서 git을 다운로드 하여 설치한다

---

## 실습전 몇 가지 확인사항

[git-scm에서 다운로드](https://git-scm.com/)

### 버전체크하기

--version을 사용하여 현재의 git version을 체크한다.(참고로 나의 현재 git version은 windows용 버전 2.19, 20180917기준)

>git --version

```
$ git --version
git version 2.19.0.windows.1
```

### git config

git config는 username, useremail 등의 정보를 설정할 때 쓰며, 이외에도 많은 기능이 있으나 추후에 설명한다.

#### global(전역)에 설정할 때

>git config --global user.name "username"
>git config --global user.email "useremail"

예를 들어 username이 xmlnsBuzz이고 이메일이 xmlnsbuzz@gmail.com 이라면

>git config --global user.name "xmlnsBuzz"
>git cinfig --global user.email "xmlnsbuzz@gmail.com"

이 될 것이다.

#### local(working directory)에 설정할 때

>git config --local user.name "username"
>git config --local user.email \"useremail\"

#### config list(목록) 보기

>git config --list

```
...
user.name=xmlnsBuzz
user.email=xmlnsbuzz@gmail.com
...
alias.co=checkout
alias.br=branch
alias.st=status
alias.cm=commit
...
```
위와 비슷한 설정목록이 나올 것이다.

### git help

>git help &lt;verb>

또는

>git &lt;verb> --help

와 같이 입력한다. 예를 들어 config명령에 대한 도움말을 보고 싶으면

>git help --config

혹은

>git --config help

어떤 명령이든 같은 형식으로 하면 된다. 예를 들어 'git add'의 도움말을 보려면

>git add --help

or

>git help add

처럼 하면 될 것이다. 언제부터인지 모르지만 최신의 git 버전을 설치했다면 도움말이 기본브라우저가 열리며 링크된 페이지를 보여준다.

## 실습 시나리오

실습을 진행하는데 있어 전제되어야 할 것들이 있다.

### 시나리오 1 : Local에서 작업중인 데이터를 git repository로 initialize 하여 git repository로 만드는 방법

현재 local disk의 어떤 directory 안에 Cloned-Repo, Slides, Local-Repo, remote_repo.git 이라는 4개의 폴더가 있다.

### Local-Repo 폴더에는 .project, calc.py라는 파일이 있다.

.project
calc.py

>git init

- 로 initialize하고 나면 .git이라는 폴더가 생긴다.

- Initialize한 git을 취소하는 방법

엄밀히 말해, 취소가아니라 '.git directory를 지우는 것이다.

>**rm -rf .git**

-rf option은 묻지도 따지지도 않고 지정한 파일이나 폴더를 무조건 삭제하는 명령이므로 think twice해야만 할 것이다.

- Before first commit

>git status

- git status로 상태를 확인한다.

>touch .gitignore

```
Glob 패턴은 정규표현식을 단순하게 만든 것으로 생각하면 되고 보통 쉘에서 많이 사용한다. 애스터리스크(*)는 문자가 하나도 없거나 하나 이상을 의미하고, [abc]는 중괄호 안에 있는 문자 중 하나를 의미한다(그러니까 이 경우에는 a, b, c). 물음표(?)는 문자 하나를 말하고, [0-9]처럼 중괄호 안의 캐릭터 사이에 하이픈(-)을 사용하면 그 캐릭터 사이에 있는 문자 하나를 말한다.

다음은 .gitignore 파일의 예이다:

# a comment - 이 줄은 무시한다.
# 확장자가 .a인 파일 무시
*.a
# 윗 줄에서 확장자가 .a인 파일은 무시하게 했지만 lib.a는 무시하지 않는다.
!lib.a
# 루트 디렉토리에 있는 TODO파일은 무시하고 subdir/TODO처럼 하위디렉토리에 있는 파일은 무시하지 않는다.
/TODO
# build/ 디렉토리에 있는 모든 파일은 무시한다.
build/
# `doc/notes.txt`같은 파일은 무시하고 doc/server/arch.txt같은 파일은 무시하지 않는다.
doc/*.txt
# `doc` 디렉토리 아래의 모든 .txt 파일을 무시한다.
doc/**/*.txt
```

### WHERE ARE WE NOW

ADD FILES TO STAGING AREA
>git add -A
>git status

- 1개의 파일을 add할 경우

>git add .gitignore  
>git status

새파일이나 수정된 파일을 한꺼번에 add 하는 경우
>git add -A
>git status

REMOVE FILES FORM STAGING AREA 는
>git reset

1개 파일의 staging을 취소하는 경우
>git reset [filename]

예를 들어 .gitignore의 staging을 취소하려면
>git reset calc.py >git status

폴더(working directory) 전체를 reset할 경우 >git reset

OUR FIRST COMMIT
>git add -A
>git commit -m "Initial commit"
>git status >git log

git log는 commit한 파일에 대한 hash code, author, date, commit message 등을 보여준다
CLONING A REMOTE REPO 
>git clone &lt;url> &lt;cloneTargeFolderPath>
>git clone ../remote_repo.git .  
>git clone https://github.com/[usernaem]/[reponame] .

git clone &lt;url> . 에서 '.'은 현재디렉터리를 뜻한다.
base directory로 가서 cloned-repo로 들어간다.
>cd ..

>ls >cd Cloned-Repo

>ls -al

local repo에서 다른 directory로 'clone' 하는 방법
>git clone ../remote.git .

VIEWING INFORMATION ABOUT THE REMOTE REPOSITORY
>git remote -v
>git branch -a

### PUSHING CHANGES

COMMIT CHANGES LIKE WE DID PREVIOUSLY
>git diff
>git status
>git add -A
>git commit -m "Modified multiply function"

### THEN PUSH:

>git pull origin mster
>git push origin master
>git add -A > git commit -m "Multiply Function"
>git push -u origin calc-divide > git branch -a
>git checkout master
>git branch --merged >git merge calc-divide
>git push origin master

### branch 지우는 방법

>git branch -d calc-divide
>git branch -a

(-a 는 List all remote branches )

### remote 의 calc-divide branch 지우는 방법

>git push origin --delete calc-divide
이후에  
>git branch -a 로 확인한다.

calc.py를 수정한 후에
>git status
>git add -A >git commit -m "Subtract"
>git push -u origin subtract
>git checkout master
>git pull origin master
>git merge subtract
>git push origin master