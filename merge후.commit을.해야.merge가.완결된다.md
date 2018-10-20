# Merge를 해서 브랜치를 합친 후에는 commit을 해야 완결된다

## 용법

* merge는 merge명령을 하는 시점에서 '어떤 브랜치가 wd(working branch)냐'가 기준이다. 예를 들어 현재 master 브랜치 상태에서 'aaa' branch를 merge하고 싶어서,

> git merge aaa

* 라고 했다면 'master'브랜치와 'aaa'브랜치가 merge로 통합된 것이다. 위의 명령으로 merge가 되었다면 git bash prompt 끝에 '**(master | MERGED)**'가 표시 될 것이다.

하지만 이 것으로 완결이 아니다, 따라서 이 것을 완결시키려면 commit을 한다.

> git commit -m "master와 aaa를 merge 했음"

위의 결과로 prompt 끝에 'MERGED'가 없어지고 (master)가 표시되었다면 이로써 merge가 완결된 것이다.