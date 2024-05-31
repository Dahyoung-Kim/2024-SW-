# 리눅스 명령어 중에서 top, ps, jobs, kill 명령어에 대해서 조사해보자!

## 1. top 명령어
### top 명령어란?
리눅스 명령어 top은 실시간으로 시스템의 프로세스와 리소스 사용 상태를 모니터링하는 데 사용됩니다.
top 명령어는 CPU 사용량, 메모리 사용량, 스왑 사용량, 각 프로세스의 상태 등을 나타내주며 top를 실행하는 동안에는 주기적인 업데이트로 실시간에 근접한 내용을 보여줍니다.

### top 명령어 사용 예시
```
top - 10:15:03 up  2:34,  2 users,  load average: 0.42, 0.31, 0.28
Tasks: 164 total,   1 running, 163 sleeping,   0 stopped,   0 zombie
%Cpu(s):  4.3 us,  1.2 sy,  0.0 ni, 94.0 id,  0.5 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  8009672 total,  3029648 free,  2351244 used,  2628780 buff/cache
KiB Swap:  2047996 total,  2047996 free,        0 used.  5154872 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND    
 2043 john      20   0  156460   3564   2652 R   5.0  0.1   0:01.43 top        
 1827 root      20   0  275644  16048   9280 S   1.5  0.2   0:12.38 Xorg       
 2005 john      20   0  475280  34212  14836 S   0.5  0.4   0:05.67 gnome-term 
 1356 root      20   0  145324  10312   6124 S   0.3  0.1   0:02.14 NetworkMan 
 1395 mysql     20   0  528180  40256   9156 S   0.3  0.5   1:22.67 mysqld     
 1501 www-data  20   0  395400  24208   8324 S   0.3  0.3   0:08.36 apache2    
 2102 john      20   0  193700   7344   5244 S   0.3  0.1   0:02.34 gedit      
    1 root      20   0  186400   5472   3208 S   0.0  0.1   0:01.12 systemd    
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd   
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ksoftirqd/0
```

### top 명령어 실행 시 영역별 설명
![image](https://github.com/Dahyoung-Kim/2024-SW-/assets/171330254/bb53cb39-4960-41a8-b62d-4f631220b246)

+ top : 시스템이 얼마나 오래 실행 중인지 표시합니다.
+ Tasks : 현재 실행 중, 대기 중, 중단된 작업 수를 표시합니다.
+ %Cpu(s) : 각 CPU의 사용률을 보여줍니다.
  + 예시: 사용자(user), 시스템(system), 유휴(idle), 대기(wait), 하이퍼스레드(ht)
+ KiB Mem : 물리적 메모리 사용률을 표시합니다.
+ KiB Swap : 가상 메모리 사용률을 표시합니다.

좀 더 자세한 유저세션이 궁금하다면 who 명령어를 통해 알 수 있습니다.

### top 명령어 실행 시 디테일 영역별 설명
![image](https://github.com/Dahyoung-Kim/2024-SW-/assets/171330254/3310610b-7f46-406d-aafb-dc0358287b09)
+ PID : PID는 프로세스 ID이며 프로세스를 구분하기 위한 겹치지않는 고유한 값입니다.
+ USER : 해당 프로세스를 실행한 USER 이름 또는 효과를 받는 USER의 이름입니다.
+ PR : 커널에 의해서 스케줄링되는 우선순위입니다.
+ NI : PR에 영향을 주는 nice라는 값입니다.
+ VIRT : 프로세스가 소비하고 있는 총 메모리입니다. 프로그램이 실행중인 코드, heap, stack과 같은 메모리, IO buffer 메모리를 포함합니다.
+ RES : RAM에서 사용중인 메모리의 크기를 나타냅니다.
+ SHR : 다른 프로세스와의 공유메모리(Shared Memory)를 나타냅니다.
+ S : 프로세스의 현재 상태를 나타냅니다.
+ %CPU : 각 프로세스가 사용하는 CPU의 비율을 나타냅니다.
+ %MEM : RAM에서 RES가 차지하는 비율을 나타냅니다.
+ TIME+ : 프로세스가 사용한 토탈 CPU 시간을 나타냅니다.
+ COMMAND : 해당 프로세스를 실행한 커맨드를 나타냅니다.

### top 명령어 실행 시 사용 가능한 명령어
+ h : 도움말을 표시합니다.
+ k : 특정 PID를 가진 프로세스를 종료합니다.
+ r : 특정 PID를 가진 프로세스의 우선순위를 변경합니다.
+ u : 특정 사용자의 프로세스만 표시합니다.
+ M : 메모리 사용량을 기준으로 정렬합니다.
+ P : CPU 사용량을 기준으로 정렬합니다.
+ T : 실행 시간을 기준으로 정렬합니다.
+ 1 : 각 CPU 코어의 사용률을 개별적으로 표시합니다.
+ q : top을 종료합니다.

### top 명령어 옵션
+ -d : 업데이트 간격을 설정합니다.
  + 예: top -d 2는 2초 간격으로 업데이트
+ -p : 특정 PID의 프로세스를 모니터링합니다.
  + 예: top -p 1234
+ -n : 업데이트 횟수를 지정합니다.
  + 예: top -n 5는 5번 업데이트 후 종료
+ -u : 특정 사용자의 프로세스를 모니터링합니다.
  + 예: top -u username

## 2. ps 명령어
### ps 명령어란?
리눅스 명령어 ps는 현재 실행 중인 프로세스에 대한 정보를 표시하는 데 사용됩니다.
ps 명령어는 다양한 옵션을 통해 실행 중인 프로세스의 상세 정보를 제공할 수 있고 특정 프로세스를 필터링하거나 정렬하는 데 유용합니다.

### ps 명령어 사용 예시
```
$ ps
  PID TTY          TIME CMD
 1234 pts/0    00:00:00 bash
 2345 pts/0    00:00:00 ps
```
### ps 명령어 실행 시 영역별 설명
![image](https://github.com/Dahyoung-Kim/2024-SW-/assets/171330254/e6553b1e-c1ef-424b-9019-2f8efee34204)
+ PID : 프로세스 ID를 표시합니다.
+ TTY: 프로세스가 연결된 터미널을 표시합니다.
+ TIME: 프로세스가 사용한 총 CPU 시간을 표시합니다.
+ COMMAND: 실행 중인 명령어를 표시합니다.

### ps 명령어 옵션
+ a: 터미널에 종속되지 않은 모든 프로세스를 보여줍니다.
+ u: 사용자 친화적인 포맷으로 출력합니다.
+ x: 터미널에 종속되지 않은 모든 프로세스를 포함합니다.
+ e: 모든 프로세스를 보여줍니다.

## 3. jobs 명령어
### jobs 명령어란?
jobs는 현재 셸 세션에서 실행 중인 백그라운드 작업을 보여줍니다. 이 명령어는 백그라운드 및 포그라운드 작업의 상태를 모니터링하고 관리하는 데 유용합니다.

### jobs 명령어 사용 예시
```
$ jobs
[1]   Running                 long_running_command &
[2]-  Stopped (tty output)    another_command
[3]+  Stopped (tty output)    yet_another_command
```
### jobs 명령어 실행 시 영역별 설명
![image](https://github.com/Dahyoung-Kim/2024-SW-/assets/171330254/f5efef13-2f1a-421c-a10e-adf336570d34)
+ [N]: 작업 번호 (job number). 이 번호는 셸 세션 내에서 해당 작업을 참조하는 데 사용됩니다.
+ Running: 작업이 백그라운드에서 실행 중입니다.
+ Stopped: 작업이 일시 중지되었습니다.
+ Done: 작업이 완료되었습니다.
+ Exited: 작업이 종료되었습니다.

### jobs 명령어 옵션
+ -l : 프로세스 ID와 함께 잡 목록을 출력합니다.
+ -n : 마지막로 알림 이후 변경된 잡만 출력합니다.
+ -p : 잡의 프로세스 ID만 출력합니다.
+ -r : 실행 중인 잡만 출력합니다.
+ -s : 중지된 잡만 출력합니다.

## 4. kill 명령어
### kill 명령어란?
kill은 프로세스에 신호를 보내는 데 사용됩니다.
이 신호는 프로세스를 종료하거나, 중지하거나, 다시 시작하는 등 다양한 작업을 수행할 수 있습니다. 
kill 명령어는 프로세스를 제어하고 관리하는 데 중요한 도구입니다.

### kill 명령어 사용 예시
```
$ kill -l
 1) SIGHUP     2) SIGINT     3) SIGQUIT    4) SIGILL     5) SIGTRAP
 6) SIGABRT    7) SIGBUS     8) SIGFPE     9) SIGKILL    10) SIGUSR1
11) SIGSEGV   12) SIGUSR2   13) SIGPIPE   14) SIGALRM   15) SIGTERM
16) SIGSTKFLT 17) SIGCHLD   18) SIGCONT   19) SIGSTOP   20) SIGTSTP
21) SIGTTIN   22) SIGTTOU   23) SIGURG    24) SIGXCPU   25) SIGXFSZ
26) SIGVTALRM 27) SIGPROF   28) SIGWINCH  29) SIGPWR    30) SIGSYS
```

### kill 명령어 옵션
+ -l : 모든 신호 이름을 출력하거나, 주어진 신호 번호 또는 이름에 해당하는 신호 번호를 출력합니다.
+ -s <signal> : 특정 신호를 보냅니다. 신호 이름 또는 번호로 지정할 수 있습니다.
+ -SIG<signal> : 신호 이름 앞에 SIG를 붙여 신호를 보냅니다.
+ --help : kill 명령어의 사용법을 출력합니다.
+ -v : 신호를 성공적으로 보낸 후에 메시지를 출력합니다.
+ -V : kill 명령어의 버전을 출력합니다.

### kill 명령어의 주요 시그널
+ SIGHUP
  + HUP : hangup, 로그아웃등의 접속이 끊을 때 발생하는 신호(Signal)로 특정 실행 중인 프로그램이 사용하는 설정 파일을 변경시키고 변화된 내용을 적용할때 사용됩니다.
+ SIGINT
  + INT : 현재 작동중인 프로그램의 동작을 멈출때 사용되며, 일반적인 값은 <CTRL>+<c> 입니다.
+ SIGKILL
  + KILL : 	프로그램을 무조건 종료할 경우 사용됩니다.
+ SIGSEGV
  + SEGV : 잘못된 메모리 관리시 생기는 신호(Signal) 입니다.
+ SIGTERM
  + TERM : 실행중인 프로그램을 정상적인 종료방법으로 프로그램을 종료하는 신호(Signal)로 kill 명령에서 신호(Signal)를 지정하지 않으면 이 신호(Signal)를 사용하여 프로그램을 종료합니다.
+ SIGCONT
  + CONT : 중지 되어 있는 프로그램을 재실행 하는데 사용되는 신호(Signal) 입니다.
+ SIGSTOP
  + STOP : 프로그램을 중지 하는데 사용되는 신호(Signal) 입니다.
+ SIGTSTP
  + TSTP : 	터미널에서 중지되어 있는 신호(Signal) 입니다.






