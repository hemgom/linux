# 목적
'Linux' 및 관련 정보 중, 기본적인 부분을 이곳에 정리하고자 한다.
<br/><br/><br/><br/>

# 명령어
## clear
터미널을 사용하다 보면 어느새 화면이 명령어와 출력 결과로 가득차게 된다. 이 때 `터미널 화면을 정리하기 위해 사용`하는 명령어이다.
<br/><br/><br/>

## pwd
`pwd` 는 `'Print Working Directory(작업 중인 디렉토리 출력)'` 의 약자로 사용자가 `현재 위치한 디렉토리를 확인할 때 사용`하며, 사용 시 `현재 위치한 디렉토리의 전체 경로`를 알려준다.
```
user@server:~$ pwd
/home/user		(현재 사용자가 위치한 디렉토리 경로)
```
`CLI(Command Line Interface)` 를 사용하기 때문에 현재 위치를 확인 할 수 있는 `pwd` 는 매우 중요하니, 반드시 잊지말자!
<br/><br/><br/>

## cd
`cd` 명령어는 `Change Directory(디렉토리 변경)` 의 약자로 `현재 위치에서 다른 디렉토리로 이동`하고 싶을 때 사용한다.
<br/><br/>

### 사용 예시 - ①
```
user@server:~/test$ pwd
/home/user/test
user@server:~/test$ cd
user@server:~$ pwd
/home/user		(현재 사용자의 홈 디렉토리 경로)
```
단순하게 `cd` 명령어만을 사용할 경우 사용자의 `홈 디렉토리(/home/사용자명)` 로 이동하게 된다.
<br/><br/>

### 사용 예시 - ②
```
user@server:~$ pwd
/home/user
user@server:~$ cd test
user@server:~/test$ pwd
/home/user		(이동 후 현재 디렉토리 경로)
```
`cd 디렉토리명(or 경로)` 을 사용할 경우 `하위 디렉토리(or 경로의 최하위 디렉토리)로 이동` 하게 된다. 
- 디렉토리가 `/home/user/test/test2` 같이 구성되어 있고, 현재 위치가 `user` 디렉토리 일 때, `test2` 디렉토리로 한 번에 이동하고 싶다면 반드시 경로로 입력해야 한다. 경로가 아닌 디렉토리명을 사용하면 `user` 디렉토리에서는 해당 디렉토리를 찾을 수 없다는 오류 메시지가 출력된다.
- 이동하고자 하는 `경로(위치)` 를 지정할 때, 2가지 방식으로 작성할 수 있다.
	1. 절대경로 : `root 디렉토리(/)` 부터 이동하고자 하는 디렉토리까지의 경로, 경로의 시작을 최상위 디렉토리인 `root` 로 고정한다.
	2. 상대경로 : 경로의 시작은 현재 위치한 디렉토리가 되며, 현재 위치에서 타겟 디렉토리까지의 경로를 말한다. 당연하지만 같은 디렉토리로 이동해도 현재 위치가 다르면 지정할 경로가 계속 바뀐다.
<br/><br/>

### 사용 예시 - ③
```
user@server:~/test$ pwd
/home/user/test
user@server:~/test$ cd
user@server:~$ pwd
/home/user		(현재 디렉토리의 상위 부모 디렉토리로 이동한 경로)
```
`cd` 사용시 경로 외에도 사용되는 것이 `..` 이다. `현재 디렉토리의 부모(상위) 디렉토리의 의미` 를 가지며, `cd ..` 사용시 현재 위치한 디렉토리의 부모 디렉토리로 이동하게 된다.
- 참고 : `.` 도 사용하는데, `현재 디렉토리` 를 의미한다.
<br/><br/><br/>

## mkdir
`mkdir` 는 `MaKe DIRectory(디렉토리 만들기)` 의 약어로 `새로운 디렉토리를 생성`할 때 사용하는 명령어이다.
<br/><br/>

### 사용 예시 - ①
```
user@server:~$ pwd
/home/user
user@server:~$ mkdir test
user@server:~$ ls
test		(새로 생성한 'test' 디렉토리)	
```
`mkdir 디렉토리명` 을 사용하면 현재 위치한 디렉토리의 하위에 새로운 디렉토리를 생성한다. 생성에 성공하면 아무런 내용도 출력되지 않는다. 
<br/><br/>

### 사용 예시 - ②
```
user@server:~/test$ pwd
/home/user/test
user@server:~/test$ mkdir ../test2
user@server:~/test$ cd ..
user@server:~$ ls
test  test2		(/home/user 디렉토리 아래에 생성된 두 디렉토리)	
```
`mkdir 경로` 의 방식도 사용가능하다. 상대경로 방식으로 `/home/user/test` 의 위치에서 상위 디렉토리인 `user` 에 신규 디렉토리를 생성하도록 응용 해보았다.
- `mkdir ../test2` : `..` 을 통해 상위 디렉토리로 생성 위치가 변경되고 `/test2` 를 통해 신규 디렉토리의 이름을 설정한 것이다.
- 의도한대로 디렉토리가 생성되었는지 확인하기 위해 `cd ..` 를 통해 `/home/user` 로 이동한 후 `ls` 로 현재 디렉토리에 존재하는 디렉토리들을 확인해보니, 기존의 `test` 와 새로 생성한 `test2` 가 있는걸 확인할 수 있었다.
- 해당 실습을 통해 `현재 위치와 다른 디렉토리에도 신규 디렉토리를 생성할 수 있다는 걸 파악`할 수 있었다.
- 상대경로를 통한 실습을 한 후 `절대경로를 사용`해봤는데, `디렉토리를 생성할 수 없다는 오류 메시지가 출력` 되었다.
<br/><br/><br/>

## ls
`ls` 는 `LiSt(목록)` 의 약어이며, 현재 위치한 디렉토리에 존재하는 디렉토리 및 파일의 목록을 출력하는 명령어이다.
<br/><br/>

### 사용 예시 - ①
```
user@server:~$ pwd
/home/user
user@server:~$ ls
test  test2  testText.txt		(현재 디렉토리에 존재하는 디렉토리&파일 명 목록)
```
`ls` 를 사용하니 `/home/user` 디렉토리에 존재하는 디렉토리와 파일들의 이름 목록이 출력된다. 디렉토리의 경우 파란색으로 표시되며 파일의 경우 흰색으로 출력되었다. 이름만으로 디렉토리와 파일을 구별할 수 없기에 폰트색상으로 구별하는 듯 하다.
- `ls -a` : `-a` 속성(파라미터)을 사용하면 `숨긴 파일을 포함한 모든 파일` 들의 이름 목록을 출력한다.
- `ls -l` : `-l` 속성을 사용하면 파일들의 이름뿐만 아니라 자세한 정보(권한, 연결 파일 수, 수정일 등)가 담긴 목록을 출력하게 된다.
- 참고 : 두 가지 속성을 적용할 경우 `ls -l -a`, `ls -la`, `ls -al` 중 하나를 선택해 사용하면 된다. 세 가지 방식 모두 같은 결과(현재 디렉토리의 모든 파일의 자세한 정보를 가진 목록)가 출력되는 것을 확인하였다.
<br/><br/>

### 사용 예시 - ②
```
user@server:~/test$ pwd
/home/user/test
user@server:~/test$ ls ..
test  test2  testText.txt		('test' 상위 디렉토리에 존재하는 디렉토리&파일 명 목록)
```
`ls 경로` 를 사용하면 경로의 해당 디렉토리에 존재하는 파일들의 목록을 출력한다.
- 예시에서는 상대경로를 사용하였는데, 추가적으로 절대경로를 사용해보니 정상적으로 목록이 출력되는 것을 확인하였다.
- 경로를 사용할 때도 `ls` 명령어의 속성을 사용할 수 있는데 `ls .. -l`, `ls -l ..` 두 방식 모두 목록을 정상 출력하는 걸로 보아 경로와 속성을 적는 순서는 상관 없는 것 같다.
<br/><br/>

### 사용 예시 - ③
```
user@server:~$ pwd
/home/user
user@server:~$ ls t*
testText.txt

test:
lowdir  lowText.txt

test2:
```
`ls t*` 를 사용하면 `*` 앞에 존재하는 문자(들)로 시작하는 파일명을 가진 모든 파일들의 목록을 출력한다. 출력 순서는 파일, 디렉토리 순서로 출력되는 듯 하다. 디렉토리의 경우 `이름:` 형식으로 출력되며, 디렉토리의 하위 파일들도 같이 출력된다.
- `ls *t` : `t` 로 끝나는 파일명을 가진 파일들만 목록에 출력된다.
- `ls *.txt` : `txt` 확장자를 가진 파일들만 목록에 출력된다.
<br/><br/><br/>

## touch
`touch` 는 크기가 `0`인 새 파일을 생성하며, 이미 같은 이름과 확장자를 가진 파일이 존재한다면 최종 수정 시간을 변경한다.
```
user@server:~$ touch testText.txt
user@server:~$ ls
test  test2  testText.txt		(새로 생성한 빈 파일 확인)
```
예시에는 기본 `ls` 명령어로 새 파일의 생성을 확인했지만, 실습에서 `ls -l` 을 사용해 확인해보니 새 파일의 크기가 `0` 인 것을 확인하였다. 추가적으로 `touch testText.txt` 를 한 번더 실행한 결과 `testText.txt` 의 수정일이 변경된 것 또한 확인했다.
<br/><br/><br/>

## rm
`rm` 은 `ReMove(삭제)` 의 약어로 파일을 삭제한다. `rm` 명령어를 실행하기 위해서는 권한이 있어야 하며, `root(최고 권한 사용자)` 사용자는 해당 명령어 사용에 제약이 없다.
```
user@server:~$ ls
test  test2  testText.txt
user@server:~$ rm testText.txt
user@server:~$ ls
test  test2		('testText.txt' 파일 삭제 확인)
```
`rm 파일` 을 사용하면 해당 파일을 삭제(물론 사용자가 권한이 있다면) 한다. 기본적으로는 삭제 여부를 확인하지 않으므로 기본 속성은 `rm -f` 인 것 같다.
- `rm -i 파일` : 파일 삭제 전에 삭제 여부를 확인한다. `y` 입력시 삭제가 진행되며 `n` 를 입력하면 삭제가 취소된다.
- `rm -f 파일` : 삭제 여부를 묻지 않고 삭제를 진행한다.
- `rm -r 디렉토리` : 디렉토리를 삭제하며, 디렉토리에 하위 디렉토리 또는 파일을 모두 삭제한다.(무척이나 위험한 옵션, 사용하지 말자)
<br/><br/><br/>

## rmdir
`rmdir` 은 `ReMove DIRectory(디렉토리 삭제)` 의 약어로 디렉토리를 삭제한다. 해당 디렉토리에 대한 권한이 있어야 삭제 가능하며, 또한 해당 디렉토리가 비어 있어야 한다.
```
user@server:~$ ls *
testText.txt

test:
low

test2:
user@server:~$ rmdir test2
user@server:~$ ls
test  testText.txt		('test2' 디렉토리 삭제 확인)
```
`rmdir 디렉토리명` 을 사용하면 `빈 디렉토리` 가 삭제된다. 디렉토리에 파일 또는 하위 디렉토리가 존재한다면 오류 메시지가 출력된다.
- `rm -r 디렉토리명` 을 사용하는 경우 해당 디렉토리 안에 존재하는 모든 파일 및 디렉토리가 함께 삭제 되기 때문에 `rmdir` 을 사용해 디렉토리를 삭제하는 것이 좀 더 안전한 것 같다.
<br/><br/><br/>

## cp
`cp` 는 `CoPy` 의 약자로 사용시 `파일 또는 디렉토리를 복사`한다. 복사한 파일의 소유권은 복사한 사용자가 가지게 되므로 명령을 실행하기 위해서는 복사하고자 하는 파일의 읽기 권한이 필요하다.
<br/><br/>

### 사용 예시 - ①
```
user@server:~/test$ cp ../testText.txt ../copyTest.txt
user@server:~/test$ cd ..
user@server:~$ ls
testText.txt  copyTest.txt		(복시된 파일이 있는지 확인)
```
`cp` 의 가장 기본적인 사용 법은 `cp 복사대상명 복사결과명` 이다. 해당 예시는 `현재 위치와 다른 곳에 있는 파일을 다른 위치에 복사하는 식으로 실습한 내용`이다. `복사 대상 파일` 과 `복사 결과 파일` 에는 파일명 뿐만 아니라 상대경로 및 절대경로를 사용 가능하다.
<br/><br/>

### 사용 예시 - ②
```
user@server:~$ ls *
test:
copy.txt  low
user@server:~$ cp -r test test2
user@server:~$ ls *
test:
copy.txt  low

test2:
copy.txt  low		(복사한 디렉토리 확인)
```
`cp` 명령어로 디렉토리를 복사하기 위해서는 `-r` 속성을 사용해야 한다. 디렉토리 복사시, 복사하는 대상 디렉토리에 파일 및 하위 디렉토리까지 함께 복사한다.
<br/><br/><br/>

## mv
`mv` 는 `MoVe` 의 약자로 파일 또는 디렉토리의 이름을 변경하거나 위치를 옮길 때 사용한다.
<br/><br/>

### 사용 예시 - ①
```
user@server:~$ ls *
test:
test.txt

test2:
user@server:~$ mv test/test.txt /home/user/test2
user@server:~$ ls *
test:

test2:
test.txt
```
`mv 옮길대상 옮길위치` 를 사용하면 `대상(파일, 디렉토리)을 지정한 위치로 옮길 수`가 있다. 대상의 `파일명(또는 디렉토리명)`을 적어도 되고 다른 위치의 대상을 옮길 경우 `경로(상대, 절대 모두)로 지정`이해도 정상 실행된다. 
- 한 번에 다수의 파일(또는 디렉토리)들을 한 위치로 옮길 수 있다. `mv 대상1 대상2 위치` 같은 방식으로 명령어를 작성하면 된다.
<br/><br/>

### 사용 예시 - ②
```
user@server:~$ ls *
test:
targetDir

test2:
user@server:~$ mv test/targetDir test2/mvDir
user@server:~$ ls *
test:

test2:
mvDir		(위치와 이름을 동시에 변경한 디렉토리 확인)
```
`mv 대상 변경이름` 을 사용하면 대상의 파일명(또는 디렉토리명)을 바꿀 수 있다. `mv 대상경로 변경경로(+변경이름)` 을 사용하면, 위의 예시처럼 위치 변경과 이름 변경을 동시에 바꿀 수도 있다.
- 사실 직접 사용해본 바, 이름변경 기능은 존재하지 않는 경로를 인식해서 적용되는 것 같다. `변경경로에 대한 부분을 오류 없이 잘 지정`할 필요가 있는 듯 하다. 
<br/><br/><br/>

## sudo
`sudo` 명령어는 `sudo 명령어` 방식으로 사용하며, `root` 사용자가 아닌 사용자가 `root` 권한으로 명령어 실행이 필요할 때 사용하는 명령어이다. 우리가 흔히 윈도우 환경에서 `관리자 권한으로 실행` 기능을 사용하는데 이와 같거나 비슷한 기능을 하는 명령어인 것 같다.
<br/><br/><br/>

## nano
`nano` 명령어를 사용하면 `문서 작성 에디터` 가 실행된다. 해당 에디터로 `문서를 작성`할 수 있으며 `기존의 문서를 읽거나 수정`, `새로운 문서 작성 및 저장` 등의 기능을 가지고 있다. 여러 기능이 있어 이 부분은 추후에 직접 문서 작업을 해보고 정리하도록 하겠다.
<br/><br/><br/>

## help
`help` 는 도움말 명령어로 사용시 사용가능한 명령어들과 명령어들의 속성(간략하게)들을 출력해 알려준다. `명령어 --help`를 사용할 경우 해당 명령어에 대한 설명과 사용가능한 속성에 대한 자세한 설명을 출력해 알려준다.
<br/><br/><br/>

## man
`man` 은 `MANual` 의 약자로 설명서 페이지를 볼 수 있는 명령어 이다. `man 명령어` 를 사용하면 지정한 명령어에 대한 설명서 페이지를 출력하여 해당 명령어에 대한 상세한 정보를 알 수 있다. 위에서 다룬 `help` 명령어보다 더 자세한 설명을 볼 수 있다.
- 설명서 페이지는 다양한 키 입력으로 이동하면 볼 수 있지만 직접해본 바로는 스크롤 느낌이 나는 `방향키(위, 아래)` 가 좀 더 보기 편했다.
<br/><br/><br/><br/>

# Package Manager
`Linux` 에서 필요한 소프트웨어를 다운로드 및 업데이트 할 때 사용된다. 마치 우리가 늘 사용하는 `앱 스토어` 와 같은 개념으로 이해하면 될 듯 하다. 종류는 대표적으로 `apt`, `yum` 등이 있다.
<br/><br/>

## apt
실습으로는 `apt` 패키지 매니저를 먼저 사용해 보았다. 명령어를 실행하니 권한이 되지 않아 명령어를 수행할 수 없어다. 그래서 `sudo` 명령어를 추가해 `root` 권한으로 명령어를 실행하니 정상 작동하였다. `apt` 또한 옵션을 가지고 있는데 해당 옵션은 명령어에 따라 기본 값이 자동 적용되어 실행되니 해당 문서에서는 명령어에 대해 정리하도록 하겠다.
<br/><br/>

### 명령어
많은 명령어가 있으나 필수거나 자주 사용되는 명령어에 대해 먼저 정리하고, 추후에 추가적으로 사용한 명령어에 대해서 정리하도록 하겠다.
- `update` : 현재 패키지 리스트를 최신 패키지에 대한 정보로 업데이트 한다. 정보만 업데이트 할 뿐 패키지들의 버전은 그대로 유지된다. `sudo apt update`, `sudo apt-get update` 방식으로 사용한다.
- `search` : 현재 가지고 있는 패키지 목록에서 검색어에 해당하거나 관련된 패키지 목록을 출력한다. `sudo apt-cache search 검색어` 방식으로 사용한다.
- `install` : 지정한 패키지를 설치한다. `sudo apt-get install 패키지명`, `sudo apt install 패키지명` 방식으로 사용한다.
- `upgrade` : 지정한 패키지를 업그레이드 한다. `sudo apt-get upgrade 패키지명`, `sudo apt upgrade 패키지명`  방식으로 사용한다.
- `remove` : 지정한 패키지를 삭제한다. `sudo apt-get remove 패키지명`, `sudo apt remove 패키지명` 방식으로 사용한다.
<br/><br/><br/><br/>

# 다운로드
우리는 늘상 인터넷에서 많은 것들을 다운로드 받는다. 그럼 리눅스 환경에서는 인터넷 상에서 다운로드를 어떻게 받을까?
<br/><br/>

## wget
다운로드 경로를 통한 다운로드 방식을 제공하는 명령어이다.
```
user@server:~$ wget -O 저장명 다운로드-URL
```
위와 같은 방식으로 인터넷 상의 정보를 다운로드 받을 수 있다. `-O` 옵션을 사용하면 파일명을 지정해 다운로드가 가능하다.
<br/><br/><br/>

## git
`Github` 는 많은 사람들이 버전관리를 위해 사용하지만 사실 오픈소스의 근간이 되는 곳이다. 필요한 오픈 소스를 다운로드하기 위해서 해당 명령어가 사용된다. (물론 git 패키지가 설치되어 있어야 한다.)
```
user@server:~$ git clone 레포지토리-URL 저장위치(경로)
```
위와 같은 방식으로 깃허브의 레포지토리 복사본을 다운로드 받을 수 있다.
<br/><br/><br/><br/>

# 실습 환경
- 운영체제 : __Ubuntu Server__ - 22.04.4 LTS
	- 가장 최신 버전인 24.04 LTS 를 사용하고자 했으나 현재 문제가 많다고 하여 이전 버전을 사용하고 있다.
- 가상머신 : __VirtualBox__ - 7.0.20
<br/><br/><br/><br/>

# 참고 문서
- [생활 코딩 - Linux](https://www.inflearn.com/course/%EC%83%9D%ED%99%9C%EC%BD%94%EB%94%A9-%EB%A6%AC%EB%88%85%EC%8A%A4-%EA%B0%95%EC%A2%8C/dashboard)
- [Linux 명령어 - 한빛출판네트워크(실습 결과와 다른 내용이 있음, 참고에 주의!)](https://www.hanbit.co.kr/channel/category/category_view.html?cms_code=CMS6390061632)