# 파일에서 문자열을 찾습니다.

* 우선 grep로 bash terminal에서 찾는 것은 포기하고 findstr 먼저...

## 모든 하위 폴더 포함하여 확장자 'txt'인 파일들에서 '대한민국' 이라는 문자열 찾기

* 예제
>findstr /s /i "대한민국" ./*

FINDSTR [/B] [/E] [/L] [/R] [/S] [/I] [/X] [/V] [/N] [/M] [/O] [/P]
         [/F:파일][/C:문자열] [/G:파일] [/D:디렉터리 목록] [/A:색 속성] [/OFF[LINE]]
         문자열 [[드라이브:][경로]파일이름[ ...]]

  /B         패턴이 행의 첫 부분에 있는지를 비교합니다.
  /E         패턴이 행의 끝부분에 있는지를 비교합니다.
  /L         찾는 문자열을 글자 그대로 사용합니다.
  /R         찾는 문자열을 정규식으로 사용합니다.
  * /S         현재 디렉터리와 모든 하위 디렉터리에서 일치하는 파일을 찾습니다.
  * /I         찾을 때 대/소문자를 구별하지 않습니다.
  
  /X         정확히 일치하는 줄만 보여줍니다.
  /V         일치하는 텍스트가 없는 줄만 보여줍니다.
  /N         일치하는 각 줄 앞에 줄 번호를 보여줍니다.
  /M         파일에 일치하는 텍스트가 있으면 파일 이름만 보여줍니다.
  /O         일치하는 각 줄 앞에 문자 오프셋을 보여줍니다.
  /P         인쇄할 수 없는 텍스트가 포함된 파일은 건너뜁니다.
  /OFF[LINE] 오프라인 속성 세트 파일을 건너뛰지 않습니다.
  /A:속성    색 속성을 두 자리 16진수로 지정합니다. "color /?"를 참조하십시오.
  /F:파일    지정된 파일에서 파일 목록을 읽습니다('/'는 콘솔에 해당됩니다).
  /C:문자열  지정된 텍스트를 글자 그대로 찾는 문자열로 사용합니다.
  /G:파일    지정된 파일로부터 찾는 텍스트를 받습니다('/'는 콘솔에 해당됩니다).
  /D:디렉터리    디렉터리 목록을 구분하는 세미콜론(;)를 찾습니다.
  문자열     찾을 텍스트.
  [드라이브:][경로]파일이름
             찾을 파일을 지정합니다.

/C 옵션을 사용한 경우가 아니면, 찾는 문자열을 여러 개 지정할 때
공백으로 분리하십시오. 예를 들면, 'FINDSTR "hello there" x.y' 명령을
입력하면 파일 x.y에서 "hello"나 "there"을 찾습니다.
반면에 'FINDSTR /C:"hello there" x.y' 명령을 입력하면 파일 x.y에서
"hello there"을 찾습니다.

정규식에 대한 참고 사항:
  .         와일드카드: 모든 문자
  *         반복: 문자나 클래스에 대하여 0번 이상 반복
  ^         행 위치: 행의 앞부분
  $         행 위치: 행의 끝부분
  [클래스]  문자 클래스: 세트에 있는 문자
  [^클래스] 역 클래스: 세트에 없는 문자
  [x-y]     범위: 특정 범위에 있는 문자
  \x        이스케이프: 메타 문자 x를 문자 그대로 사용
  \<xyz     단어 위치: 단어의 앞부분
  xyz\>     단어 위치: 단어의 끝부분

Findstr에서 사용 가능한 정규식은 온라인 명령을 참조하십시오.



기본사용법 : findstr /?
■ PoolMon.exe 를 사용할때.. 커널드라이버 Tag 검색
findstr /m /l "BcMc" c:\windows\system32\drivers\*.sys
 
■ 특정 문자열 검색
findstr 문자열1 document.txt
findstr "문자열1 문자열2" document.txt 
findstr /c:"똑같은 문자열만 찾아주세요" document.txt
 
■ W로 시작해서 ws로 끝나는 문자열 검색
findstr "W.*ws" document.txt
 
■ C: 드라이브와 하위폴더에서 문자열 검색 (대소문자 불문)
findstr /s /i 문자열1 C:\*.*
 
■ 파일목록내에 문자열 검색하기
findstr /f:C:\files.txt /m /l "BcMc"
findstr /g:argument.txt /f:files.txt


[출처] Window FindStr 사용방법 |작성자 네프





사용 방법 :

 

findstr "찾고싶은 문자" *  --> findstr "check" *

 

이렇게 하면 현재 위치한 디렉토리에서만 모든 파일에서 check가 포함도니 라인을 출력해 줍니다.

그런데 이게 몇번째 라인인지 알 수가 없으니 grep 처럼 나타내 주기 위해서 /N 옵션을 붙여 줍니다.

 

findstr /N "check" *

 

하위 폴더까지 검색하고 싶다? 

 

findstr /N /S "check" *

 

모든 파일을 다 검색하니 느려터진다. 특정 파일만 필터해서 검색하고 싶다면?

 

findstr /N /S "check" *.txt

 

요런 식으로 사용하면 된다.

 

결과가 너무 많아! 파일로 천천히 보고 싶어!

 

findstr /N /S "check" *.txt > findstr.log

 

> 다음 파일명은 취향것. 이렇게 되면 현재 디렉토리에 findstr.log 파일에 다 기록된다.