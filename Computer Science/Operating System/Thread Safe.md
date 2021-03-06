## 💡 스레드 안전성 (Thread Safe)
+ ```멀티 스레드 프로그래밍```환경에서 __여러 스레드__ 가 __동시에__ 어떤 함수나 변수, 혹은 객체에 접근해도 프로그램의 실행에 문제가 없는 것  .
+ ex. 하나의 함수가 어떤 스레드에서 실행중일 때 다른 스레드가 해당 함수를 호출해서 동시에 실행하더라도 각 스레드에서의 함수 호출 결과가 문제 없이 동일하게 도출되는 것.

## 📚 Thread Safety 하게 코드를 작성하는 법
+ ```Re-entrancy```
  + 여러 스레드가 동시에 똑같은 함수를 호출하더라도 각각이 올바른 결과를 도출할 수 있어야 함.
  + 스레드끼리 독립적일 수 있어야 함.
+ ```Tread-local storage```
  + 공유 자원(ex. 전역 변수 등)의 사용을 최소화하여 각각의 스레드에서만 접근 가능한 저장소들을 사용함으로써 한 자원에 대한 스레드의 동시 접근을 막음.
+ ```Mutual Exclustion```
  + 공유 자원의 사용이 불가피할 경우에는 해당 자원의 접근을 세마포어 등의 락으로 통제함.
  + ex. 동기화 객체, Python의 threading.lock
+ ```Authomic operations```
  + 공유 자원에 접근할 때 원자 연산을 이용하거나 ‘원자적’으로 정의된 접근 방법을 사용함으로써 상호 배제를 구현할 수 있음.
  + ex. “+=” 연산의 경우, ‘+’ 연산 후에 ‘=’ 연산을 하기 때문에 원자적이라고 하기 어렵다.

### 📌 팁
+ thread-safey가 자명한 경우를 제외하면 보통은 구현이 가장 쉬운 Mutual exclusion(동기화 객체)를 사용하는 것이 일반적.
+ 이 mutual exclusion을 사용하는 예시가 바로 Python의 ```GIL(Global Interpreter Lock)```. 
+ CPython의 메모리 관리 상태가 thread-safe하지 않기 때문에 Python에서 GIL이 필요함. 즉, 스레드 안전의 해결책으로서 사용하는 것이 GIL.
