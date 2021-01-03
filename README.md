# Http 웹 기본 지식

> [인프런. Http 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC)

## 인터넷 통신

- IP(인터넷 프로토콜)
  - 지정한 IP 주소(IP Address)에 데이터 전달
  - 패킷(Packet)이라는 통신 단위로 데이터 전달

- IP 프로토콜의 한계
  - 비연결성
    - 패킷을 받을 대상이 없거나 서비스 불능 상태여도 패킷 전송
  - 비신뢰성
    - 중간에 패킷이 사라지면?
    - 패킷이 순서대로 안오면?
  - 프로그램 구분
    - 같은 IP 를 사용하는 서버에서 통신하는 애플리케이션이 둘 이상이라면?

## TCP, UDP

IP 프로토콜의 한계점을 해결하기 위한 것이 TCP, UDP 이다.

![img](/images/1.JPG)

- TCP 특징
  - 전송 제어 프로토콜(Transmission Control Protocol)
  - 연결지향 - TCP 3 way handshake (가상연결)
  - 데이터 전달 보증
  - 순서 보장
  - 신뢰할 수 있는 프로토콜
  - 현재는 대부분 TCP 사용

![img](/images/2.JPG)

![img](/images/3.JPG)

![img](/images/4.JPG)
