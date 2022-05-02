# axios를 이용한 비동기 통신 개념

## AJAX

- Asynchoronous JavaScript And XML (비동기식 JavaScript와 XML)
- XML, JSON는 결국 데이터를 표현하는 방식
- 객체, 딕셔너리 등등 한 줄의 레코드를 표현하기 가장 좋은 자료구조
- JSON은 이를 배열 혹은 리스트 자료형으로 묶는 방식
- XML은 HTML의 데이터 표현 방식과 유사
  - eXtended Markup Language
  - 정해진 태그만 쓰는 거 아닌 원하는 대로 확장해서 사용
- JSON이 XML보다 더 선호되는 이유
  - 전송해야하는 데이터 양이 더 많음 데이터를 주고 받을 때 JSON이 더 빠름

### AJAX 특징

- 페이지 전체를 새로고침 하지 않고서도 수행되는 **비동기성**
  - 서버의 응답에 따라 전체 페이지가 아닌 일부분만을 업데이트 할 수 있음
- AJAX의 비동기성으로 아래의 작업이 가능
  - 페이지 새로 고침 없이 서버에 요청
  - 서버로부터 데이터를 받고 해당 작업 수행
- ex 연관검색어 AJAX로 구글 서버에서 받아오는 것
  - 입력했을 때 무엇을 하겠다 = 외부에서 코드를 가져오겠다
  - console 옆에 톱니바퀴 누르고 Log XMLHttpRequests 로 확인가능
- ex 지도 마치 전세계 맵데이터를 들고 있는 것 처럼 쓸 수 있게 해주는 건 뒤에 구글서버가 열일하는 것 줌 땡기고 옮길 때마다 서버에서 요청-응답
- 마우스 휠을 돌리는 것도 서버에 요청을 보내는 것 누르면 그냥 탭이 나오는 거 같지만 이 데이터는 서버에서 가져오는 것 전체 페이지 새로고침 아니라 웹페이지 한 부분에서만 서버로부터 데이터 가져와 변경되는 것
- 모던앱의 핵심
- 기술이라기 보단 접근법

### XMLHttpRequest 객체

- XMLHttpRequest -> XHR
- 이름과 달리 모든 종류의 데이터를 받아올 수 있음
- `XMLHttpRequest()` 객체를 생성하는 함수
- 요즘에는 라이브러리 사용



## Asynchoronous JavaScript

### 동기식

- 순차적, 직렬적 task 수행
  - 앞에 줄이 끝나야 뒤에 줄이 실행
- 일반적인 코드 흐름은 동기식 - 너무 당연한 것!
- 요청을 보낸 후 응답을 받아야만 다음 동작이 이루어짐(blocking)

### 비동기식

- 병렬적 task 수행
  - 무언가 일이 시작됐는데 그걸 끝날 때 까지 기다리지 않고 다른 일 시작될 수 있는 것
  - 일이 동시에 일어날 수 있음
- 요청을 보낸 후 해당 task가 끝날 때 까지 기다리지 않고 다음 동작 실행 (non-blocking)

```javascript
const request = new XMLHttpRequest()
const URL = 'https://jsonplaceholder.typicode.com/todos/1/'

reqeust.open('GET', URL)
request.send() // XMLHttpRequest 요청

const todo = request.response // 빈 응답 값을 todo에 할당
console.log(`data: ${todo}`) 
```

- 응답이 올 때까지 기다리지 않고 다음 코드로 넘어감
- 아직 응답이 없없기 때문에 변수에 빈값이 할당되어 결과적으로 빈 문자열이 출력
- `request.send()` 이전 코드까진 동기식이나 요청을 보낸 후 응답을 기다리지 않고 다음 코드 실행
- 왜 이러한 방식으로 동작하는가? 자바스크립트의 thread 이용 방식이 single thread이기 때문
  - JavaScript은 single threaded

### Threads

- 각 thread는 한 번에 하나의 작업을 수행할 수 있음
  - 하나의 탭에 하나의 일꾼이 배정
- 여러 개의 작업이 들어오면 작업 1을 처리한 뒤 작업 2를 처리해야함 무조건 순차적으로 처리

### 왜  비동기를 사용하는가?

- 왜 웹에서는 비동기를 중요하게 생각하는가 이유는 딱 하나 **사용자 경험**(UX)
- 비동기로 사용하지 않으면(동기식 코드라면) 데이터가 다 로드될 때까지 일이 진행되지 않을 것
  - 동기식 코드 데이터 모두 불러온 뒤에 앱이 실행되거나 웹 페이지가 보여지게 됨
  - 멈춘 것 처럼 보인다면 사용자가 사용하지 않을 것
- 비동기식 코드라면 데이터를 요청하고 응답 받는 동안 앱 실행을 함께 진행
  - 요청을 쫙 보낸 다음 서버로부터 응답이 온 순서대로 화면에 뿌려줌
  - 데이터를 불러오는 동안 지속적으로 응답하는 화면을 보여줌으로써 더욱 쾌적한 사용자 경험 제공
- 많은 웹 API 기능은 비동기 코드를 사용해 실행됨
- 파이썬 코드 끝날 때가지 다음으로 넘어갈 수 없음
- js 기본적으로 끝날 때까지 기다리나 send는 기다리지 않음 넘어감 몇몇 함수, 메소드만 이렇게 동작

### JavaScript = single threaded

- 단일 스레드에서만 작업을 수행 즉 이벤트를 처리하는 Call Stack이 하나인 언어
- 따라서 자바스크립트는 효과적으로 동작하기 위해 다음의 과정을 수행
  - 즉시 처리하지 못 하는 이벤트들을 Web API(브라우저 내부)으로 보내 처리
  - 처리된 이벤트들은 처리된 순서대로 Task queue에 줄을 세움
  - Call Stack이 비면 Event Loop가 Task queue에서 가장 오래된(제일 앞) 이벤트를 Call Stack에 보냄

### Concurrency model

- Event loop을 기반으로 하는 동시성 모델(Concurrency model)

#### Call stack

- 요청이 들어올 때마다 해당 요청을 순차적으로 처리하는 스택 형태 자료구조

#### Web API

- JavaScript 엔진이 아닌 브라우저 영역에서 제공하는 API, 브라우저 API
- AJAX 요청, 시간 관련된 것들(`setTimeout()`등) 시간이 소요되는 일을 처리
  - 언제 응답올 지 모름, 언제 끝날지 모른다는 공통점
  - `setTimeout(콜백함수, 시간)` milesecond
- 비동기 동작을 하는 원인

#### Task queue

- 비동기 처리된 callback함수가 대기하는 큐 형태의 자료구조
- Call stack이 빌 때까지 Task queue에 남아있음
- Callback 함수에서 Task queue에 가는 경우 우선순위가 밀리게 됨 Call stack에 있는 것이 우선

#### Event loop

- 자동 감시자
- Call Stack이 비어있는지 확인
- 비어있는 경우 Task queue에서 실행 대기 중인 callback 함수가 있는지 확인
- Task queue에 대기 중인 callback 함수가 있다면 가장 앞에 있는 callback 함수를 Call Stack으로 push

### 순차적인 비동기 처리하기

- Web API로 들어오는 순서는 중요하지 않고 어떤 이벤트가 먼저 처리되느냐가 중요
  - 실행 순서 불명확
- 순차적인 비동기 처리를 위한 2가지 작성 방식
  - Async callbacks
  - promise-style



