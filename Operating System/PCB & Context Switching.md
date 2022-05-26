# PCB & Context Switching

## Process Management

> CPU가 프로세스가 여러 개일 때, CPU 스케줄링을 통해 관리하는 것을 말한다.
이때, CPU는 각 프로세스들이 누군지 알아야 관리가 가능한데 이 프로세스들의 특징을 갖고 있는 것이 바로 **Process Metadata**이다.

### Process Metadata
- **Process ID** : PID(Process Identification Number)라고도 한다. (프로세스 고유 식별 번호)
- - **Process State(프로세스 상태)** : 프로세스의 현재 상태(준비, 실행, 대기 상태)를 기억시킨다.
- **Process Priority(스케줄링 정보)** : 프로세스 우선순위 등과 같은 스케줄링 관련 정보를 기억시킨다.
- **CPU Registers** : 프로세스의 레지스터 상태를 저장하는 고간 등. CPU 내 범용 레지스터(AX, BX, CX, DX), 데이터 레지스터(SP, BP, SI, DI), 세그먼트 레지스터(CS, DS, ES, SS) 등이 갖고 있는 값을 기억시킨다.
- **Owner(계정 정보)** : CPU 사용시간의 정보(Quantum), 각종 스케줄러에 필요한 정보를 기억시킨다.
- **기억장치 관리 정보** : 프로그램이 적재될 기억 장치의 상한치, 하한치, 페이지 테이블 등의 정보를 기억시킨다.
- **입출력 정보** : 프로세스 수행시 필요한 주변 장치, 파일들의 정보를 기억시킨다.
- **프로그램 카운터(계수기)** : 다음에 실행되는 명령어의 주소를 기억시킨다.

이러한 정보들이 담긴 메타데이터는 프로세스가 생성되면 **PCB(Process Control Block)** 이라는 곳에 저장이 된다.

## PCB(Process Control Block)

> 프로세스 메타데이터들을 저장해놓은 곳이다. 
> 하나의 PCB 안에는 하나의 프로세스의 정보가 담겨있다.

![image (3)](https://user-images.githubusercontent.com/38287375/170870828-bc4ca5de-fabc-48d4-a2c6-45692a2c5bfd.png)

### 처리 과정

1. 프로그램 실행
2. 프로세스 생성
3. 프로세스 주소 공간에 (코드, 데이터, 스택) 생성
4. 이 프로세스의 메타데이터들이 PCB에 저장

### PCB 상세 구조

- Process State : 프로세스 상태(Create, Ready, Running, Block, terminated)
- Process Counter : 다음 실행할 명령어의 주솟값
- CPU Registers : accumulator, index register, stack pointers, general purpose registers.

### PCB가 필요한 이유

CPU에서는 프로세스의 상태에 따라 교체 작업이 이루어진다. (Interrupt가 발생해서 할당받은 프로세스가 Block(Waiting) 상태가 되고 다른 프로세스를 Running으로 바꿀 때)
**이때, 앞으로 다시 수행할 Block 상태의 프로세스의 상태값을 PCB에 저장해두는 것**이다.

### PCB 관리 방식

- Linked List 방식으로 관리된다.
- PCB List Head에 PCB들이 생성될 때마다 붙게 된다. 주솟값으로 연결이 이루어져 있는 연결 리스트 형태로, **삽입 삭제가 용이**하다.
- **즉, 프로세스가 생성되면 해당 PCB가 생성되고 프로세스 완료 시 제거가 된다.**
- 이렇게 수행 중인 프로세스를 변경할 때, **CPU의 레지스터 정보가 변경되는 것**을 **Context Switching이라고 한다.**

## Context Switching

1. CPU가 현재 실행하고 있는 Task(Process, Thread)의 상태를 저장하고, 다음 진행할 Task의 상태 및 Register 값들에 대한 정보(Context)를 읽어 새로운 Task의 Context 정보로 교체하는 과정

2. CPU가 이전의 프로세스 상태를 PCB에 보관하고, 또 다른 프로세스의 정보를 PCB에서 읽어서 레지스터에 적재하는 과정

3. 다중 프로그래밍 시스템에서 CPU가 할당되는 프로세스를 변경하기 위해 현재 CPU를 사용하여 실행되고 있는 프로세서의 상태 정보를 저장하고 제어권을 인터럽트 서비스 루틴(ISR)에게 넘기는 작업

### Context Switching이 필요한 이유

> Q. 만약 컴퓨터가 매번 하나의 Task만 처리할 수 있다면?
>
> A. 다음 Task를 처리하기 위해서 현재 Task가 끝날 때까지 기다려야 한다.
> A.반응속도가 매우 느리고 사용하기 불편하다.

**다양한 사람들이 동시에 사용하는 것처럼 하기 위해서 Context Switching이 필요하게 되었다.**

- 컴퓨터 멀티태스킹을 통해 빠른 반응속도로 응답 가능하다.
- 빠르게 Task를 바꾸면서 실행하기에 사람은 실시간처리가 되는 것처럼 보인다.
- CPU가 Task를 바꿔가며 실행하기 위해 Context Switching이 필요하게 되었다.

### Context Switching 수행 과정

1. Task의 대부분 정보는 Register에 저장되고 PCB(Process Control Block)로 관리가 되고 있다.

2. 현재 실행하고 있는 Task의 PCB 정보를 저장하게 된다.(Process Stack, Ready Queue)

3. 다음 실행할 Task의 PCB 정보를 읽어 Register에 적재하고 CPU가 이전에 진행했던 과정을 연속적으로 수행할 수 있게 된다.

### Context Switching과 시간 할당량

> 프로세스들의 시간 할당량은 시스템 성능의 중요한 역할을 한다. 
> 시간 할당량이 적을수록 사용자 입장에서는 여러 개의 프로세스가 거의 동시에 수행되는 느낌을 갖지만 인터럽트의 수와 문맥 교환의 수가 늘어난다. 
> 프로세스의 실행을 위한 부가적인 활동을 **Overhead(간접 부담 비용)** 이라고 하는데, 이 또한 문맥 교환 수와 같이 늘어나게 된다. 

- 시간 할당량이 적어질 경우 : 문맥 교환 수, 인터럽트 횟수, 오버헤드가 증가하지만 여러 개의 프로세스가 동시에 수행되는 느낌을 갖는다.

- 시간 할당량이 커질 경우 : 문맥 교환 수, 인터럽트 횟수, 오버헤드가 감소하지만 여러 개의 프로세스가 동시에 수행되는 느낌을 갖지 못한다.

**프로세스를 수행하다가 I/O event가 발생하여 BLOCK 상태로 전환시켰을 때, CPU가 그냥 놀게 놔두는 것보다 다른 프로세스를 수행시키는 것이 효율적**이므로, CPU에 계속 프로세스를 수행시키도록 하기 위해서 다른 프로세스를 실행시키고 Context Switching을 할 때 Overhead가 발생한다.

CPU가 놀지 않도록 만들면서, 사용자에게 빠르게 일처리를 제공해 주기 위한 것이다.


---

참조

https://m.blog.naver.com/adamdoha/222019884898
