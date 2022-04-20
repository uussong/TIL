# REST API

## HTTP

- HyperText Transfer Protocol
- 웹에서 이루어지는 모든 데이터 교환의 기초
- HTTP 객체가 요청과 응답을 통해 왔다갔다하는데 그 안에는 여러 데이터 정보가 들어있음
- 기본특성
  - Stateless 무상태 
  - Connectionless 비연결성
- 쿠키와 세션을 통해 서버 상태를 요청과 연결하도록 함

### HTTP 메세지

- Status code가 점점 중요해질 것

### HTTP request methods

- 우리가 어딘가 요청을 보냈을 때 결국 원하는 동작이 무엇이냐
- 같은 주소로 요청을 보내더라도 메서드에 따라 우리가 원하는 행동이 달라짐
  - GET 조회 POST 작성, 수정, 삭제
    - POST 요청 나눌 것! -> POST 작성 PUT 수정 DELETE 삭제 
  - RESTful API와 연결
    - url에는 뭘 하겠다는 액션이 없음 그저 자원을 표현하는 단계
    - post/1/을 GET / POST 할 때 동작이 달라질 것

### HTTP response status codes

- 특정 HTTP 요청이 성공적으로 완료되었는지 여부를 나타냄
- 회사 내부적으로 백엔드 개발자와 클라이언트 개발자가 약속하는 것
- 응답은 5개의 그룹으로 나누어짐 (2, 4, 5알아둘 것) [공식문서](https://developer.mozilla.org/ko/docs/Web/HTTP/Status)
  - Infomational responses (1xx)
    - 일반적인 기업에서 많이 쓰지 않음
  - Successful responses (2xx)
    - 정상
    - 200 OK 정상적 처리 / 201 Created 새로운 데이터 생성 
  - Redirection responses (3xx)
  - Client error responses (4xx)
    - 웹 브라우저에서 문제 발생
    - 400, 401 로그인 할 때 인증된 유저가 아닐 경우, 403 Forbidden
    - 404 Not Found 리소스를 찾을 수 없음, url 잘 못 입력, 요청을 잘 못 한 경우
  - Server error responses (5xx)
    - 백엔드에서 문제 발생 
    - 500 Internal Server Error 서버 안 쪽에서 로직 처리하다가 문제 발생, 503

### 웹에서의 리소스 식별

- 리소스(resource, 자원): HTTP 요청의 대상
  - 문서, 사진 또는 기타 어떤 것이든 될 수 있음
- 각 리소스는 리소스 식별을 위해 HTTP 전체에서 사용되는 URI로 식별됨

### URL, URN

- 인터넷 상에서 정보를 어떻게 표현할 것인가.
- URL(Uniform Resource Locator)
  - 가장 일반적으로 사용
- URN(Uniform Resource Name)
  - URL과 달리 자원의 위치에 영향을 받지 않는 유일한/고유한 이름 역할

### URI

- Uniform Resource Identifier
- 인터넷의 자원을 식별하는 유일한 주소(정보의 자원을 표현)
- 하위 개념이 URL, URN
- URN을 사용하는 비중이 매우 적기 때문에 일반적으로 URL은 URI와 같은 의미 처럼 사용
- **구조**
  - Scheme(protocol) 
    - http(s)
  - Host (Domain name)
    - 요청 받는 웹 서버 이름
    - IP address를 사람이 사용하기엔 부적합해 주소로 갈 수 있는 이름을 붙여놓는 것
    - 배포할 때 나만의 도메인 주소를 구매하기도 함
  - Port
    - 웹 서버 상의 리소스에 접근하는데 사용되는 기술적인 문
    - 일반적으로 출력되지 않으며 로컬 서버에서 진행될 때 로컬 서버가 출력됨
    - HTTP 프로토콜의 표준 포트
      - HTTP 80 HTTPS 443
  - Path
    - 웹 서버 상의 자원의 경로
    - 실제 위치가 아닌 추상적인 형태로 표현됨
  - Query (Identifier)
    - Query String Parameters
    - 웹 서버에 제공되는 추가적인 매개 변수
    - &로 구분되는 key-value 목록
      - GET요청 시 확인 가능
      - 웹 서버에 검색할 경우 확인 가능
  - Frangment
    - #뒤로 오는 부분
    - 특정 자원 안에서의 북마크 역할
    - HTML안의 특정 지점을 공유할 때 나타남
    - #뒤의 부분 요청은 서버에 보내지지 않으며 Fragment를 해석하는 것은 브라우저임



## RESTful API

### API

- Application Programming Interface
- 애플리케이션과 프로그래밍으로 소통하는 방법
  - CLI 명령어, GUI 그래픽(아이콘) 클릭, API 프로그래밍 요청을 통해
- 어떤 서비스를 이용하기 위해 데이터를 어떻게 요청하고 어떤 데이터를 내려줄 지 짜는 것
- 응답 데이터 타입 
  - JSON (HTML, XML)
- Web API
  - (장고처럼)웹 애플리케이션 개발에서 다른 서비스에 요청을 보내고 응답을 받기 위해 정의된 명세
  - Open API 활용 -> 거의 모든 사이트에서 제공
    - Youtube, 카카오톡, 네이버 웹툰, 디스코드, TMDB 등

### REST

- REpresentational State Transfer
- API 서버를 개발하기 위한 일종의 소프트웨어 설계 방법론
  - 규약, 약속이 아님 반드시 이런 방식으로 설계해야 하는 것 아님 다양한 방법론 중 하나
- 네트워크 구조를 설정하는 원리를 정리한 것
  - 넷 상에서 자원을 정의하고 자원에 대한 주소를 지정하는 전반적인 방법
  - URI를 어떤 구조로 정리할 것인가
- REST 원리를 따르는 시스템을 RESTful 이란 용어로 지칭
- 자원을 정의하는 방법에 대한 고민
- REST 자원과 주소의 지정 방법
  - 자원: URI
  - 행위: HTTP Method
  - 표현 
    - 자원과 행위를 통해 궁극적으로 표현되는 결과물(데이터)
    - JSON으로 표현된 데이터 제공
- REST의 핵심 규칙
  - '정보'는 URI로 표현
  - 자원에 대한 '행위'는 HTTP Method로 표현 (R: GET, C: POST, U: PUT, D: DELETE)
- 설계 방법론을 지키지 않더라도 동작 여부에 영향을 미치지 않으나 실제 개발 환경에서 모두 사용하므로 지켜야만 함

### JSON

- JavaScript Object Notation
- 가벼운 데이터 통신 포맷
- JavaScript의 객체 표기법을 따르는 단순 문자열
- 사람이 읽거나 쓰기 쉽고 기계가 파싱(해석, 분석)하고 만들어내기 쉬움
- key-value의 데이터 쌍이 여러 개 있는 구조 
  - 프로그래밍 언어에서 기본적으로 지원하는 구조

### RESTful API

- REST 원리에 따라 설계한 API
- REST API와 같은 말
- 프로그램을 통해 해당되는 클라이언트에 대한 요청에 JSON을 응답하는 서버를 구성
- 오늘 사용하는 장고 서버가 REST API 서버가 되는 것



