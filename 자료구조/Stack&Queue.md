ADT(abstract data type)

-추상 자료형
-개념적으로 어떤 동작이 있는지만 정의
-구현에 대해서는 다루지 않음

DS(data structure)
-ADT에서 정의된 동작을 실제로 구현함

스택(stack)
LIFO(Last In First Out) 형태로 데이터를 저장

스택 주요 동작
- push 아이템 넣기
- pop 아이템 꺼내기
- peek 최상단에 있는 아이템 확인하기

스택 동작 방식 설명

push(1)
push(2)
push(3)

pop을 하면 최상단에 있는 3이 꺼내진다

peek 하면 = 2가 확인 된다


큐(queue)

FIFO(First In First Out) 형태로 데이터를 저장

큐 주요 동작 
- enqueue 아이템 넣기 
- dequeue 아이템 빼기
- peek 꺼내게될 아이템 확인하기 

큐 동작 방식 설명 
enqueue(1)
enqueue(2)
enqueue(3)

dequeue() = 1
dequeue() = 2
peek = 3



스택/큐 관련 에러와 해결
StackOverFlowError

재귀함수(recursive funcion)에서 탈출 못해서 발생

탈출 조건을 잘 써주면 된다.

OutOfMemoryError
java의 힙(heap) 메모리를 다 썼을 때 발생

큐에 데이터가 계속 쌓이기만 한다면 발생 

큐 사이즈를 고정

큐가 다 찼으면 어떻게 해결 할까?
- 예외(exception) 던지기 
- 특별한 값(null or false)을 반환
- 성공 할때까지 영원히 스레드 블락(block)
- 제한된 시간만 블락되고 그래도 안 되면 포기 


