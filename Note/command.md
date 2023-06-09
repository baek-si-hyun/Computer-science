## 고급언어(소스코드)와 저급언어(목적언어)
- 고급언어는 코딩할때 쓰는 언어 (c, c++, python...)
- 저급언어는 컴퓨터가 사용하는 언어 ( 0, 1)
- 저급언어는 어셈블리어랑 기계어로 나뉜다
- 어셈블리어는 사람이 이해하기 쉽게만든 저급언어이다
- 어셈블리어는 CPU 종류마다 다르다
- 고급언어는 컴파일과정을 통해 어셈블리어가 되고, 어셈블리어는 링크 과정을 통해 기계어가 된다.


## 컴파일언어와 인터프리트언어 차이
- 컴파일언어는 고급언어 전체를 저급언어로 바꾸지만 인터프리트언어는 한줄씩 바꾼다
- 컴파일언어는 컴파일 도중 오류가 발생하면 소스코드 전체가 실행되지 않음
- 인터프리터언어는 오류가 발생하면 중단. 오류가 발생하기 전까지는 실행됨
** 컴파일언어와 인터프리터 언어는 경계가 모호해 지금까지도 논쟁의 중심에 있다.


## 명령어의 구조
- 연산코드와 오퍼랜드(주소필드)로 나뉜다
- 연산코드는 수행할 연산이, 오퍼랜드는 연산에 사용될 데이터 혹은 데이터의 위치가 담겨있다
- 오퍼랜드의 개수는 없을 수도 있고 많을 수도 있다.
- 연산코드는 데이터 전송, 산술/논리 연산, 제어 흐름 변경, 입출력 제어 이렇게 4가지 종류가 있다 (CPU마다 다름)

## 자주언급되는 자료구조 3가지
- 힙(Heap)은 이진 트리(Binary Tree)의 한 종류로, 각 노드가 하나 이상의 자식 노드를 가지며, 최대값 또는 최소값을 빠르게 찾아내기 위해 사용된다. 힙은 대개 우선순위 큐(Priority Queue)를 구현하는 데 사용된다.
- 스택(Stack)은 후입선출(Last In First Out, LIFO) 구조를 가지는 자료 구조이다. 새로운 요소는 스택의 가장 위에 추가되며, 요소를 삭제할 때는 가장 위의 요소가 먼저 삭제된다. 스택은 함수 호출(Call Stack)과 같은 작업에서 사용된다.
- 큐(Queue)는 선입선출(First In First Out, FIFO) 구조를 가지는 자료 구조이다. 새로운 요소는 큐의 뒤쪽에 추가되며, 요소를 삭제할 때는 가장 앞쪽의 요소가 먼저 삭제된다. 큐는 대기열(Queue)과 같은 작업에서 사용된다.

## 대표적인  연산 코드의 종류

### 데이터 전송
- MOVE: 데이터를 옮겨라
- STORE: 메모리에 저장해라
- LOAD(FETCH): 메모리에서 CPU로 데이터를 가져와라
- PUSH: 스택에 데이터를 저장하라
- POP: 스택의 최상단 데이터를 가져와라

### 산술,논리 연산
- ADD, SUBTRACT, MULTIPLY, DIVIDE: 덧셈, 뺄셈, 곱셈, 나눗셈을 수행하라
- INCREMENT, DECREMENT: 오페랜드에 1을 더해라, 오퍼랜드에 1을 빼라 
- AND, OR, NOT: AND, OR, NOT 연산을 해라
- COMPARE: 두개의 숫자 또는 TRUE, FALSE 값을 비교해라

### 제어 흐름 변경
- JUMP:  특정 주소로 실행을 옯겨라
- CONDITIONAL JUMP: 조건에 부합할 떄 특정 주소로 실행 순서를 옮겨라
- HALT: 프로그램의 실행을 멈춰라
- CALL: 되돌아올 주소를 저장한 채 특정 주소로 실행 순서를 옯겨라
- RETURN: CALL을 호출할 때 저장했던 주소로 돌아가라

### 입출력 제어
- READ(INPUT): 특정 입출력 장치로 부터 데이터를 읽어라
- WRITE(OUTPUT): 특정 입출력 장치로 데이터를 써라
- START IO: 입출력 장치의 상태를 확인하라
- TEST IO: 입출력 장치의 상태를 확이하라

## 유효 주소
- 연산에 사용할 데아터가 저장된 위치

## 명령어 주소 지정 방식
- 연산에 사용할 데이터가 저장된 위치를 찾는 방법
- 유효 주소를 찾는 방법
- 다양한 명령어 주소 지정 방식들
- 오퍼랜드에 연산에 사용될 데이터의 저장된 위치 값이 담긴다. 

** 데이터를 직접 가져오면 되는데 왜 굳이 주소를 가져올까? **
- 명령어에서 표현할 수 있는 데이터의 크기는 매우 제한적 이기 때문
- 명령어가 표현할 수 있는 데이터의 크기가 제한적이면 명령어 안에 포함되어있는 오퍼랜드 또한 영향을 받는다

### 즉시 주소 지정 방식
- 연산에 사용할 데이터를 오퍼랜드 필드에 직접 명시
- 가장 간단한 형태의 주소 지정 방식
- 연산에 사용할 데이터의 크기가 작아질 수 있지만 빠르다

### 직접 주소 지정 방식
- 오퍼랜드 필드에 유효 주소를 직접적으로 명시
- 유효 주소를 표현 할 수 있는 크기가 연산 코드만큼 줄어듦

### 간접 주소 지정 방식
- 오퍼랜드 필드에 유효 주소의 주소를 명시
- 앞선 주소 지정 방식들에 비해 속도가 느림

** CPU가 메모리에서 일을 처리하는 속도는 느리다. 그래서 메모리 접근을 최소화 해야한다. **

### 레지스터 주소 지정 방식
- 연산에 사용할 데이터가 저장된 레지스터 명시
- 메모리에 접근하는 속도보다 레지스터에 접근하는 것이 빠름

** CPU가 레지스터에 접근하는 속도는 메모리에 접근하는 속도 보다 빠르다. 이유는 레지스터는 CPU 안에 있고 메모리는 CPU 밖에 있기 때문 **

### 레지스터 간접 주소 지정 방식
- 연산에 사용할 데이터를 메모리에 저장
- 그 주소를 저장한 레지스터를 오퍼랜드 필드에 명시
































