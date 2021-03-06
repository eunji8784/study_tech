## ๐ ์คํ & ํ
+ ์คํ๊ณผ ํ๋ ์๋ฃ๊ตฌ์กฐ์ ๊ธฐ์ด ๊ฐ๋์ผ๋ก ๋ค์์ ๋ ํต์ฌ์ ์ธ ํจ์๋ก ๊ตฌ์ฑ๋จ
  + __์ฝ์(Push):__ ๋ฐ์ดํฐ๋ฅผ ์ฝ์ํ๋ค.
  + __์ญ์ (Pop):__ ๋ฐ์ดํฐ๋ฅผ ์ญ์ ํ๋ค.
+ ์ถ๊ฐ๋ก ์์๋ฌ์ผ ํ๋ ๊ฐ๋
  + __์ค๋ฒํ๋ก(Overflow):__ ๋ฐ์ดํฐ๊ฐ ์ด๋ฏธ ์ ์ฅ ๊ณต๊ฐ์ ๋ชจ๋ ์ฑ์ ๋๋ฐ ์ฝ์ ์ฐ์ฐ์ ์ํํ  ๋ ๋ฐ์
  + __์ธ๋ํ๋ก(Underflow):__ ๋ฐ์ดํฐ๊ฐ ํ๋๋ ์๋๋ฐ ์ญ์  ์ฐ์ฐ์ ์ํํ  ๋ ๋ฐ์
### ๐ ์คํ ์๋ฃ๊ตฌ์กฐ
+ ๋จผ์  ๋ค์ด ์จ ๋ฐ์ดํฐ๊ฐ ๋์ค์ ๋๊ฐ๋ ํ์(ํ์์ ์ถ(LIFO))์ ์๋ฃ๊ตฌ์กฐ  
_ex. ๋ฐ์ค์๊ธฐ_
+ __์๊ตฌ์ ์ถ๊ตฌ๊ฐ ๋์ผํ ํํ__ ๋ก ์คํ์ ์๊ฐํํ  ์ ์์
<img width="190" alt="แแณแแณแแตแซแแฃแบ 2022-04-04 แแฉแแฎ 7 28 03" src="https://user-images.githubusercontent.com/70746467/161525703-e5292d4b-ed03-4e63-b6fb-84362506bf51.png">

+ __๊ฐ์ ๊ตฌ์กฐ__ ์ __ํฌ๊ธฐ__ ์ ์๋ฃ๋ฅผ ์ ํด์ง ๋ฐฉํฅ์ผ๋ก๋ง ์์ ์ ์์
+ ```top```์ผ๋ก ์ ํ ํ ๊ณณ์ผ๋ก๋ง ์ ๊ทผํ๋๋ก ์ ํ๋จ.
+ ```top```: ์ฝ์๊ณผ ์ญ์ ๊ฐ ์ผ์ด๋๋ ์์น๋ก ```ํ์ฌ ์คํ์ ๊ฐ์ฅ ์์ ์๋ ๋ฐ์ดํฐ ์์น```
+ ์คํ์์ top์ ํตํ ์ฝ์ ์ฐ์ฐ์ __push__ , top์ ํตํ ์ญ์  ์ฐ์ฐ์ __pop__ ์ด๋ผ๊ณ  ํจ

```c
[์คํ์ ์ถ์ ์๋ฃํ]

ADT Stack
๋ฐ์ดํฐ: 0๊ฐ ์ด์์ ์์๋ฅผ ๊ฐ์ง ์ ํ ์์ ๋ฆฌ์คํธ
์ฐ์ฐ: S โ Stack; item โ Element;

// ๊ณต๋ฐฑ ์คํ S๋ฅผ ์์ฑํ๋ ์ฐ์ฐ
createStack(S) ::= create an empty Stack S;

// ์คํ S๊ฐ ๊ณต๋ฐฑ์ธ์ง ํ์ธํ๋ ์ฐ์ฐ
isEmpty(S) ::= if (S is empty) then return true
               else return false;
               
// ์คํ S์ top์ item(์์)์ ์ฝ์ํ๋ ์ฐ์ฐ
push(S, item) ::= insert item onto the top of Stack S;

// ์คํ S์ top์ ์๋ item(์์)์ ์ญ์ ํ๋ ์ฐ์ฐ
pop(S) ::= if (isEmpty(S)) then return error
           else delete and return the top item of Stack S;
           
// ์คํ S์ top์ ์๋ item(์์)์ ๋ฐํํ๋ ์ฐ์ฐ
peek(S) ::= if (isEmpty(S)) then return error
            else return the top item of the Stack S;
            
End Stack            
```

```c
[์คํ์ ์์ ์ฝ์]

push(S, x)
     // top์ ์์น๋ฅผ ํ๋ ์ฆ๊ฐ
     top <- top + 1;
     // top ์์น๊ฐ ์คํ ํฌ๊ธฐ(stack_SIZE)๋ณด๋ค ํฌ๋ฉด ์ค๋ฒํ๋ก๊ฐ ๋์ด ์ฝ์ ์ฐ์ฐ์ ์คํจํ๊ณ  ์ข๋ฃ
     if (top > stack_SIZE) then overflow;
     // ์ค๋ฒํ๋ก ์ํ๊ฐ ์๋๋ผ๋ฉด ์คํ์ top ์์น์ x๋ฅผ ์ฝ์
     else
       S(top) <- x;
end push()
```

```c
[์คํ์ ์์ ์ญ์ ]

pop(S)
     // top์ด 0์ด๋ผ๋ฉด ๊ณต๋ฐฑ ์คํ์ด๋ฏ๋ก ์ญ์  ์ฐ์ฐ์ ์ํํ์ง ๋ชปํ๊ณ  ์ข๋ฃ
     if (top = 0) then underflow;
     else {
       // ๊ณต๋ฐฑ ์คํ์ด ์๋๋ฉด top์ ์๋ ์์๋ฅผ ์ญ์ ํ๊ณ  ๋ฐํ
       return S(top);
       // top์ ์์น๋ฅผ ํ๋ ๊ฐ์
       top <- top - 1;
      }
end pop()
```

```python 
# ํ์ด์ฌ์์ ์คํ ์์
stack = []

์ฝ์(1) - ์ฝ์(2) - ์ฝ์(3) - ์ญ์ () - ์ฝ์(4)
stack.append(1)
stack.append(2)
stack.append(3)
stack.pop()
stack.append(4)

print(stack) # ๋งจ ๋ฐ์ ์์๋ถํฐ ์ถ๋ญ: [1, 2, 4]
print(stack[::-1]) # ๋งจ ์์ ์์๋ถํฐ ์ถ๋ ฅ: [4, 2, 1]
```
+ ํ์ด์ฌ์์ ์คํ์ ์ด์ฉํ  ๋์๋ ๋ณ๋์ ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ฅผ ์ฌ์ฉํ  ํ์๊ฐ ์์
  + append(): ๊ฐ์ฅ ์ค๋ฅธ์ชฝ์ ์์ ์ฝ์
  + pop(): ๊ฐ์ฅ ์ค๋ฅธ์ชฝ์ ์์ ์ญ์ 
  + ์๊ฐ ๋ณต์ก๋๋ ์์์๊ฐ. O(1)

#### ๐ก ์คํ์ ์์ฉ
1. ```์คํ์ ์ด์ฉํ ์ญ์ ๋ฌธ์์ด```: ๋ฌธ์์ด์ ์ฒ์๋ถํฐ ์์๋๋ก ์คํ์ ๋ชจ๋ ์ฝ์ํ ๋ค, ์คํ์ ์๋ ์์๋ฅผ ๊ณต๋ฐฑ ์คํ์ด ๋  ๋๊น์ง ์ญ์ ํ๋ฉด์ ๋ฐํ๋ ๋ฌธ์๋ฅผ ๋์ด
2. ```์์คํ ์คํ```: ํ๋ก๊ทธ๋จ ๊ฐ์ ํธ์ถ๊ณผ ๋ณต๊ท์ ๋ฐ๋ฅธ ์ํ ์์๋ ๊ฐ์ฅ ๋์ค์ ํธ์ถ๋ ํจ์๊ฐ ๊ฐ์ฅ ๋จผ์  ์คํ์ ์๋ฃํ๊ณ  ๋ณต๊ทํ๋ ํ์์ ์ถ ๊ตฌ์กฐ์. ํ์์ ์ถ ๊ตฌ์กฐ๋ฅผ ๊ฐ๋ ์คํ์ ์ฌ์ฉํ์ฌ ํธ์ถ๊ณผ ๋ณต๊ท ์์๋ฅผ ๊ด๋ฆฌํ  ์ ์๋๋ฐ ์ด๋ฌํ ์คํ์ ์์คํ ์คํ์ด๋ผ ํจ
3. ```์คํ์ ์ด์ฉํ ์์์ ๊ดํธ ๊ฒ์ฌ```: ์์์ ๋ค์ด๊ฐ๋ ๊ดํธ๋ ๊ฐ์ฅ ๋ง์ง๋ง์ ์ด๋ฆฐ ๊ดํธ๋ฅผ ๊ฐ์ฅ ๋จผ์  ๋ซ๋ LIFO์ ํน์ฑ์ด ์์ผ๋ฏ๋ก, ์คํ์ ์์ฉํ์ฌ ์์์ ๊ดํธ๋ฅผ ๊ฒ์ฌํ๋ ๋ฐ ์ฌ์ฉํ  ์ ์์
4. ```์ค์ ํ๊ธฐ์์ ํ์ ํ๊ธฐ์ ๋ณํ```๊ณผ ```ํ์ ํ๊ธฐ์์ ์ฐ์ฐ```

### ๐ ํ ์๋ฃ๊ตฌ์กฐ
+ ๋จผ์  ๋ค์ด ์จ ๋ฐ์ดํฐ๊ฐ ๋จผ์  ๋๊ฐ๋ ํ์(์ ์์ ์ถ(FIFO))์ ์๋ฃ๊ตฌ์กฐ
_ex. ๋์ด๊ณต์ ์ค ์๊ธฐ_
+ __์๊ตฌ์ ์ถ๊ตฌ๊ฐ ๋ชจ๋ ๋ซ๋ ค ์๋ ํฐ๋๊ณผ ๊ฐ์ ํํ__ ๋ก ์๊ฐํํ  ์ ์์
<img width="555" alt="แแณแแณแแตแซแแฃแบ 2022-04-04 แแฉแแฎ 7 46 02" src="https://user-images.githubusercontent.com/70746467/161528370-1d42f43e-546c-4fb0-a4c9-880df231ba7c.png">

+ ๋ฆฌ์คํธ์ ํ์ชฝ ๋์์๋ ์ฝ์ ์์๋ง, ๋ฐ๋์ชฝ ๋์์๋ ์ญ์  ์์๋ง ์ด๋ฃจ์ด์ง
+ ํ ์ชฝ ๋์ ```front(๋จธ๋ฆฌ)```๋ก ์ ํด ์ญ์  ์ฐ์ฐ๋ง ์ํํ๊ณ , ๋ค๋ฅธ ์ชฝ ๋์ ```rear(๊ผฌ๋ฆฌ)```๋ก ์ ํด ์ฝ์ ์ฐ์ฐ๋ง ์ํํจ
+ ```rear```: ๊ฐ์ฅ ๋ค์ ์๋ ์์, ์ฆ ํ์ ๋จ์ ์๋ ์์ ์ค์์ ๊ฐ์ฅ ๋ง์ง๋ง์ ์ฝ์๋ ์์์ ์์น๋ฅผ ์๋ฏธ. rear์์๋ง ์ฝ์ ๊ฐ๋ฅ
+ ```front```: ๊ฐ์ฅ ์์ ์๋ ์์, ์ฆ ํ์ ๋จ์ ์๋ ์์ ์ค์์ ๊ฐ์ฅ ๋จผ์  ์ฝ์๋ ์์์ ์์น๋ฅผ ์๋ฏธ, front์์๋ง ์ญ์  ๊ฐ๋ฅ
+ ํ์ ```rear```์์ ์ด๋ฃจ์ด์ง๋ ์ฝ์ ์ฐ์ฐ์ __enQueue__ ๋ผ๊ณ  ํ๊ณ , ```front```์์ ์ด๋ฃจ์ด์ง๋ ์ญ์  ์ฐ์ฐ์ __deQueue__ ๋ผ๊ณ  ํจ

```c
[ํ์ ์ถ์ ์๋ฃํ]

ADT Queue
๋ฐ์ดํฐ: 0๊ฐ ์ด์์ ์์๋ฅผ ๊ฐ์ง ์ ํ ์์ ๋ฆฌ์คํธ
์ฐ์ฐ: S โ Stack; item โ Element;

// ๊ณต๋ฐฑ ํ๋ฅผ ์์ฑํ๋ ์ฐ์ฐ
createQueue() ::= create an empty Q;

// ํ๊ฐ ๊ณต๋ฐฑ ์ํ์ธ์ง ๊ฒ์ฌํ๋ ์ฐ์ฐ
isEmpty(Q) ::= if (Q is empty) then return true
               else return false;
               
// ํ์ rear์ ์์๋ฅผ ์ฝ์ํ๋ ์ฐ์ฐ
enQueue(Q, item) ::= insert item at the rear of Q;

// ํ์ front์ ์๋ ์์๋ฅผ ์ญ์ ํ๋ ์ฐ์ฐ
deQueue(Q) ::= if (isEmpty(Q)) then return error
           else delete and return the front item Q;
           
// ํ์ front์ ์๋ ์์๋ฅผ ๋ฐํํ๋ ์ฐ์ฐ
peek(Q) ::= if (isEmpty(Q)) then return error
            else return the front item of the Q;
            
End Queue
```

```python
# ํ์ด์ฌ์์ ํ ์์
from collections import deque

queue = deque()

์ฝ์(1) - ์ฝ์(2) - ์ฝ์(3) - ์ญ์ () - ์ฝ์(4)
queue.append(1)
queue.append(2)
queue.append(3)
queue.popleft()
queue.append(4)

print(queue) # ๋จผ์  ๋ค์ด์จ ์์๋๋ก ์ถ๋ ฅ: deque([2, 3, 4])
queue.reverse() # ์ญ์์ผ๋ก ๋ฐ๊พธ๊ธฐ
print(queue) # ๋์ค์ ๋ค์ด์จ ์์๋ถํฐ ์ถ๋ ฅ: deque([4, 3, 2])
```
+ __ํ์ด์ฌ์ผ๋ก ํ๋ฅผ ๊ตฌํํ  ๋์๋ collections ๋ชจ๋์์ ์ ๊ณตํ๋ deque ๋ผ์ด๋ธ๋ฌ๋ฆฌ ์ฌ์ฉ__ (๋ฆฌ์คํธ๋ก ๊ตฌํํ  ์ ์์ง๋ง ๋นํจ์จ์ ์)

#### ๐ก ํ์ ์์ฉ
1. ```์์ ๋ฒํผ ํ```
2. ```ํ๋ก์ธ์ค ์ค์ผ์ค๋ง```
3. ```๋๊ธฐ ํ๋ ฌ์ ๋ชจ๋ธ๋งํ๋ ์๋ฎฌ๋ ์ด์``` _ex) ๊ณตํญ์ ์๊ตญ ์ฌ์ฌ ์ฐฝ๊ตฌ_
4. ```๋๋น ์ฐ์  ํ์(BFS, Breadth-First Search) ๊ตฌํ```
