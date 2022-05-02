## 📌 스택 & 큐
+ 스택과 큐는 자료구조의 기초 개념으로 다음의 두 핵심적인 함수로 구성됨
  + __삽입(Push):__ 데이터를 삽입한다.
  + __삭제(Pop):__ 데이터를 삭제한다.
+ 추가로 알아둬야 하는 개념
  + __오버플로(Overflow):__ 데이터가 이미 저장 공간을 모두 채웠는데 삽입 연산을 수행할 때 발생
  + __언더플로(Underflow):__ 데이터가 하나도 없는데 삭제 연산을 수행할 때 발생
### 📍 스택 자료구조
+ 먼저 들어 온 데이터가 나중에 나가는 형식(후입선출(LIFO))의 자료구조  
_ex. 박스쌓기_
+ __입구와 출구가 동일한 형태__ 로 스택을 시각화할 수 있음
<img width="190" alt="스크린샷 2022-04-04 오후 7 28 03" src="https://user-images.githubusercontent.com/70746467/161525703-e5292d4b-ed03-4e63-b6fb-84362506bf51.png">

+ __같은 구조__ 와 __크기__ 의 자료를 정해진 방향으로만 쌓을 수 있음
+ ```top```으로 정한 한 곳으로만 접근하도록 제한됨.
+ ```top```: 삽입과 삭제가 일어나는 위치로 ```현재 스택의 가장 위에 있는 데이터 위치```
+ 스택에서 top을 통한 삽입 연산을 __push__ , top을 통한 삭제 연산을 __pop__ 이라고 함

```c
[스택의 추상 자료형]

ADT Stack
데이터: 0개 이상의 원소를 가진 유한 순서 리스트
연산: S ∈ Stack; item ∈ Element;

// 공백 스택 S를 생성하는 연산
createStack(S) ::= create an empty Stack S;

// 스택 S가 공백인지 확인하는 연산
isEmpty(S) ::= if (S is empty) then return true
               else return false;
               
// 스택 S의 top에 item(원소)을 삽입하는 연산
push(S, item) ::= insert item onto the top of Stack S;

// 스택 S의 top에 있는 item(원소)을 삭제하는 연산
pop(S) ::= if (isEmpty(S)) then return error
           else delete and return the top item of Stack S;
           
// 스택 S의 top에 있는 item(원소)을 반환하는 연산
peek(S) ::= if (isEmpty(S)) then return error
            else return the top item of the Stack S;
            
End Stack            
```

```c
[스택의 원소 삽입]

push(S, x)
     // top의 위치를 하나 증가
     top <- top + 1;
     // top 위치가 스택 크기(stack_SIZE)보다 크면 오버플로가 되어 삽입 연산에 실패하고 종료
     if (top > stack_SIZE) then overflow;
     // 오버플로 상태가 아니라면 스택의 top 위치에 x를 삽입
     else
       S(top) <- x;
end push()
```

```c
[스택의 원소 삭제]

pop(S)
     // top이 0이라면 공백 스택이므로 삭제 연산을 수행하지 못하고 종료
     if (top = 0) then underflow;
     else {
       // 공백 스택이 아니면 top에 있는 원소를 삭제하고 반환
       return S(top);
       // top의 위치를 하나 감소
       top <- top - 1;
      }
end pop()
```

```python 
# 파이썬에서 스택 예시
stack = []

삽임(1) - 삽입(2) - 삽입(3) - 삭제() - 삽입(4)
stack.append(1)
stack.append(2)
stack.append(3)
stack.pop()
stack.append(4)

print(stack) # 맨 밑의 원소부터 출럭: [1, 2, 4]
print(stack[::-1]) # 맨 위의 원소부터 출력: [4, 2, 1]
```
+ 파이썬에서 스택을 이용할 때에는 별도의 라이브러리를 사용할 필요가 없음
  + append(): 가장 오른쪽에 원소 삽입
  + pop(): 가장 오른쪽의 원소 삭제
  + 시간 복잡도는 상수시간. O(1)

#### 💡 스택의 응용
1. ```스택을 이용한 역순 문자열```: 문자열을 처음부터 순서대로 스택에 모두 삽입한 뒤, 스택에 있는 원소를 공백 스택이 될 때까지 삭제하면서 반환된 문자를 나열
2. ```시스템 스택```: 프로그램 간의 호출과 복귀에 따른 수행 순서는 가장 나중에 호출된 함수가 가장 먼저 실행을 완료하고 복귀하는 후입선출 구조임. 후입선출 구조를 갖는 스택을 사용하여 호출과 복귀 순서를 관리할 수 있는데 이러한 스택을 시스템 스택이라 함
3. ```스택을 이용한 수식의 괄호 검사```: 수식에 들어가는 괄호는 가장 마지막에 열린 괄호를 가장 먼저 닫는 LIFO의 특성이 있으므로, 스택을 응용하여 수식의 괄호를 검사하는 데 사용할 수 있음
4. ```중위 표기식의 후위 표기식 변환```과 ```후위 표기식의 연산```

### 📍 큐 자료구조
+ 먼저 들어 온 데이터가 먼저 나가는 형식(선입선출(FIFO))의 자료구조
_ex. 놀이공원 줄 서기_
+ __입구와 출구가 모두 뚫려 있는 터널과 같은 형태__ 로 시각화할 수 있음
<img width="555" alt="스크린샷 2022-04-04 오후 7 46 02" src="https://user-images.githubusercontent.com/70746467/161528370-1d42f43e-546c-4fb0-a4c9-880df231ba7c.png">

+ 리스트의 한쪽 끝에서는 삽입 작업만, 반대쪽 끝에서는 삭제 작업만 이루어짐
+ 한 쪽 끝을 ```front(머리)```로 정해 삭제 연산만 수행하고, 다른 쪽 끝을 ```rear(꼬리)```로 정해 삽입 연산만 수행함
+ ```rear```: 가장 뒤에 있는 원소, 즉 큐에 남아 있는 원소 중에서 가장 마지막에 삽입된 원소의 위치를 의미. rear에서만 삽입 가능
+ ```front```: 가장 앞에 있는 원소, 즉 큐에 남아 있는 원소 중에서 가장 먼저 삽입된 원소의 위치를 의미, front에서만 삭제 가능
+ 큐의 ```rear```에서 이루어지는 삽입 연산을 __enQueue__ 라고 하고, ```front```에서 이루어지는 삭제 연산을 __deQueue__ 라고 함

```c
[큐의 추상 자료형]

ADT Queue
데이터: 0개 이상의 원소를 가진 유한 순서 리스트
연산: S ∈ Stack; item ∈ Element;

// 공백 큐를 생성하는 연산
createQueue() ::= create an empty Q;

// 큐가 공백 상태인지 검사하는 연산
isEmpty(Q) ::= if (Q is empty) then return true
               else return false;
               
// 큐의 rear에 원소를 삽입하는 연산
enQueue(Q, item) ::= insert item at the rear of Q;

// 큐의 front에 있는 원소를 삭제하는 연산
deQueue(Q) ::= if (isEmpty(Q)) then return error
           else delete and return the front item Q;
           
// 큐의 front에 있는 원소를 반환하는 연산
peek(Q) ::= if (isEmpty(Q)) then return error
            else return the front item of the Q;
            
End Queue
```

```python
# 파이썬에서 큐 예시
from collections import deque

queue = deque()

삽입(1) - 삽입(2) - 삽입(3) - 삭제() - 삽입(4)
queue.append(1)
queue.append(2)
queue.append(3)
queue.popleft()
queue.append(4)

print(queue) # 먼저 들어온 순서대로 출력: deque([2, 3, 4])
queue.reverse() # 역순으로 바꾸기
print(queue) # 나중에 들어온 원소부터 출력: deque([4, 3, 2])
```
+ __파이썬으로 큐를 구현할 때에는 collections 모듈에서 제공하는 deque 라이브러리 사용__ (리스트로 구현할 순 있지만 비효율적임)

#### 💡 큐의 응용
1. ```작업 버퍼 큐```
2. ```프로세스 스케줄링```
3. ```대기 행렬을 모델링하는 시뮬레이션``` _ex) 공항의 입국 심사 창구_
4. ```너비 우선 탐색(BFS, Breadth-First Search) 구현```
