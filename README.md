# 과제2
#### 20223214진보미_컴퓨터공학과
***
# 리눅스 명령어
+ #### top 
##### top 명령어를 사용하여 시스템 사용량을 실시간으로 확인 할 수 있다.
##### ***ef)*** *로그인된 사용자 수*, *uptime결과*, *프로세스 수치*, *CPU정보* *등* ...
 
##### 사용예시 : 옵션 없이 명령어를 실행하면 interval간격으로 화면을 갱신하며 정보를 보여줌.
##### 실행결과
<img src ="https://user-images.githubusercontent.com/106435720/171386846-b3c72b00-70f3-4478-9eb8-abff81377d96.png" width = "680" height = "480"> 
[실행결과 이미지 출처](https://blog.naver.com/jjune095/221242495248)

##### top[옵션]
|[옵션]|설명|
|------|---|
|-b |배치모드로 정보를 출력한다. 실시간 상화 대화형 모드로 정보를 화면에 일렬로 출력한다.|
|-d |지정한 시간(delay초)의 간격으로 정보를 업데이트하여 출력한다.|
|-i |토글값이 off일 때, idle 프로세스나 좀비 프로세스 정보를 출력하지 않는다.|
|-n |지정한 시간(num)만큼 업데이트 정보를 출력한다.|
|-p |지정한 프로세스 ID(pid)의 정보만을 출력한다.|
|-q |시간의 간격 없이 계속하여 업데이트 정보를 출력한다.|
|-s |몇 개의 대화식 명령을 비활성화한다.(시큐어 모드)|
|-S |누적된 정보를 출력한다.(comulative 모드)|

##### top 실행 후 명령어
1. shift + p : CPU사용률 내림차순
2. shift + m : 메모리 사용률 내림차순
3. shift + t : 프로세스가 돌아가고 있는 시간 순
4. k : kill. k 입력 후 PID번호 작성. signal은 9
5. f : sort filed 선택 화면 - q 누르면 RES순으로 정렬
6. a : 메모리 사용량에 따라 정렬
7. b :  Batch 모드로 작동
8. 1 : CPU Core별로 사용량 보여줌

+ #### ps
##### ps(process status)를 사용하면 현재 실행중인 프로세스 목록을 확인할 수 있습니다.
#####실행결과

```
$ps

PID TTY TIME CND

3134pts/1    00:00:00 bash
15027 pts/1  00:00:00 ps
```

##### 프로그램의 정보
|[옵션]|설명|
|------|---|
|-V|버전 정보를 출력한다.|
|L |모든 형태의 지시자를 출력한다.|
|--help|사용법을 출력한다.|
|--info|디버깅 정보를 출력한다.|
|--version|버전 정보를 출력한다.|
##### 전체 프로세스와 관련된 옵션
|[옵션]|설명|
|------|---|
|-A|모든 프로세스를 출력한다.|
|-N|-A 옵션과 비슷하나 ps프로세스를 제외하고 출력한다.|
|-a|세션 리더 및 터미널에 속하지 않는 프로세스를 제외하고 출력한다.
|-d|세션 리더를 제외한 모든 프로세스를 출력한다.|
|-e|커널 프로세스를 제외한 모든 프로세스를 출력한다.|
|T|현재 터미널에서의 모든 프로세스를 출력한다.|
|a|현재 터미널의 사용자 고유 프로세를 출력한다.|
|r|현재 실행 중인 프로세스를 출력한다.|
|x|터미널이 없는 프로세를 출력한다.|

+ #### jobs
##### jops는 작업이 중지된 상태, 백그라운드로 진행 중인 작업 상태, 변경 되었지만 보고되지 않은 상태 등을 표시하는 명령어다. 
##### 사용법 : jops[옵션] [job ID] , jobs-x command[args]

```
$jobs
[1]- 정지됨          vi
[2]+ 정지됨          tail -f /var/log/messages
```
```
$jobs -l
[1]- 4908 Stopped (tty output)       vi
[2]+ 4987 Stopped                    tail -f /var/log/messages
```

1. -I : 프로세스 그룹 ID를 state필드 앞에 출력한다.
2. -n : 프로세스 그룹 중에 대표 프로세스 ID를 출력한다.
3. -p : 각 프로세스 ID에 대해 한 행씩 출력한다.
4. command : 지정한 명령어를 실행한다.

##### jobs 명령어로 확인할 수 있는 세션의 상태값
|상태|설명|
|------|---|
|Running|작업이 일시 중단되지 않았고 종료하지 않고 계속 진행 중임을 뜻한다.|
|Done   |작업이 완료되어 0을 반환하고 종료했음을 뜻한다.|
|Done(code)|작업이 정상적으로 완료했으며, 0이 아닌 코드를 반환했음을 뜻한다.|
|Stopped|작업이 일시 중단됨을 뜻한다.|
|Stopped(SIGTSTP)|SIGTSTP 신호가 작업을 일시 중단했음을 뜻한다.|
|Stopped(SIGSTOP)|SIGSTOP 신호가 일시 중단했음을 뜻한다.|
|Stopped(SIGTTIN)|SIGTTIN 신호가 작업을 일시 중단했음을 뜻한다.|
|Stopped(SIGTTOU)|SIGTTOU 신호가 작업을 일시 중단했음을 뜻한다.|

+ ##### KILL
##### kill명령어는 프로세스에 종료 시그널을 보낸다. 
##### 사용법 : kill[-s시그널][-a]pid, kill-l[시그널]
<img src = "https://user-images.githubusercontent.com/106435720/171396601-7bc02129-72e3-46ab-9233-4d2e12737bd5.jpg" width = "300" height = "200">

1. pid ··· : 종료시킬 프로세스 ID나 프로세스 이름을 지정한다.
2. -s : 전달할 시그널의 종류를 지정한다. 여기에는 시그널 이름이나 번호를 써준다.
3. -l : 시그널로 사용할 수 있는 시그널 이름들을 보여준다. 이것은 /usr/include/linux/signal.h 파일에서도 알 수 있다.
4. -1, : -HUP 프로세스를 재활성화한다.
5. -9 : 프로세스를 강제로 종료시킨다.

##### 관련 명령어
|ps명령어|sshd프로세스|설명|
|------|---|---|
|Root|USER|프로세스의 사용자|
|2518|PID|프로세스 ID|
|0.0|%CPU|마지막 1분 동안 프로세스가 사용한 CPU 점유율|
|0.1|%MEN|마지막 1분 동안 프로세스가 사용한 메모리의 점유율|
|7084|VSZ|가상메모리에 있는 프로세스의 KB 단위 크기|
|1076|RSS|프로세스의 실제 메모리의 크기로 KB 단위|
|?|TTY|연결되어 있는 터미널|
|Ss|STAT|실행되고 있는 프로세스 상태|
|Jun07|START|프로세스가 시작된 날짜|
|0:00|TIME|프로세스가 소비한 총 시간|
|/usr/sbin/sshd|COMMAND|사용자가 실행한 명령 이름|

***
# vim 에디터 - 매크로 사용방법

|기능|일반모드|예제|
|------|---|---|
|녹화|q+(매크로KEY)|qa|
|녹화종료|q|q|
|재생|@+(매크로key)|@a|
|마지막 매크로 실행|@@|@@|
|횟수실행|(횟수)@(매크로key)|10@a|

##### 일반모드에서 q+키 입력을 누르면 vim의 상태바에서Recording이라는 표시가 나온다. 이후에 반복적으로 수행할 키로그를 녹화하고 동작이 다 끝나면 q를 입력하여 종료해야한다.

##### 매크로를 정해진 횟수만큼 반복할때, a에 매크로 작업한 것을 10회 반복해서 연속 실행할때는 10@a 라고 일반모드에서 입력하면 된다.

##### 숫자증가 감소
|기능|일반모드|예제|
|------|---|---|
|숫자증가|CTRL + a|증가시키고 싶은 숫자에 커서 두고 ^a|
|숫자증가|CTRL + x|증가시키고 싶은 숫자에 커서 두고 ^x|
##### 참고<https://maduinos.blogspot.com/2020/07/vim-lecture-4-vim.html>
