네트워크


L2

NIC : Network Interface Card 
흔히 LAN 카드이다.

LAN은 규모를 말함 

유/무선 NIC이 있지만 굳이 구별하지 않고 NIC이라고 할 떄가 많다
NIC은 H/W이며 MAC주소를 갖는다

(L2) 수준의 단위를 Frame이라고 한다.

L2 Access switch

End-point와 직접 연결되는 스위치

MAC주소를 근거로 스위칭


Link-up 잘 연결됐다
Link-down 연결 안 됐다
라우터에 연결 되면 UpLink


L2 Distribution switch

쉽게 생각하면 L2 Access 스위치를 위한 스위치 
VLAN 기능을 제공하는 것이 일반적 

LAN과 WAN의 경계 그리고 Broadcast

Broadcast 범위를 생각해보자
Broadcast 주소라는 매우 특별한 주소가 존재한다.(MAC, IP 모두 존재)
논리적인 것인지 아니면 물리적인 것인지로 구분하는 것도 방법이다.
일단 MAN(Metroplitan Area Network)은 제외하자.

브로드캐스트는 최소화 해야한다.

L3

IPv4 주소의 구조

32비트이다 
8개의 비트씩 잘라서 표현 
ex) 192.168.0.10 

잘라서 표현 Network ID와 Host ID

예를 들어서 물류센터라고 생각하고
192.168.0 가 동이다 / 그리고 그 뒤에 나오는 10은 번지이다.

L3 Packet  

Packet = 단위 데이터 (작은 데이터)
Packet이라는 말은 L3 IP Packet으로 외워라 
Packet : Header와 Payload로 나뉘며 이는 상대적인 분류이다.
*최대크기* 는 MTU  1500bytes , 1.4KB이다. (제일중요)

Header 와 Payload로 나눠짐 
Header에 있는 정보 출발지 - 목적지

Encapsulation 

별것 아니다. 러시아 전통 목각 인형인 마트료시카 인형을 떠올려라

L2 안에 L3안에 L4안에 계속 들어있다 그렇지만 끝은 있다

패킷의 생성, 전달, 소멸

 Port번호가 이름 

계층별 데이터 단위 

L1~L2 Frame / 데이터 단위 Frame 
L3 ~ packet  / 데이터 단위 MTU 1500byte
L4 ~ Segment / 데이터 단위 : MSS 1460byte
 중간에 소켓이 있음  /  소켓  Stream
L5 ~ Stream / 데이터 덩어리 

Stream의 특징 : 시작은 있으나 끝은 모름 연속적으로 이어진 큰 데이터


파리에서 에펠탑을 택배로 보내려면 어떻게 해야 할까?


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

널널한 개발자 :인터넷은 라우터의 집합체 라고 할 수 있는 논리 네트워크이다.