Map

-key-value pair들을 저장하는 ADT
-같은 key를 가지는 pair는 최대 한개만 존재 
-associative array, dictionary라고 불리기도 함

map 구현체 
-hash table
-tree-based

hash table(hash map)
-배열과 해시 함수(hash function)를 사용하여 
map을 구현한 자료 구조 
-(일반적으로) 상수 시간으로 데이터에 접근하기 때문에 빠름

Hash function
-임의의 크기를 가지는 type의 데이터를 고정된 크기를 가지는 type의 데이터로 변환하는 함수
-해쉬테이블에서 임의의 데이터를 정수로 변환하는 함수 
 
해쉬충돌(hash collision)
-key는 다른데 hash가 같을 때 
-key도 hash도 다른데 hash % map_capa 결과가 같을 때 

hasg collision 해결 방법 
-open addressing(inear probing) / 공간이 없으면 밑으로 보냄 /
-separate chaining 리스트 형식으로 저장

hash table resizing
-데이터가 많이 차게 되면 크기를 늘려줘야 한다 
