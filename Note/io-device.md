## 입출력장치
- 입출력장치는 보조기억장치도 포함할 수 있다
- 입출력장치는 종류가 많아 정보를 주고 받는 방식을 규격화 하기 어렵다
- 데이터 전송률이 낮다 (전송률: 데이터를 얼마나 빨리 교환할 수 있는지를 나타내는 지표)
- 위의 문제들 때문에 장치 컨트롤러를 통해 컴퓨터 내부와 정보를 주고 받는다

## 장치 컨트롤러
- CPU와 입출력장치간의 통신 중개
- 오류 검출
- 장치 컨트롤러 안에 레지스터가 내장되어 있다 (데이터 레지스터, 상태 레지스터, 제어 레지스터)
- 입출력버스와 입출력장치와 연결된다
- 데이터 버퍼링

** 버퍼링이란 전송률이 높은 장치와 낮은 장치 사이에 주고받는 데이터를 버퍼라는 임시 저장공간에 저장하여 전송률을 비슷하게 맞추는 방법 **
ex) CPU가 너무 빨리 데이터를 전송하면 이 데이터를 모아 놓고 조금씩 내보낸다. 
    반대로 입출력장치가 느리게 데이터를 전송하면 모았다가 한번에 전송한다.
    
### 데이터 레지스터
- CPU와 입출력장치 사이에 주고받을 데이터가 담기는 레지스터(버퍼)
- RAM을 사용하기도 한다

### 상태 레지스터
- 상태 정보를 저장한다
  - 입출력장치가 입출력 작업을 할 준비가 되었는지,
  - 입출력 작업이 완료되었는지
  - 입출력장치에 오류는 없는지 등이 상태 정보

### 제어 레지스터
- 입출력장치가 수행할 내용에 대한 제어 정보

## 장치 드라이버
- 장치 컨트롤러가 입출력장치를 연결하기 위한 하드웨어적인 통로라면 장치 드라이버는 입출력장치를 연결하기 위한 솦트웨어적인 통로이다
- 장치 컨트롤러의 동작을 감지하고 제어하는 프로그램

## 프로그램 입출력
- 프로그램 속 명령어로 입출력장치를 제어하는 방법
- 입출력 명령어로써 장치 컨트롤러와 상호작용
- 메모리에 저장된 정보를 하드디스크에 백업
- 메모리 맵 입출력 방식과 고립형 입출력으로 나뉜다

### 메모리 맵 입출력
- 메모리에 접근하기 위한 주소 공간과 입출력장치에 접근하기 위한 주소 공간을 하나의 주소 공간으로 간주하는 방법
- 같은 메모리에 메모리를 위한 주소 공간과 입출력장치를 위한 주소 공간이 공존한다
- 메모리에 접근하는 명령어와 입추렭장치에 접근하는 명령어가 동일하다
- 메모리 주소 공간이 축소된다(나눠쓰기 때문)

### 고립형 입출력
- 메모리를 위한 주소 공간과 입출력 장치를 위한 주소 공간을 분리하는 방법
- 입출력 전용 명령어를 사용해야 한다
- 메모리와 입출력 장치는 분리된 주소 공간을 사용한다
- 메모리 주소 공간이 축소되지 않는다

### 메모리에 저장된 정보를 하드디스크에 백업하는 과정
1. CPU는 하드 디스크 컨트롤러의 제어 레지스터에 쓰기 명령 내보내기
2. 하드디스크 컨트롤러는 하드디스크 상태를 확인하고 상태 레지스터에 준비완료 표시
3. CPU는 상태 레지스터를 주기적으로 읽어 보며 하드디스크의 준비 여부를 확인
4. 하드디스크가 준비되었다면 백업할 메모리의 정보를 데이터 레지스터에 쓰기 (아직 백업 작업이 끝나지 않았다면 1번부터 다시 시작)
5. 쓰기가 끝나면 작업 종료

## 인터럽트 기반 입출력
- 하드웨어 인터럽트는 장치 컨트롤러에 의해 발생
- 입출력 장치가 많을때는 동시다발적인 인터럽트가 발생하게 된다

## 동시다발적 인터럽트
- 여러 하드웨어 인터럽트는 순차적으로 처리할순 있지만 모든 인터럽트를 순차적으로 처리할 순 없다
- 우선순위를 반영해 인터럽트를 처리할 수 있다

### PIC(Programmable Interrupt Controller)
- 여러 장치 컨트롤러에 연결되어 장치 컨트롤러의 하드웨어 인터럽트 우선 순위를 판단한 뒤 CPU에게 알려주는 하드웨어

## DMA(Direct Memory Accesss)
- 프로그램 입출력, 인터럽트 기반의 입출력 모두 CPU를 거친다
- DMA는 CPU를 거치지 않고 입출력장치가 메모리에 직접 접근하게 하는 기능
- CPU 대신 장치 컨트롤러와 상호작용한다
- DMA는 메모리와 장치 컨트롤러와 상호작용하기 위해 시스템 버스를 사용하는데 CPU와 시스템 버스 사용이 겹치지 않게 CPU가 시스템버스를 사용하지 않을 때 사용한다
- CPU가 아예 관여를 안하는 것이 아니고 처음과 마지막만 관여한다.

## 입출력 버스
- 시스템 버스 사용을 줄이기 위해(CPU와 겹치는걸 최소하기 위해) 장치 컨트롤러와 DMA는 입출력 버스를 이용한다






























