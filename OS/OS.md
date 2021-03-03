1. 프로세스와 쓰레드의 비교

   - 프로세스: 메모리에 적재되어 CPU를 할당 받아 실행되는 프로그램
   - 쓰레드: 프로세스의 작업단위. 자원을 공유하거나 하지 않는 경우 둘 다 있다.

2. 힙과 스택의 차이점

   - 힙: 메모리 주소가 낮은 영역부터 채워진다
   - 스택: 메모리 주소가 높은 영역부터 채워진다

   - 힙: 동적할당할 경우 할당되는 영역
   - 스택: 함수 호출 시 함수 지역변수 저장, 함수 호출 caller의 환경정보 저장

3. 프로세스의 생성 과정

   - PCB가 생성되며 OS가 실행한 프로그램의 코드를 읽어들여 프로세스에 할당된 메모리의 Text segment에 저장한다.
   - 초기화된 전역 변수 및 static 변수를 data segment에 할당.
   - HEAP과 Stack은 초기 메모리 주소만 초기화됨.
   - PCB에 여러 정보가 기록되면 Ready Queue에서 CPU를 할당받기까지 대기한다.

4. 컴퓨터의 구성요소

   - CPU : 연산 및 신호를 처리하는 장치
   - 메모리 : 계산한 것, 계산해야 할 것을 저장하는 장치. 단기 기억장치.
   - 디스크 : 메모리와 달리 영구적으로 데이터를 저장해주는 장치 (하드디스크, SSD)
   - OS: CPU와 메모리에 명령을 내리는 주체로, 자원을 효율적으로 관리하고,  후순위 프로세스를 종료시킵니다

5. 인터럽트란?

   - 원래 프로세스를 진행하다 다른 일을 먼저 하게 되는 신호

6. PCB(프로세스 제어 블록)

   - 특정 프로세스에 대한 중요한 정보를 저장하고 있는 운영체제의 자료구조입니다.
   - 프로세스의 생성과 동시에 고유한 PCB를 생성합니다.
   - 인터럽트 발생 시 당시 프로세스의 작업을 PCB에 저장하고, CPU를 다시 할당받으면 PCB로부터 불러옵니다

7. 멀티스레드 vs 멀티프로세스

   - 멀티스레딩의 장점: 메모리 공간과 시스템 자원 소모가 줄어들게 된다. 스레드 간의 통신이 필요한 경우에도 별도의 자원을 이용하는 것이 아니라 전역 변수의 공간 또는 동적으로 할당된 공간인 Heap 영역을 이용하여 데이터를 주고받을 수 있습니다
   - 비교
     - 멀티스레드: 멀티 프로세스보다 적은 메모리 공간을 차지하고 문맥 전환이 빠르다는 장점이 있지만, 오류로 인해 하나의 스레드가 종료되면 전체 스레드가 종료될 수 있다는 점과 동기화 문제를 안고 있다
     - 멀티프로세스: 하나의 프로세스가 죽더라도 다른 프로세스에는 영향을 끼치지 않고 정상적으로 수행된다는 장점이 있지만, 멀티 스레드보다 많은 메모리 공간과 CPU 시간을 차지한다는 단점이 존재한다.

8. 스케줄러

   - Job Queue : 현재 시스템 내에 있는 모든 프로세스의 집합
   - Ready Queue : 현재 메모리 내에 있으면서 CPU 를 잡아서 실행되기를 기다리는 프로세스의 집합
   - Device Queue : Device I/O 작업을 대기하고 있는 프로세스의 집합

9. Round Robin

   - 현대적인 CPU 스케줄링
   - 각 프로세스는 동일한 크기의 할당 시간(time quantum)을 갖게 된다.
   - 할당 시간이 지나면 프로세스는 선점당하고 ready queue 의 제일 뒤에 가서 다시 줄을 선다.
   - RR은 CPU 사용시간이 랜덤한 프로세스들이 섞여있을 경우에 효율적

10. Critical Section과 해결책

    - 정의
      멀티 스레딩에 문제점에서 나오듯, 동일한 자원을 동시에 접근하는 작업(e.g. 공유하는 변수 사용, 동일 파일을 사용하는 등)을 실행하는 코드 영역을 Critical Section 이라 칭한다.
    - 해결책
      - Lock :(하드웨어기반)
        동시에 공유 자원에 접근하는 것을 막기 위해 Critical Section 에 진입하는 프로세스는 Lock 을 획득하고 Critical Section 을 빠져나올 때, Lock 을 방출합니다
      - Semaphores: (소프트웨어기반)
        - 카운팅 세마포: 가용한 개수를 가진 자원 에 대한 접근 제어용으로 사용되며, 세마포는 그 가용한 자원의 개수 로 초기화 된다. 자원을 사용하면 세마포가 감소, 방출하면 세마포가 증가 한다.
        - 이진 세마포:  상호배제의 (Mutual Exclusion)의 머릿글자를 따서 만들어졌다. 이름 그대로 0 과 1 사이의 값만 가능하며, 다중 프로세스들 사이의 Critical Section 문제를 해결하기 위해 사용한다.
    - Deadlock
      세마포가 Ready Queue 를 가지고 있고, 둘 이상의 프로세스가 Critical Section 진입을 무한정 기다리고 있고, Critical Section 에서 실행되는 프로세스는 진입 대기 중인 프로세스가 실행되야만 빠져나올 수 있는 상황을 지칭한다.

11. 메모리 관리전략

    - 페이징
      하나의 프로세스가 사용하는 메모리 공간이 연속적이어야 한다는 제약을 없애는 메모리 관리 방법이다.
      페이징 기법을 사용함으로써 논리 메모리는 물리 메모리에 저장될 때, 연속되어 저장될 필요가 없고 물리 메모리의 남는 프레임에 적절히 배치됨으로 외부 단편화를 해결할 수 있는 큰 장점이 있다.

      단점
      내부 단편화 문제의 비중이 늘어나게 된다. 예를들어 페이지 크기가 1,024B 이고 프로세스 A 가 3,172B 의 메모리를 요구한다면 3 개의 페이지 프레임(1,024 \* 3 = 3,072) 하고도 100B 가 남기때문에 총 4 개의 페이지 프레임이 필요한 것이다. 결론적으로 4 번째 페이지 프레임에는 924B(1,024 - 100)의 여유 공간이 남게 되는 내부 단편화 문제가 발생하는 것이다.

    - 세그멘테이션
      페이징에서처럼 논리 메모리와 물리 메모리를 같은 크기의 블록이 아닌, 서로 다른 크기의 논리적 단위인 세그먼트(Segment)로 분할 사용자가 두 개의 주소로 지정(세그먼트 번호 + 변위) 세그먼트 테이블에는 각 세그먼트의 기준(세그먼트의 시작 물리 주소)과 한계(세그먼트의 길이)를 저장

      단점
      서로 다른 크기의 세그먼트들이 메모리에 적재되고 제거되는 일이 반복되다 보면, 자유 공간들이 많은 수의 작은 조각들로 나누어져 못 쓰게 될 수도 있다.(외부 단편화)

12. 가상메모리

    - 가상메모리는 프로세스 전체가 메모리 내에 올라오지 않더라도 실행이 가능하도록 하는 기법 이며, 프로그램이 물리 메모리보다 커도 된다는 주요 장점이 있다.
    - 가끔만 사용되는 코드가 차지하는 메모리들을 확인할 수 있다는 점에서, 불필요하게 전체의 프로그램이 메모리에 올라와 있어야 하는게 아니라는 것을 알 수 있다.

13. 캐시메모리
    - 캐시 메모리는 속도가 빠른 장치와 느린 장치간의 속도차에 따른 병목 현상을 줄이기 위한 범용 메모리이다. 이러한 역할을 수행하기 위해서는 CPU 가 어떤 데이터를 원할 것인가를 어느 정도 예측할 수 있어야 한다.