# 제 2과목_전자계산기 구조

* CPLD( Complex Programmable Logic Device)
    * 복합 프로그래머블 논리 소자
    * 여러개의 LAB(Logic Array Block)
    * 연결선 PIA(Programmable Interconnection Array)로 구성
    * 빠른 성능이나 정확한 타이밍의 예측이 필요한 곳에서 사용

* IC에 필요한 pin 수
	- 주소 1024 = 2의 10승 = `10` word
	- 데이터 버스 `8`bit
	- chip select bit `1`개
	- 따라서 `10+8+1=19`개의 핀이 필요하다

* 논리연산
    * AND
    * OR
    * NOT
    * NAND
    * NOR
    * XOR
        * 두 데이터를 비교할 때 사용
        * 배타적 논리합
        * 두개의 비트가 같으면 0, 다르면 1을 출력
    * XNOR

* 논리 마이크로 연산 selective-set연산을 수행하면?<br/>
`A(프로세서 레지스터) = 0011, B(논리 오퍼랜드) = 1010`
    * selective-set : 각 자리를 OR 연산 = `1011`
    * 반대는 mask : 각 자리를 AND 연산
	
	- selective-Set동작(Or 동작)    
	- selective-Complement 동작(Exclusive-OR동작)
	- selective-Clear 동작(A<-A^B’)   
	- Mask 동작 (AND동작)
	- insert 동작(원하는 위치 비트의 마스크 후 원하는 값으로 OR동작)
	- Complete 동작(Exclusive-OR동작)

* 부동 소수점 나눗셈
    * 제수가 0인지 여부를 조사
    * 부호 결정
    * 피제수의 가수 부분이 제수의 가수 부분보다 작아지도록 피제수 위치 조정
    * 지수끼리 뺄셈, 가수끼리 나눗셈

* 병렬 컴퓨터 클록 주기 80ns, 데이터 버스의 폭이 8byte. 전송가능한 데이터 양은?
    * 8bytes / 80ns
    * = 8bytes / 0.000008sec 
    * = 100000bytes/sec 
    * = 100Mbytes/sec

* I/O operation = 입출력 제어방식
    * program 제어 방식
        * CPU가 상태 플러그를 계속 조사 (I/O완료 여부)
        * CPU가 직접 MBR과 AC사이의 자료 전송 처리
    * interrupts 제어 방식
        * 인터페이스가 CPU에게 입출력을 요청
        * 완료되면 CPU는 수행중이던 부분 재개
        * CPU의 상태 보존이 필요
        * 비동기적 제어방식
    * DMA에 의한 방식
        * 주기억장치와 I.O장치간 데이터 교환은 CPU의 개입 없이 진행
    * channel
        * 입출력 명령어는 별도의 입출력 프로세서가 전담(CPU관여 없음)
    * strobe pulse
    * hand shaking 방식

* Emulation
    * 한 컴퓨터가 다른 컴퓨터처럼 똑같이 작동하도록 소프트웨어나 마이크로 프로그래밍을 사용하는 기법

* 하나의 명령 처리 과정
    * 인스트럭션 페치
    * 인스트럭션 디코딩
    * 오퍼랜드 페치
    * 실행
    * 인터럽트 조사

* Micro Operation
    * 하나의 클럭펄스 시간동안 실행되는 기본 동작(한 단계씩 실행)
    * 명령을 수행하기 위해 CPU내의 레지스터와 플래그의 상태 변환을 일으키는 작업
    * 기억장치로부터 인출한 명령어를 실행하기 위해 제어 신호를 발생시키는 각 단계 세부 동작
    * 레지스터에 저장된 데이터에 의해 동작한다.
    <br/><br/>
    * Common Operation
    * Axis Operation
    * Count Operation

* 디코더 논리게이트 기호
    * not <br/>
    ![NOT](https://upload.wikimedia.org/wikipedia/commons/6/67/Not-gate-en.png "NOT")
    * or <br/>
    ![OR](https://upload.wikimedia.org/wikipedia/commons/b/b9/OR-gate-US.png "OR")
    * and <br/>
    ![AND](https://upload.wikimedia.org/wikipedia/commons/0/03/AND-gate-US.png "AND")
    * xor<br/>
    ![XOR](https://upload.wikimedia.org/wikipedia/commons/6/61/XOR-gate-US.png "XOR")
    * nor<br/>
    ![NOR](https://upload.wikimedia.org/wikipedia/commons/a/ad/NOR-gate-US.png "NOR")
    * nand<br/>
    ![NAND](https://upload.wikimedia.org/wikipedia/commons/d/d3/NAND-gate-US.png "NAND")


* 래지스터
    * SET한다 = 비트를 1로 바꾼다
    * 16진수 80H = 2진수 10000000
    * 0,2,4번째 비트를 세트 = 00010101
    * 10000000 +(or) 00010101 = 00010101
    * 00010101 = 15H

* 크로스 어셈블러
    * 다른 컴퓨터를 이용하여 어셈블리 언어의 프로그램을
    * 이식(porting)하려는 마이크로프로세서의 기계어로 번역하는 프로그램
    * 어셈블리어 프로그램을 A(번역)컴을 이용하여 B(이식대상)의 언어로 번역

* 8비트 레지스터에서 2의보수로 숫자를 표시한다면
    * 맨 앞이 1이면 음수, 0이면 양수
    * 0 : 00000000
    * 1 : 00000001
    * -1 : 11111111
    * 127 : 011111111
    * -127 : 10000001
    * -128 : 10000000
    * 10진수의 범위 : -128~127

* 멀티 프로그래밍
    * 2개 이상의 프로그램을 주기억장치에 저장
    * CPU를 번갈아 사용
    * 컴퓨터시스템 자원 활용률을 극대화

* 동기 고정식 마이크로 오페레이션 제어의 특징
    * 제어장치의 구현이 간단하다
    * 중앙처리장치의 시간 이용이 비효율적이다
    * 여러 종류의 MO수행 시 CPI사이클타임이 실제 오퍼레이션 시간보다 길다.
    * 가장 긴 마이크로 오퍼레이션의 동작을 마이크로사이클 시간으로 정함
    * 동작시간이 비슷할 때 유리 (시간지연 없음)

* 입출력 제어장치의 종류
    * DMA
    * 채널
    * 입출력 프로세서
    * 데이터버스는 입출력 제어장치라는 표현에 분류하지 않는다!!

* 인터럽트 벡터 필수요소
    * `분기 번지`
    * 인터럽트가 발생했을 때 특정 번지로 점프하도록 기억
    * 특정 번지의 서브루틴을 실행

* 명령어 처리를 위한 마이크로 사이클
    * 인출 (Fetch)
    * 간접 (Indirect)
    * 실행 (Excute)
    * 인터럽트 (Interrupt)

* 주소 명령어 형식
    * 3번지 명령어
        * 명령 인출 횟수가 적다
        * 연산 결과를 주로 op1에 따로 저장 (원래 내용이 소멸되지 않음)
        * 프로그램 결과의 길이가 전체적으로 짧아짐
    * 2번지 명령어
        * 가장 일반적
        * 연산 결과를 한 쪽에 저장해야 해서 한쪽의 자료가 사라짐
        * MOVE 명령어
    * 1번지 명령어
        * AC(누산기) 이용
        * 명령어 뒤에 한개만 나옴
        * ex > LOAD A , ADD B
    * 0번지 명령어
        * 스택이 필요. PUSH POP
        * 가장 짧은 명령어 형식
        * postfix형태의 수식
        * !스택컴퓨터가 순서대로라서 편리하다는 말은 오답!

* 상대 주소모드
    * 분기 명령어의 길이 `3바이트`
    * 분기명령어 `256AH` 번지에 저장
    * 명령어에 지정된 변위 값 `-75H`
    * 분기 주소 위치는? 
        * 상대 주소모드는 분기명령어가 저장된 위치에서 변위값을 빼면 된다.
        * 단, 분기명령어의 길이도 더해줘야 한다.
        * 따라서 256AH - (-75H) + 3H = 24F8H 번지
