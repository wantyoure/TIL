B tree가 왜 DB 인덱스로 사용되는지를 설명합니다

secondary storage

* 데이터를 처리하는 속도가 가장 느리다
* 데이터를 저장하는 용량이 가장 크다
* block 단위로 데이터를 읽고 쓴다
  (*file system이 데이터를 읽고 쓰는 논리적인 단위
   *block의 크기는 2의 승수로 표현되며 대표적인 block size는 4KB, 8KB, 16KB)

* DB는 secondary storage에 저장된다
* DB에서 데이터를 조회할 때 secondary storage에 최대한 적게 접근하는 것이 성능 면에서 좋다
* block 단위로 읽고 쓰기 때문에 연관된 데이터를 모아서 저장하면 더 효율적으로 읽고 쓸 수 있다 

* B tree 노드는 block 단위의 저장 공간을 알차게 사용할 수 있다 

