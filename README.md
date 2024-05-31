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

### Top 명령어 실행 시 영역별 설명
+ top : 시스템이 얼마나 오래 실행 중인지 표시합니다.
+ Tasks : 현재 실행 중, 대기 중, 중단된 작업 수를 표시합니다.
+ %Cpu(s) : 각 CPU의 사용률을 보여줍니다.
  + 예시: 사용자(user), 시스템(system), 유휴(idle), 대기(wait), 하이퍼스레드(ht)
+ KiB Mem : 물리적 메모리 사용률을 표시합니다.
+ KiB Swap : 가상 메모리 사용률을 표시합니다.





## 2. ps 명령어

## 3. jobs 명령어

## 4. kill 명령어
