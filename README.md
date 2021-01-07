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

위 그림 처럼 순서 보장이 가능한 이유는 TCP 정보에는 `전송 제어, 순서, 검증 정보` 등이 추가가 되어있다.

- UDP 특징
  - 사용자 데이터그램 프로토콜(User Datagram Protocol)
  - 하얀 도화지에 비유(기능이 거의 없음)
  - 연결지향 - TCP 3 way handshake X
  - 데이터 전달 보증 X
  - 순서 보장 X
  - 데이터 전달 및 순서가 보장되지 않지만, 단순하고 빠름
  - IP와 거의 같다. +PORT +체크섬 정도만 추가
  - 애플리케이션에서 추가 작업 필요
  
## Port

![img](/images/5.JPG)

- 0 ~ 65535 : 할당 가능
- 0 ~ 1023 : 잘 알려진 포트, 사용하지 않는 것이 좋음
- FTP - 20, 21
- TELNET - 23
- HTTP - 80
- HTTPS - 443

## DNS

DNS(Domain Name System) 도메인 명을 IP 로 변환

![img](/images/6.JPG)

## URI 와 웹 브라우저 요청 흐름

- URI(Uniform Resource Identifier)
  - URN(Uniform Resource Name)
    - 리소스에 이름을 부여
    - 이름은 변하지 않는다.
    - URN 이름만으로 실제 리소스를 찾을 수 있는 방법이 보편화 되지 않음
    - urn:isbn:8960777331 (어떤 책의 isbn URN)
  - URL(Uniform Resource Locator) 
    - 리소스가 있는 위치를 지정
    - 위치는 변할 수 있다.
  
- URI 단어 의미
  - Uniform : 리소스 식별하는 통일된 방식
  - Resource : 자원, URI 로 식별할 수 있는 모든 것
  - Identifier : 다른 항목과 구분하는데 필요한 정보
  
![img](/images/7.JPG)

### URL

- 문법
  - `scheme://[userinfo@]host[:port][/path][?query][#fragment]`
  - https://www.google.com:443/search?q=hello&hl=ko

- `scheme`
  - 주로 프로토콜 사용
  - 프로토콜 : 어떤 방식으로 자원에 접근할 것인가 하는 약속 규칙
    - ex) http, https, ftp 등
  - http는 80 포트, https는 443 포트를 주로 사용, 포트는 생략 가능
  - https는 http에 보안 추가 (HTTP Secure)
- `userinfo`
  - URL 에 사용자 정보를 포함해서 인증
  - 거의 사용 안함
- `host`
  - 호스트명
  - 도메인명 또는 IP 주소를 직접 사용 가능
    - ex) www.google.com
- `port`
  - 접속 포트
  - 일반적으로 생략(http는 80, https는 443)
- `path`
  - 리소스 경로, 계층적 구조
    - ex) /members/100, /items/iphone12
- `query`
  - key=value 형태
  - `?`로 시작 `&`로 추가 가능 
    - ?keyA=valueA&keyB=valueB
  - query parameter, query string 등으로 불린다. 
  - 웹 서버에 제공하는 파라미터
- `fragment`
  - html 내부 북마크 등에 사용
  - 서버에 전송하는 정보 아님

# HTTP(HyperText Transfer Protocol)

- `HTTP 메시지에 모든 것을 전송`
  - HTML, TEXT
  - IMAGE, 음성, 영상, 파일
  - JSON, XML
  - 거의 모든 형태의 데이터 전송 가능
  - 서버간에 데이터를 주고 받을 때도 대부분 HTTP 사용
  
- `역사`
  - HTTP/0.9 1991년: GET 메서드만 지원, HTTP 헤더X
  - HTTP/1.0 1996년: 메서드, 헤더 추가
  - `HTTP/1.1` 1997년: 가장 많이 사용, 우리에게 가장 중요한 버전
  - RFC2068 (1997) -> RFC2616 (1999) -> RFC7230~7235 (2014)
  - HTTP/2 2015년: 성능 개선
  - HTTP/3 진행중: TCP 대신에 UDP 사용, 성능 개선
  
- `사용 추세`
  - TCP: HTTP/1.1, HTTP/2
  - UDP: HTTP/3
  - 현재 HTTP/1.1 주로 사용
  - HTTP/2, HTTP/3 도 점점 증가

- `특징`
  - 클라이언트 서버 구조
    - Request Response 구조
    - 클라이언트는 서버에 요청을 보내고, 응답을 대기
    - 서버가 요청에 대한 결과를 만들어서 응답
    - `클라이언트 서버로 구조를 나누면 좋은점은 비지니스로직이나 데이터를 서버에 전부 밀어넣고, 클라이언트는 UI 와 UX 에 집중한다. 이렇게되면 클라이언트와 서버가 각각 독립적으로 진화할 수 있다. 즉, 클라이언트는 복잡한 비지니스 로직을 다룰 필요가 없게된다.`
  - 무상태 프로토콜(stateless)
    - 서버가 클라이언트의 상태를 보존X
    - 장점: 서버 확장성 높음(스케일 아웃)
    - 단점: 클라이언트가 추가 데이터 전송
    - 무상태는 응답 서버를 쉽게 바꿀 수 있다. -> 무한한 서버 증설 가능
  - 비연결성
    - 일반적으로 초 단위의 이하의 빠른 속도로 응답
    - 1시간 동안 수천명이 서비스를 사용해도 실제 서버에서 동시에 처리하는 요청은 수십개 이하로 매우 작음
  - HTTP 메시지
  - 단순함, 확장 가능
 
- `실무 한계`
  - 모든 것을 무상태로 설계 할 수 있는 경우도 있고 없는 경우도 있다.
  - 무상태
    - 예) 로그인이 필요 없는 단순한 서비스 소개 화면
  - 상태 유지
    - 예) 로그인
    - 로그인한 사용자의 경우 로그인 했다는 상태를 서버에 유지
    - 일반적으로 브라우저 쿠키와 서버 세션등을 사용해서 상태 유지
    - 상태 유지는 최소한만 사용

- `비 연결성 한계와 극복`
  - TCP/IP 연결을 새로 맺어야 함 - 3 way handshake 시간 추가
  - 웹 브라우저로 사이트를 요청하면 HTML 뿐만 아니라 자바스크립트, css, 추가 이미지 등 수 많은 자원이 함께 다운로드
  - 지금은 HTTP 지속 연결(Persistent Connections)로 문제 해결
  - HTTP/2, HTTP/3에서 더 많은 최적화
  
![img](/images/8.JPG)

![img](/images/9.JPG)

## 스테이스리스를 기억하자(서버 개발자들이 어려워하는 업무)

- 정말 같은 시간에 딱 맞추어 발생하는 대용량 트래픽
  - ex) 선착순 이벤트, 명절 KTX 예약, 학과 수업 등록
  - ex) 저녁 6:00 선착순 1000명 치킨 할인 이벤트 -> 수만명 동시 요청
  
대용량 트래픽은 최대한 머리를 쥐어짜서 stateless 하게 만들어야한다. stateless 는 스케일 아웃의 장점이 있으므로 대용량 트래픽이 발생하면
서버를 확 늘려서 대응을 할 수 있는 부분들이 많아진다.

그래서 이벤트 설계시 다음과 같은 방식으로 많이한다. 첫 페이지는 로그인도 필요없는 정적 페이지만 뿌린다.(상태없는 순수한 html) 그리고 사람들이
그 페이지에서 이것저것 보고 머무르는 시간을 가지게끔 한다음에 이벤트 참여 버튼을 누르게하거나 한다.
