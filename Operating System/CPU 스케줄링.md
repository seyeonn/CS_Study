# CPU 스케줄링

-   시스템의 자원을 효율적으로 사용하기 위해  `어떤 프로세스를 먼저 처리할지`  순서를 정하는 것
-   `CPU 이용률 극대화`가 목적

- 조건 : 오버헤드 ↓ / 사용률 ↑ / 기아 현상 ↓
- 목표
	1.  `Batch System`: 가능하면 많은 일을 수행. 시간(time) 보단 처리량(throughout)이 중요
	2.  `Interactive System`: 빠른 응답 시간. 적은 대기 시간.
	3.  `Real-time System`: 기한(deadline) 맞추기.

## 선점/비선점 스케줄링

### 선점 (Preemptive)
OS가 CPU의 사용권을 선점할 수 있는 경우, 강제 회수하는 경우 (처리시간 예측 어려움)

### 비선점 (nonpreemptive)
프로세스 종료 or I/O 등의 이벤트가 있을 때까지 실행 보장 (처리시간 예측 용이함)

## 프로세스 상태/상태 전이

<img width="698" alt="ss" src="https://user-images.githubusercontent.com/38287375/172017105-2bfbd720-9cd7-4248-a6f2-d25a09e9a572.png">

### 프로세스 상태

**1. 생성**  
- 사용자에 의해 프로세스가 생성된 상태  

**2. 준비**  
- CPU를 할당받을 수 있는 상태  
- 가장 높은 우선순위를 갖는 프로세스가 다음 순서에 CPU를 할당 받음  

**3. 실행**  
- CPU를 할당받아 동작(점유)중인 상태  

**4. 대기**  
- 프로세스 실행 중 입출력(I/O)처리 등으로 CPU를 양도하고 처리 완료까지 기다리는 상태  
- 대기 리스트는 우선 순위가 존재하지 않음  

**5. 종료**  
- 프로세스가 CPU를 할당 받아 주어진 시간 내에 완전히 수행을 종료한 상태

### 프로세스 상태 전이

-   **디스패치(Dispatch)**
    -   `준비 상태 → 실행 상태`
    -   준비 리스트에 있는 여러 프로세스 중 실행될 프로세스를 선정하여 CPU를 할당
-   **타이머 런 아웃(Timer Run Out)**
    -   `실행 상태 → 준비 상태`
    -   지정된 시간이 초과되면 CPU 반납 후 다시 준비 상태로 전이
-   **블록(Block)**
    -   `실행 상태 → 대기 상태`
    -   지정된 할당 시간을 초과하기 전 입출력 또는 기타 사건이 발생하면 입출력이 완료될 때까지 대기 상태로 전이
-   **웨이크 업(Wake-up)**
    -   `대기 상태 → 준비 상태`
    -   어느 순간 입출력이 종료되면 대기 상태의 프로세스에게 입출력 종료 사실을 알려주고 준비 상태로 전이

### CPU 스케줄링 종류

### 선점형 스케줄링 알고리즘

**1. 라운드 로빈 (Round Robin)**
-   프로세스는  `같은 크기의 CPU 시간`을 할당 (균등한 CPU 점유 시간)
-   프로세스가 할당된 시간 내에 처리 완료를 못한다면, 준비 큐 리스트의 가장 뒤로 보내지고 CPU는 대기 중인 다음 프로세스로 넘어간다

<img width="675" alt="round" src="https://user-images.githubusercontent.com/38287375/172017260-c8909ddd-675a-476d-8f59-e52881d281a3.png">

**2. SRT (Shortest Remaining Time First)**
-   `가장 짧은 소요 시간`이 걸리는 프로세스를 먼저 수행
-   남은 처리 시간이 더 짧다고 판단되는 프로세스가 준비 큐에 생기면 언제라도 프로세스가 선점됨

<img width="622" alt="short" src="https://user-images.githubusercontent.com/38287375/172017270-2bed17ff-ee95-4029-91ee-dd5a05639f18.png">

### 비선점 스케줄링 알고리즘

**1, FCFS (First Come First Service)**
-   프로세스가  `대기 큐에 도착한 순서`에 따라 CPU 할당
-   Queue와 동일, FIFO 알고리즘

<img width="674" alt="fcfs" src="https://user-images.githubusercontent.com/38287375/172017317-4e23d489-644d-420d-97f2-62cb1ea83478.png">

**2. SJF (Shortest Job First)**
-   프로세스가 도착하는 시점에 따라  `그 당시 가장 짧은 소요 시간을 갖는 프로세스가 종료 시까지 CPU 점유`
-   CPU 요구 시간이 긴 작업과 짧은 작업 간의 불평등이 심해 기아 현상 발생 가능성

<img width="581" alt="sjf" src="https://user-images.githubusercontent.com/38287375/172017328-ec404307-5e3b-40d3-b92f-e2b4d8cd6963.png">

### CPU 스케줄링 척도

1.  Response Time
    -   작업이 처음 실행되기까지 걸린 시간
2.  Turnaround Time
    -   실행 시간과 대기 시간을 모두 합한 시간으로 작업이 완료될 때 까지 걸린 시간

---
참조

https://gyoogle.dev/blog/computer-science/operating-system/CPU%20Scheduling.html

https://velog.io/@dasssseul/CS-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%A7%81%EC%84%A0%EC%A0%90-%EB%B9%84%EC%84%A0%EC%A0%90
