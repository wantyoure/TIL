### 네트워크
___



>L2

NIC : Network Interface Card 
흔히 LAN 카드이다. 

* LAN은 규모를 말함 

 * 유/무선 NIC이 있지만 굳이 구별하지 않고 

    NIC이라고 할 떄가 많다
    NIC은 H/W이며 **MAC** 주소를 갖는다

    (L2) 수준의 단위를 **Frame** 이라고 한다.

>L2 Access switch

* End-point와 직접 연결되는 스위치

  MAC주소를 근거로 스위칭


  Link-up 잘 연결됐다

  Link-down 연결 안 됐다
라우터에 연결 되면 UpLink


>L2 Distribution switch

* 쉽게 생각하면 L2 Access 스위치를 위한 스위치 

  VLAN 기능을 제공하는 것이 일반적 

  
>LAN과 WAN의 경계 그리고 Broadcast

* Broadcast 범위를 생각해보자
  Broadcast 주소라는 매우 특별한 주소가 존재한다.(MAC, IP 모두 존재)
논리적인 것인지 아니면 물리적인 것인지로 구분하는 것도 방법이다.
일단 MAN(Metroplitan Area Network)은 제외하자.

   브로드캐스트는 최소화 해야한다.

>L3

* IPv4 주소의 구조

  32비트이다 
8개의 비트씩 잘라서 표현 
ex) 192.168.0.10 

  잘라서 표현 Network ID와 Host ID
     |NetworkID|HostID|
     |:--:|:--:|
     |192.168.0|10|
    


  예를 들어서 물류센터라고 생각하고
  192.168.0 가 동이다 / 그리고 그 뒤에 나오는 10은 번지이다.
___
     **L3 Packet**

* Packet = 단위 데이터 (작은 데이터)
* Packet이라는 말은 L3 IP Packet으로 외워라 
* Packet : Header와 Payload로 나뉘며 이는 상대적인 분류이다.
 **최대크기** 는 MTU  1500bytes , 1.4KB이다. (제일중요)

   Header 와 Payload로 나눠짐 
   Header에 있는 정보 출발지 - 목적지

>Encapsulation 

별것 아니다. 러시아 전통 목각 인형인 마트료시카 인형을 떠올려라

L2 안에 L3안에 L4안에 계속 들어있다 그렇지만 끝은 있다

패킷의 생성, 전달, 소멸

 Port번호가 이름 

계층별 데이터 단위 

* L1~L2 Frame / 데이터 단위 Frame 
* L3 ~ packet  / 데이터 단위 MTU 1500byte
* L4 ~ Segment / 데이터 단위 : MSS 1460byte
*  중간에 소켓이 있음  /  소켓  Stream
* L5 ~ Stream / 데이터 덩어리 

  Stream의 특징 : 시작은 있으나 끝은 모름 연속적으로 이어진 큰 데이터


>파리에서 에펠탑을 택배로 보내려면 어떻게 해야 할까?


 TCP는 순서가 중요하다

 서브넷 마스크

서브넷 마스크 기준으로 Net ID 와 Host ID를 자른다

서브넷 마스크와 Net ID와 같다면 패킷이 우리쪽으로 온다

CIDR이 등장

Broadcast IP주소

ex) 192.168.0.255

Host 자신을 가리키는 IP주소

127.0.0.1 : Loop back address

나에게 접속, 접근, 연결 할 때 

널널한 개발자 : ex)인터넷은 라우터의 집합체 라고 할 수 있는 논리 네트워크이다.


>TTL과 단편화 

Time TO Live는 세포의 텔로미어 같은 역할을 한다.

단편화는 MTU크기 차이로 발생한다.

보통 단편의 조립은 수신측 Host에서 이루어진다.

128이라고 할때 라우터를 지날때마다 -1씩 된다

VPN IPSec이 보안 때문에 단편화가 날 수 있다.


>인터넷 설정 자동화를 위한 DHCP

`인터넷 사용전에 해야 할 설정 `

 * IP주소
 * Subnet mask
 * Gateway IP주소
 * DNS 주소

    보통은 자동으로 설정된다

>DHCP(Dynamic Host Configuration Protocol)

체계는 주소를 할당하는 서버와 할당 받으려는 클라이언트로 구성된다.

복잡한 인터넷 설정을 자동으로 해준다고 볼 수 있는데 핵심은 내가 사용할 IP주소를 서버가 알려준다는 것에 있다.


>ARP(Address Resolution Protocol)

ARP는 IP주소로 MAC주소를 알아내려 할 때 활용된다.
보통의 경우 PC를 부팅하면 Gateway의 MAC를 찾아내기 위해 ARP Request가 발생하며 이에 
대응하는 Reply로 MAC주소를 알 수 있다.

Host 주소는 MAC 주소, IP주소가 있다.


>Ping과 RTT

Ping 유틸리티(그냥 프로그램)는 특정 Host 대한 RTT(Round Trip Time)을 측정할 목적으로 사용된다.
ICMP 프로토콜을 이용한다.
DoS(Denial of Service) 공격용으로 악용되기도 한다.

>L4

**TCP와 UDP**

TCP에만 연결(Connection, Session) 개념이 있다.

연결은 결과적으로 순서번호로 구현된다.

연결은 상태(전이) 개념을 동반한다. 상태(전이) 란 ? : 통화로 비유 하자면 통화걸기전 , 통화 연결 후 

TCP는 배려남, UDP는 (배려가 없는) 나쁜 남자에 비유할 수 있다.

TCP 연결 과정 (3-way handshaking)

client : SYN  - > server : SYN + ACK -> client : ACK

TPC 연결 종료 과정(4-way handshaking)

client : FIN + ACK 보냄

`server에서 ACK를 받음 
server : FIN + ACK 보냄
client에서 ACK를 받음`

TCP Header 형식
(사진 첨부)

UDP Header 형식
(사진 첨부)


>TCP '연결'이라는 착각 

재전송 타이머의 기본 근사 값은 대략 3초, 하지만

대부분의 운영체제들은 1초 미만이다.

재전송 타이머 만료 후에도 확인 응답을 받지 못한 경우 세그먼트를 재전송하고 
RTO(Retransmission Time-Out) 값은 두 배로 증가한다.
예를들어 1초> 2초> 4초> 8초> 16초 간격으로 재전송한다.
보통 최대 5회 재전송을 시도하고 5회 이상 모두 실패할 경우 보통 전송 오류가 발생한다.


>DNS 

**분산 구조형 데이터베이스**

데이터베이스 시스템의 분산 구성

데이터의 영역별 구분 및 분산관리

도메인의 네임서버 및 도메인 데이터는 해당 관리주체에 의해 독립적으로 관리됨

 * 트리 구조의 도메인 네임 체계
 * Domain : 영역, 영토를 의미
 * 도메인 네임의 자율적 생성
 * 생성된 도메인 네임은 언제나 유일 하도록 네임 체계 구성
