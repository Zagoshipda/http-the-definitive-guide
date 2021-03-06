# 01. HTTP 개관

* HTTP - Hypertext Transfer Protocol.
  * 현대 인터넷의 공용어.

## 1.1 HTTP: 인터넷의 멀티미디어 배달부

* HTTP는 웹 서버로부터 다양한 형태의 대량의 정보를 빠르고 간편하고 정확하게 웹브라우저로 옮겨준다.
* HTTP는 신뢰성있는 데이터 전송 프로토콜을 사용한다.
  * `TCP/IP`
  * 사용자는 인터넷에서 얻은 정보가 손상된 게 아닌지 염려할 필요 없다.
  * 개발자는 애플리케이션 고유 기능 개발에 집중할 수 있다.

## 1.2 웹 클라이언트와 서버

* 웹 콘텐츠는 웹 서버에 존재.
* 웹 서버는 HTTP 프로토콜로 의사소통하기에 HTTP서버로 불림.
  * 웹 서버는 인터넷의 데이터 저장, HTTP 클라이언트가 요청한 데이터 제공.
* HTTP 클라이언트와 서버는 WWW의 기본 요소.
* 가장 흔한 클라이언트는 웹 브라우저.
  * 웹 브라우저는 서버에게 HTTP 객체를 요청하고 화면에 보여준다.
    * 서버는 요청받은 객체를 찾고, 성공하면 타입, 길이 등의 정보를 HTTP응답에 실어 클라이언트에게 보낸다.

## 1.3 리소스

* 웹 서버는 웹 리소스를 관리하고 제공.
* 웹 리소스는 웹 콘텐츠의 원천.
* 가장 단순한 웹 리소스는 웹 서버 파일 시스템의 정적 파일.
* 리소스는 콘텐츠를 생산하는 프로그램이 될 수도 있다.
  * 동적 콘텐츠 리소스.
  * 사용자가 누구인지, 어떤 정보 요청했는지, 몇 시인지등에 따라 콘텐츠를 생성.

### 1.3.1 미디어 타입

* HTTP는 웹에서 전송되는 객체 각각에 MIME 타입이라는 데이터 포멧 라벨을 붙인다.
* MIME - Multipurpose Internet Mail Extensions
  * 원래 각기 다른 전자메일 시스템 사이에서 메시지가 오갈 때 겪는 문제점을 해결하기 위해 설계.
  * HTTP에서 멀티미디어 콘텐츠를 기술하고 라벨을 붙이기 위해 채택됨.
* 웹 서버는 모든 HTTP 객체 데이터에 MIME 타입을 붙임.
  * 웹 브라우저가 객체를 돌려받을 때, 다룰 수 있는 객체인지 MIME 타입을 통해 확인한다.
  * 대부분의 웹브라우저는 잘 알려진 객체타입 수백가지를 다룰 수 있음.
* MIME 타입은 주 타입\(primary object type\), 부 타입\(specific subtype\) 으로 구성된 문자열 라벨.
  * `text/html`, `text/plain`, `image/jpeg`, `image/gif` 등이 있음.

### 1.3.2 URI

* 웹 서버 리소스는 각자 이름을 갖고 있음.
* 클라이언트는 관심있는 리소스를 지목할 수 있음.
* 서버 리소스 이름 - URI, Uniform Resource Identifier
  * 인터넷의 우편물 주소 같은 것.
  * 리소스를 고유하게 식별, 위치 지정.
  * `http://www.joes-hardward.com/specials/saw-blade.gif`
* URI는 URL, URN으로 구별.

### 1.3.3 URL

* URL - Uniform Resource Locator.
* 특정 서버의 한 리소스에 대한 구체적인 위치를 서술함.
  * 리소스가 정확히 어디에 있고 어떻게 접근할 수 있는지를 분명히 알려줌.
* URL은 세 부분으로 이루어진 표준 포멧을 따름.
  * 첫번째 - scheme
    * 리소스에 접근하기 위해 사용될 프로토콜 서술.
    * 보통 HTTP 프로토콜.
  * 두번째 - 서버의 인터넷 주소.
  * 세번째 - 웹 서버의 리소스.
* 오늘날 대부분의 URI는 URL.

### 1.3.4 URN

* URN - Uniform Resource Name
* 리소스에 대해, 그 리소스의 위치에 영향 받지 않는 유일무이한 이름 역할.
* 리소스를 옮겨도 문제없이 동작.
* 여러 종류의 네트워크 접속 프로토콜로 접근해도 문제 없다.
* ex\) `urn:ietf:rfc:2141`
* 여전히 실험중인 상태.
  * 리소스 위치 분석 위한 인프라 자원 필요.
* 앞으로는 URI, URL이 같은 의미.

## 1.4 트랜잭션

* HTTP 트랜잭션은 요청 명령, 응답 결과로 구성.
  * 요청 명령 : 클라이언트 → 서버
  * 응답 결과 : 서버 → 클라이언트
* 상호작용은 정형화된 데이터 덩어리를 이용해 이루어짐.

### 1.4.1 메서드

* HTTP는 여러가지 종류의 요청 명령을 지원.
* 모든 HTTP **요청** 메시지는 한 개의 메서드를 가짐.
* 메서드는 서버에게 어떤 동작이 취해져야 하는지를 말해준다.
* 메서드
  * GET - 서버에서 클라이언트로 지정한 리소스 보내라.
  * PUT - 클라이언트에서 서버로 보낸 데이터를 지정한 이름의 리소스로 저장하라.
  * DELETE - 지정한 리소스를 삭제하라.
  * POST - 클라이언트 데이터를 서버 게이트웨이 애플리케이션으로 보내라.
  * HEAD - 지정한 리소스에 대한 응답에서, HTTP 헤더 부분만 보내라.

### 1.4.2 상태 코드

* 모든 HTTP 응답 메시지는 상태 코드와 함께 반환됨.
* 클라이언트에게 요청이 성공했는지 아니면 추가 조치가 필요한지 알려주는 세 자리 숫자.
* 상태 코드
  * `200` - 문서가 바르게 반환.
  * `302` - 다시 보내라. 다른 곳에 가서 리소스를 가져가라.
  * `404` - 없음. 리소스를 찾을 수 없다.

### 1.4.3 웹페이지는 여러 객체로 이루어질 수 있다

* 애플리케이션은 보통 하나의 작업을 수행하기 위해 여러 HTTP 트랜잭션을 수행.
  * 웹브라우저는 시각적으로 풍부한 웹페이지를 가져올 때 대량의 HTTP 트랜잭션을 수행.
* **웹페이지**는 하나의 리소스가 아닌 리소스의 모음.

## 1.5 메시지

* HTTP 메시지는 단순한 줄 단위의 문자열.
* 이진 형식이 아닌 일반 문자열이기에, 사람이 읽고 쓰기 쉬움.
* 웹 클라이언트 → 웹 서버 - 요청 메시지
* 웹 서버 → 웹 클라이언트 - 응답 메시지
* 다른 종류의 메시지는 없음.
* 메시지의 구성
  * 시작줄
    * 메시지의 첫 줄.
    * 요청이라면 무엇을 해야 하는지, 응답이라면 무슨 일이 일어났는지를 나타냄.
  * 헤더
    * 시작줄 다음에 0개 이상의 헤더 필드가 이어짐.
    * 쉬운 구문 분석을 위해, 각 헤더 필드는 `:` 으로 구분된 하나의 이름과 하나의 값으로 이루어짐.
    * 필드를 추가하기 위해선 한 줄을 더하면 됨.
    * 헤더는 빈 줄로 끝남.
  * 본문
    * 어떤 종류의 데이터든 들어갈 수 있음.
    * 요청의 본문은 웹 서버로 데이터를 실어 보냄.
    * 응답의 본문은 클라이언트로 데이터를 반환.
    * 임의의 이진 데이터를 포함할 수 있음.
    * 텍스트 포함 가능.

### 1.5.1 간단한 메시지의 예

* 서버의 HTTP 응답 메시지에는 HTTP버전 번호, 성공 상태 코드, 사유 구절, 응답 헤더 필드 영역, 요청한 문서가 담겨있는 응답 본문 등이 들어있음.
* 응답 본문 길이는 `Content-Length` 헤더, 문서의 MIME 타입은 `Content-Type` 헤더에 들어있음.

## 1.6 TCP 커넥션

### 1.6.1 TCP/_IP_

* HTTP는 애플리케이션 계층 프로토콜.
  * 네트워크 통신의 핵심적인 세부사항에 대해 신경쓰지 않음.
  * TCP/IP 를 사용.
    * TCP
      * 오류 없는 데이터 전송.
      * 순서에 맞는 전달 - 데이터는 언제나 보낸 순서대로 도착함.
      * 조각나지 않는 데이터 스트림 - 언제든 어떤 크기로든 보낼 수 있음.
* 인터넷 자체가 TCP/IP 에 기초함.
  * TCP/IP
    * TCP와 IP가 층을 이루는, 패킷 교환 네트워크 프로토콜의 집합.
    * 각 네트워크와 하드웨어의 특성을 숨기고, 어떤 종류의 컴퓨터나 네트워크든 서로 신뢰성 있는 의사소통을 하게 해준다.
* 일단 TCP 커넥션이 맺어지면, 클라이언트와 서버간 교환되는 메시지가 없어지거나, 손상되거나, 순서가 뒤바뀌어 수신되는 일은 결코 없음.
* HTTP 프로토콜은 TCP 위의 계층.
  * TCP 는 IP 위의 계층.

### 1.6.2 접속, IP주소, 그리고 포트번호

* 인터넷 프로토콜\(Internet Protocol, IP\) 주소와 포트번호를 사용해 클라이언트와 서버가 TCP 커넥션을 맺어야, HTTP 클라이언트가 서버에 메시지를 전송할 수 있음.
* HTTP 서버의 IP 주소, 포트번호는 URL을 이용해 알아낼 수 있음.
  * `[http://207.200.83.29:80/index.html](http://207.200.83.29:80/index.html)` - 이미 IP, 포트번호를 알고 있음.
  * `[http://www.netscape.com:80/index.html](http://www.netscape.com:80/index.html)` - 호스트명을 갖고 있음.
    * 호스트 명은 도메인 이름 서비스\(Domain Name Service, DNS\)를 통해 쉽게 IP로 변환됨.
  * `[http://www.netscape.com/index.html](http://www.netscape.com:80/index.html)` - port가 없음. 기본값 80으로 가정.
* 통신 순서
  * URL에서 호스트 명 추출
  * 호스트 명을 IP로 변환
  * 포트번호\(있다면\) 추출
  * 웹 서버와 TCP 커넥션을 맺음
  * 서버에 HTTP 요청 보냄
  * 서버는 HTTP 응답을 돌려줌
  * 커넥션이 닫히면, 웹브라우저는 문서를 보여줌

### 1.6.3 텔넷\(Telnet\)을 이용한 실제 예제

* telnet
  * 키보드를 목적지의 TCP 포트로 연결해주고, 출력 TCP 포트를 화면으로 연결해준다.
  * 원격 터미널 세션을 위해 흔히 사용됨.
  * HTTP 서버를 포함한 일반적인 TCP 서버에 연결하기 위해 사용될 수도 있음.
* `telnet [www.joes.hardware.com](http://www.joes.hardware.com) 80` 으로 통신 가능.
* `nc(netcat)` - HTTP를 포함한 UDP 혹은 TCP 기반의 트래픽 조작 가능.
  * [http://netcat.sourceforge.net/](http://netcat.sourceforge.net/)

## 1.7 프로토콜 버전

* `HTTP/0.9`
  * 1991년 HTTP 프로토타입.
  * 심각한 디자인 결함 존재.
  * 구식 클라이언트와만 사용.
  * GET만 지원.
  * MIME 타입, 헤더, 버전 번호 지원하지 않음.
  * 원래 간단한 HTML 객체를 받아오기 위해 만들어짐.
* `HTTP/1.0`
  * 처음으로 널리 쓰이기 시작한 HTTP 버전.
  * 헤더, 추가 메서드, 멀티미디어 객체 처리 추가.
  * 시각적으로 매력적인 웹페이지와 상호작용하는 폼을 실현.
  * 결코 잘 정의된 명세가 아님.
* `HTTP/1.0+`
  * 여러 유명 웹 클라이언트와 서버들이 HTTP에 기능을 추가함.
  * keep-alive 커넥션, 가상 호스팅 지원, 프락시 연결 지원.
  * 규격 외의 확장된 HTTP 버전.
* `HTTP/1.1`
  * HTTP 설계의 구조적 결함 교정, 두드러진 성능 최적화, 잘못된 기능 제거.
  * 더 복잡한 웹 애플리케이션, 배포 지원.
  * 현재 버전.
* `HTTP/2.0`
  * `HTTP/1.1`의 성능 문제를 개선하기 위해 구글의 SPDY 프로토콜을 기반으로 설계가 진행 중.

## 1.8 웹의 구성요소

* 프락시 - 클라이언트와 서버 사이에 위치한 HTTP 중개자
* 캐시 - 많이 찾는 웹페이지를 클라이언트 가까이에 보관하는 HTTP 창고
* 게이트웨이 - 다른 애플리케이션과 연결된 특별한 웹 서버
* 터널 - 단순히 HTTP통신을 전달하기만 하는 특별한 프락시
* 에이전트 - 자동화된 HTTP 요청을 만드는 준지능적 웹클라이언트

### 1.8.1 프락시

* 클라이언트와 서버 사이에 위치.
* 클라이언트의 모든 HTTP 요청을 받아 서버에 전달.
  * 대개 요청을 수정한 뒤 전달.
* 사용자를 대신해 서버에 접근.
* 주로 보안을 위해 사용됨.
  * 신뢰할 만한 중개자 역할.
* 요청과 응답 필터링.

### 1.8.2 캐시

* 웹 캐시, 캐시 프락시
  * 자신을 거쳐 가는 문서들 중 자주 찾는 것의 사본을 저장하는 특별한 종류의 HTTP 프락시 서버.
* 클라이언트가 같은 문서를 요청하면 그 캐시가 갖고 있는 사본을 받을 수 있음.
* 클라이언트는 웹 서버보다 근처의 캐시에서 훨씬 더 빨리 문서를 다운받을 수 있음.
* HTTP는 캐시를 효율적으로 동작하게 하고 캐시된 콘텐츠를 최신버전으로 유지하면서, 동시에 프라이버시도 보하기 위한 많은 기능을 정의함.

### 1.8.3 게이트웨이

* 다른 서버들의 중개자로 동작하는 특별한 서버.
* HTTP 트래픽을 다른 프로토콜로 변환하기 위해 사용.
* 스스로가 리소스를 갖고 있는 진짜 서버인 것처럼 요청을 다룸.
  * 클라이언트는 게이트웨이와 통신하고 있음을 알아채지 못함.
* `HTTP/FTP` 게이트웨이
  * FTP URI에 대한 HTTP 요청을 받아들인 뒤, FTP 프로토콜을 이용해 문서를 가져옴.
  * 받아온 문서는 HTTP 메시지에 담겨 클라이언트에게 보냄.

### 1.8.4 터널

* 두 커넥션 사이에서 날\(raw\) 데이터를 열어보지 않고 그대로 전달해주는 HTTP 애플리케이션.
  * 비 HTTP 데이터를 하나 이상의 HTTP 연결을 통해 그대로 전송해주기 위해 사용됨.
* 대표적인 예
  * 암호화된 SSL 트래픽을 HTTP 커넥션으로 전송함으로써 웹 트래픽만 허용하는 사내 방화벽을 통과시키는 것.

### 1.8.5 에이전트

* 사용자를 위해 HTTP 요청을 만들어주는 클라이언트 프로그램.
* 웹 요청을 만드는 애플리케이션은 뭐든 HTTP 에이전트.
* 자동화된 사용자 에이전트
  * 스파이더
  * 웹로봇

