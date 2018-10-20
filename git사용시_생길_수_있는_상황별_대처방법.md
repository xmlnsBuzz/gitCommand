# 초보자가 git을 사용할 때 생길 수 있는 상황별 대처법

* 나는 원래 어린 꼬마에게도 반말을 쓰지 않는다. 하지만 이 문서가 메뉴얼의 일종이므로 존대말은 하지 않겠다.

## 목적

누구나 경험하는 것이지만, 초보자들이 git을 사용하다 보면 수 많은 문제에 부딪친다. 나 자신이 경험한 내용을 토대로 이런 상황들을 정리해 보았고, 내가 겪어보지 못 한 새로운 상황이 생기면 계속 추가해 나갈 것이다.

## 초보자에 대한 충고

git 초보자가 가장 많이 겪는 착각은 '자신의 컴퓨터에 있는 데이터(줄여서 'local'dlfk gkrpTek.)'와 'github같은 git service제공업체'(줄여서 server라 하겠고, git service는 github말고도 BitBucket이나 gitlab같은 업체등이 있다.)의 자기 repository(줄여서 'repo'라 하겠다.)간의 위치를 혼동하는 것이라 생각한다. 예를 들어 local에서 'add', 'commit', 'branch'같은 명령으로 작업을 한 것이 server에도 똑 같이 생겼을 것으로 착각하지만, 'push' 등의 명령을 사용하여 local의 데이터를 server로 올렸을 때 비로소 내가 작업한 내용이 server의 repo에 저장되는 것이다.

그 이전에는 commit등의 명령을 아무리 많이 써도, 그건 그저 local에서 벌어지는 일일 뿐인 것이다. 이 점을 명심해 두면 많은 도움이 될 것이다.

## 내가 작업하는 환경

나는 현재 [git](https://git-scm.com)를 설치했고, Code editor는 [Visual Studio Code](https://code.visualstudio.com)를 사용하고 있다. Editor는 sublime text나 Atom 등 좋은 것들이 많지만 내가 그 걸 다 써보지 않은 관계로 각자 알아서 대처하리라 생각한다. 하지만 명령은 주로 git bash(git을 설치하면 자동으로 설치된다.) terminal에서 하므로 별 문제는 없을 것이다.

## 여러분이 갖춰야 될 환경

위의 git이 설치되어 있고 'github'에 가입해서 repo를 만들었다고 가정한다.

## 생길 수 있는 상황들

이제 본론으로 들어가자.

### commit이 안 되는 경우

commit이 안 되는 주 원인 중 하나는

* 현재 local에 아무런 **변경사항**{문서를 새로 만들지도 않았고 기존의 문서를 수정(modify)해서 저장(**문서를 수정했어도 저장하지 않았다면 git은 아무런 수정도 없는 것으로 간주한다.**)하지 않았을 경우}도 없이 commit하는 경우

commit은 변경사항이 없을 때는 절대 발생되지 않는다.

* local 문서에 변경사항이 생겼지만 'add' 명령으로 

git은 햐

add는 index에 추가하는 것.