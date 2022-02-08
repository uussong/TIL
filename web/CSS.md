# CSS

- Cascading Style Sheets

  - cascading 폭포처럼 흘러내리는
    - 상위요소에 정의되어있는 스타일이 하위요소들에도 그대로 전달
- 스타일을 지정하기 위한 언어

  - 어디에 꾸밀지 선택하고, 스타일을 지정한다.

```css
h1 {
    color: blue;
    font-size: 15px;
}

선택자(Selector) {
	속성(Property): 값(Value); 선언(Declaration)
}
```

- 속성과 값을 하나의 쌍으로 선언
- 세미클론으로 끝나야함 
  - 세미클론은 한 줄이 끝났다는 걸 알려주는 역할

- CSS 정의 방법

  - 인라인: 각각의 태그에 직접 style 속성 입력

  - 내부 참조: head 부분에 style 태그 안에 내용 적음

  - 외부 참조: 분리된 CSS 파일을 연결해 사용
    - 코드의 재사용성, 유지보수 쉬움
    - head에 `<link rel="stylesheet" href="경로">` 작성 

- CSS 정말 많은 속성을 가지고 있어 다 알 수 없음  
  - 주로 활용하는 것 위주로 기억하고 검색해서 쓰자
- CSS with 개발자 도구 
  - https://developer.chrome.com/docs/devtools/css/
  - 취소선: 상위요소에 의해 값이 바뀌었다는 것



### CSS Selectors

#### 기본 선택자

- 전체 선택자: *, 모든 요소를 선택하게 됨
- 요소 선택자: 태그명, 태그를 이용해서 선택
- 클래스 선택자: `.class_name`
  - HTML에 `<a class="class_name">`로 클래스를 줌
  - 여러 선택자에 같은 클래스를 주면 한 번에 여러 개를 선택 할 수 있음
- 아이디 선택자: `#id_name`
  - HTML에 `<a id="id_name">`로 아이디를 줌
  - 일반적으로 하나의 문서에 하나의 id 이름이 존재하는 것이 정석
  - 요소가 한 번만 정의되어야 가져오기 편함
  - 여러 개 id 선택자를 주면 의미가 퇴색되나 여러 개가 사용되기도
- 속성 선택자 ex. `button[type]`
  -  어떠한 속성을 갖고 있는지를 기준으로 선택, 다양한 속성 선택자 존재 잘 사용 안 함

- 기본 선택자만 가지고는 요소 하나에다만 스타일 속성을 주기 어려움

#### 결합자

- 요소들을 몇 개를 묶어 그 조건을 만족하는 요소를 선택
- 자손 결합자
  - `A B`: A를 만족하는 모든 하위 요소 중에서 B를 만족하는 모든 요소를 선택함
- 자식 결합자
  - `A > B`: A의 자식 중에서 B를 만족하는 요소만 선택
- 일반 형제 결합자
  - `A ~ B`: A의 형제 요소 중에서 B를 만족하는 요소만 선택
- 인접 형제 결합자
  - `A + B`: A의 모든 형제 요소 중에서 바로 다음에 오는 B만 선택

#### 의사 클래스(Pseudo Class) (가상 클래스)

- 선택하고자하는 HTML요소의 특별한 상태를 찍고 싶은 것
- `선택자:` 뒤에 의사 클래스가 옴 
  - 어떤 상태일 때 이 스타일로 변경할 건지 명시
- 특정한 상태를 만족하는 요소를 선택할 때 
  - `:hover :focus :checked :first-child :nth-child(n) :last-child` 등
- 동적 의사 클래스
  - `:link`: 사용자가 아직 한 번도 해당 링크를 누르지 않은 상태 
    - `<a>` 기본
  - `:visited`: 사용자가 한 번이라도 해당 링크를 누른 상태
  - `:hover`: 사용자의 마우스 커서가 위에 올라가 있는 상태
  - `:active`: 사용자의 마우스 커서가 클릭중인 상태
  - `:focus`: tab키로 focus가 맞춰진 상태
- 상태 의사 클래스
  - `:checked`: input의 checkbox나 raidobutton이 체크된 상태
  - `:enabled`: input의 "type=text", select, option에서 사용자가 선택한 상태
  - `:disabled`: input의 "type=text", select, option을 사용자가 선택할 수 없도록 만든 상태
- 구조 의사 클래스
  - `:first-child`: 모든 자식 요소 중에서 첫 번째에 위치하는 자식을 선택
  - `:nth-child(n)`: 모든 자식 요소 중에서 n번째에 위치하는 자식을 선택
  - `:last-child`: 모든 자식 요소 중에서 마지막에 위치하는 자식을 선택
  - `:first-of-type`: 모든 자식 요소 중에서 첫 번째에 등장하는 특정 요소를 선택
  - `:nth-of-type(n)`: 모든 자식 요소 중에서 n번째로 등장하는 특정 요소를 선택
  - `:last-of-type`: 모든 자식 요소 중에서 마지막으로 등장하는 특정 요소를 선택

#### 의사 요소 (가상 요소)

- 딱 특정 부분만 선택할 때 사용
- `::first-letter`: 요소의 텍스트에서 첫 번째 글자에 스타일을 적용
  - 블록타입의 요소에만 사용 가능

- `::first-line`: 요소의 텍스트에서 첫 줄에 스타일을 적용 블록타입의 요소에만 사용 가능
- `::before`: 요소의 콘텐츠 시작부분에 생성된 콘텐츠를 추가
- `::after`: 요소의 콘텐츠 끝부분에 생성된 콘텐츠를 추가

#### CSS 적용 우선순위

- **우선순위**
  - **인라인 > id > class**, 속성, pseudo-class **> 요소**, pseudo-element
- 중요도
  - `!important`
  - 우선 순위 다 무시
  - 뒤에서 요소를 바꾸려면 !important를 또 써줘야하기 때문에 복잡해질 수 있어 쓰지 않는 편이 좋음
- CSS 파일 로딩 순서
  - 같은 우선순위가 정의되어있을 땐 가장 마지막에 정의된 걸 따름

#### CSS 상속

- 부모에 있는 CSS요소가 자동으로 아래로 내려옴 cascading 
  - 상위 요소에 적용된 property를 하위요소가 물려받는 것

- 상위요소에 지정된 스타일이 없다면 각각 모든 요소에 css를 지정해주면 됨
- 속성 중에는 상속 되는 것과 되지 않는 것들이 있음
  - 상속 되는 것: Text 관련 요소, opacity, visibility 등
  - 상속 되지 않는 것: Box model 관련 요소(width, height, margin, padding, border, box-sizing, display), position 관련 요소(position, top/right/bottom/left, z-index) 등
    - inherit이라는 키워드를 써주면 명시적으로 상속을 시켜버릴 수 있음



### CSS 기본 스타일

#### 크기 단위

- 고정 크기 단위
  - 부모 요소 기타 다른 영향을 받지 않고 항상 일정한 크기를 나타냄
- 가변 크기 단위 
  - 디바이스, 부모 등 상황에 따라 크기가 가변적으로 바뀌는 단위
  - 반응형이 대세가 되며 가변 크기 단위를 많이 씀
- px(픽셀) 모니터의 한 화소
  - 픽셀의 크기가 변하지 않기 때문에 고정적
- in (inch) 고정크기단위라고는 하나 운영체제마다 달라짐, dpi가 달라지기 때문
  - 화면의 논리적인 길이단위
- pt 1pt = 1/72 in
- %
  - 가변적인 레이아웃에서 사용
- **em**
  - 부모 요소(바로 위에 있는 상위요소) 크기에 대한 배수단위
  - 상대적인 크기를 지니는 단위
  - 1em = 100%, 1.5em = 150%
- **rem**
  - root + em
  - 최상위 요소(HTML)에 정의되어 있는 사이즈를 기준으로 배수단위를 가짐
    - 기본적으로 root는 16px
  - 상대적인 크기를 지니는 단위
- viewport
  - 유저가 실제로 보고 있는 화면(디바이스 화면), 유저에게 바로 보이게 되는 웹 컨텐츠 영역
    - mobile device로 보고 있다면 작아짐
  - 디바이스의 viewport를 기준으로 상대적인 사이즈 결정
    - vw, vh, vmin, vmax
    - width 1/100 = 1vw, height 1/100 = 1vh
      - 100vw 화면 너비 꽉 차게, 100vh 화면 세로 꽉 차게
        - width 900px일때 1vw = 9px
    - 크기가 줄어들고 커질 때 최소/최대크기 줄 수 있음
      - 100vmin(최소 크기가 100) = 항상 디바이스 크기

#### 색상단위

- 색상 키워드
  - red, blue, black 등 직접 색상을 명시
- RGB 색상
  - #000000
  - rgb(0, 0, 0)
  - rgba(0, 0, 0, 1) 
    - a는 alpha(투명도)
- HSL 색상
  - 거의 쓰지 않음


#### CSS 문서 표현

- 텍스트, 컬러, 배경, 태그별 스타일링 등 필요할 때마다 찾아서 공부해 쓰면 됨



### CSS Box model

#### CSS 원칙

- 모든 요소는 네모(박스모델)이고 위에서부터 아래로, 왼쪽에서 오른쪽으로 쌓임
- 모든요소 즉, 박스들이 왼쪽 상단에 붙으려는 성질 = Normal Flow 
  - 모든 css는 박스 요소로 동작하며 모든 요소는 이런 식으로 배치 되려고 함 

#### Box model

- content
  - 글이나 이미지 등 요소의 실제 내용
- padding
  - content와 border 사이의 거리(간격), 테두리 안쪽 내부 여백 
  - 컨텐츠에 적용된 배경, 이미지가 패딩까지 적용됨
- border
  - 테두리
- margin:
  - 테두리 바깥 쪽의 여백
    - 요소와 요소 사이의 거리, 다른 요소와의 거리
- margin / padding
  - 값을 한 번만 주면 상하좌우 네 면에 모두 적용
  - 두 개는 상하/좌우로 적용
  - 세 개는 상/좌우/하로 적용
  - 네 개는 시계 방향 상/하/좌/우로 적용
- border 
  - 두께 스타일 색상 따로따로 값 안 주고 한 줄로 줄여쓸 수 있음
    - 순서 상관x
    - solid 실선 dashed 점선

#### box-sizing:

- 박스의 크기를 계산할 때 어떤것을 기준으로 할 건지 정하는 것
- content-box : content 기준
  - 기본적으로 우리가 주는 width는 컨텐츠 영역
- border-box : border 기준
  - 우리 눈에 보이는 건 테두리에 맞게 설정하기 위해선 border-box로 설정
  - content+padding+border 까지 모두 합쳐 width와 height 맞춰줌



### CSS Display

- 모든 요소는 네모 박스 모델이고, 좌측상단에 배치되려 함: Normal flow
- display에 따라 크기와 배치가 달라짐
  - 박스를 어떻게 쌓을 것인가
- display: block

  - block의 기본 너비는 가질 수 있는 너비(화면 너비)의 100%
  - 나머지 요소는 전부 오른쪽을 margin으로 채움 
    - 결국 화면 전체를 차지 다음 요소는 개행 즉 자동으로 줄바꿈이 일어남
  - 블록 레벨 요소 안에 인라인 레벨 요소가 들어갈 수 있음
  - `<div>` `<p>` `<form>` 등
- display: inline

  - 줄 바꿈이 일어나지 않은 행의 일부 요소
  - inline의 기본 너비는 컨텐츠의 영역만큼 차지
  - width, height (margin-top, margin-bottom) 지정할 수 없음
  - 일반적으로 text 생각하면 됨
  - block 외 나머지 `<span>` `<a>` `<input>` `<img>`등
    - `<img>`는 기본적으로 inline이나 widht, height를 지정할 수 있음
    - `<img>`에 기본적으로 있는 사이 간격을 줄이기 위해 `display:block` 값을 줌
- 속성에 따른 수평 정렬
  - block / inline 속성
    - 왼쪽 정렬: `margin-right: auto;` / `text-align: left;`
    - 오른쪽 정렬: `margin-left: auto;`  /`text-align: right;` 
    - 가운데 정렬: `margin-right: auto;`  / `margin-left: auto;` 
- 수직 정렬의 경우
  - 기본으로 위로 붙는 형태다 보니 auto를 줘도 배분할 것이 없음
  - `margin-top` 또는 `margin-bottom`이 `auto`면 실제로 갖는 값은 0 
- display: inline-block
  - block과 inline 레벨 요소 특징 모두 가짐
  - block 요소를 자리 잡고 나머지를 inline요소들로 채울 때 사용
  - 하나의 라인에 block과 다른 요소를 같이 쓸 수 있음
  - block요소와 같이 width, height, margin 속성 모두 지정 가능
- display: none
  - 해당 요소를 화면에 표시하지 않고 공간조차 부여하지 않음
  - **visibility: hidden와 차이** 
    - 해당 요소가 공간은 차지하지만 화면에 표시되지 않음



## CSS Position

- 요소를 어떻게 두는가 위치 지정
- static: 모든 태그, 포지션의 기본값
  - 일반적인 요소의 배치 순서(Normal flow)를 따름
    - 좌측 상단에 붙으려는 성질
  - 부모 요소 내에서 배치될때는 부모 요소의 위치를 기준으로 배치
- 일반적인 배치순서를 벗어날 수 있게 해주는 값
  - relative, absolute, fixed
  - 좌표 프로퍼티top, bottom, left, right를 사용해 움직임 
    - 좌측상단 기준
- relative: 상대 위치
  - Normal flow를 따랐을 때 자기 자신이 있어야 할 위치(static)를 기준으로 이동
    - Normal flow 유지
    - 원래 위치에 있고 자리만 옮겨져 있는 것
  - 요소가 차지하는 공간은 static 때와 같음
- absolute: 절대 위치
  - 절대 위치(특정 위치)에 갖다 붙임
    - 스크롤 해도 해당 위치에 고정
  - 가장 가까이의 부모, 조상 요소를 기준으로 이동
  - static position을 지정하지 않은 상태에서 absolute는 static이 아닌 가까이 있는 부모요소를 기준으로 하기 때문에 기준으로 삼고 싶은 박스에 relative 값을 줘야함
  - Normal flow에서 제거되어 공중에 떠있는 상태가 됨
    - 일반적인 흐름에서 벗어나 다른 차원에서 움직임, 겹칠 수 있음
    - 원래 위치에서 완전히 나가 그 공간을 밑에 있는 요소가 채움
- relative와 absolute는 상황에 따라 혼용해 쓸 수 있으나 앞에서 어떤 속성을 주었냐에 따라 뒤의 결과는 달라짐
- fixed: 고정 위치
  - viewport를 기준으로 해 항상 그 위치에 위치하게 하는 것
    - 스크롤 시에도 항상 같은 위치로 따라옴
  - Normal flow에서 제거되어 공중에 떠있는 상태가 됨
    - 일반적인 흐름에서 벗어나 다른 차원에서 움직임

#### CSS 원칙

- Normal flow
  - 박스모델 좌측상단 배치
  - display 따라 배치 달라짐
- position으로 normal flow 안따르고 위치 기준을 바꿀 수 있음
  - relative 자리 차지함 원래 위치 기준으로 움직임
  - absolute 자리 차지 않음 붕뜬다고 생각 특정 부모(static이 아닌 부모) 위치 기준으로 움직임
  - fixed 자리 차지 않음 붕뜬다고 생각 화면(브라우저(viewport)) 위치 기준으로 움직임



### Emmet

- `>`  태그를 만들고 들여쓰기
- `*n` 반복
- `+` 줄바꿈 + 다음 태그 추가
- `.` class 지정
- `#` id 지정
- `{content}` 내용 입력
- https://docs.emmet.io/cheat-sheet/



## CSS Layout

### Float 

- 박스를 왼쪽, 오른쪽으로 이동시켜 인라인요소들이 주변을 wrapping 하도록 함

- 블럭 요소를 인라인 요소로 감고 싶을 때 사용

  - 뉴스 레이아웃

- Normal flow를 벗어나도록 함

  - 둥둥 떠 있는 모습 옆으로 내용이 채워짐

- 속성

  - none: 기본값
  - left: 요소를 왼쪽으로 띄움
  - right: 요소를 오른쪽으로 띄움

- Clearing float

  - float값을 주었을 때 뒤의 요소가 따라오는 것을 방지
    - float를 사용했을 때 다음 요소들의 정렬 요소를 지워주기 위함
    - clear를 적용하는 요소부터 float로 인한 정렬 요소를 없앰

  - float 요소의 부모로 div를 만들고 부모 요소에게 일반적인 이름으로 .clearfix 부여

  ```css
  .clearfix::after {
      content: "";
      display: block;
      clear: both; 
  }
  ```

  - clearing을 하는 이유
    - float의 부모 요소는 높이가 0
      - css의 높이는 자식의 높이만큼 가져가게 되어있음 자식이 float되어 normal flow에서 벗어났기 때문에 부모의 높이도 0이됨
    - 뒤의 요소가 자연스럽게 공간을 채우게 되는데 이를 방지하기 위해서 부모가 자식의 높이를 가져가게 하기 위해 clearing 함
      - 그 이후에 float의 영향이 가지 않도록 함
  - inline에 float 적용하면 block으로 지정됨
  - float가 텍스트가 인라인 요소 감싸는 형태다 보니 text는 밀리게 됨
  - 개별적으로 `clear: left/right;` 등을 줄 수도 있음


### Flexbox

- 내부 영역 안에서의 배치 가능해짐 
  - 수평구조 가능해짐
- 축
  - 메인 축 main axis
  - 교차 축 cross axis
- flexbox 구성 요소
  - flex container
    - 수평이 될 요소가 들어간 컨테이너에 `display: flex;` 값을 줌
      - 개발자 도구에 flex 라 뜸
    - `display: flex`:  컨테이너가 block 방식으로 쌓임
    - `display: flex-inline`: 컨테이너가 inline 방식으로 쌓임
  - flex item
- 왜 flexbox를 사용해야 하나?
  - 수직 정렬 수동값 부여 없이 가능
  - 아이템 너비와 높이 혹은 간격을 동일하게 알아서 배치해줌

#### container에 들어갈 수 있는 것

- `display`: Flex Container를 정의

  - flex, flex-inline: 컨테이너가 쌓이는 방식 block/inline

- `flex-direction`: item들의 주 축(main-axis) 설정

  - 아이템들이 어떻게 정렬을 할 건지, 하나의 컨테이너 박스에서 아이템들의 main축을 어떻게 잡을 건지 설정
  - row, row-reverse, column, column-reverse

- `flex-wrap`: item들의 줄 바꿈 설정

  - 아이템들의 여러줄 묶음을 설정하는 속성
  - 아이템들이 브라우저 창이 줄어들었을 때 줄 바꿈을 어떻게 만들어줄건지 설정
  - nowrap: 아이템들을 묶지 않음 즉 한 줄로 모든 아이템을 표시하겠다 크기에 따라서 아이템 줄어들게 됨. default
  - wrap: 아이템을 여러줄로 묶어서 표시. 브라우저 크기가 줄어들 때 여러줄이 됨 아이템을 여러줄로 표시하겠다. 브라우저 크기에 따라 줄 바꿈을 하겠다.
  - wrap-reverse: 아래부터 쌓임 끝까지 펼치면 순서대로인데 아이템 내려가는 거가 앞에서부터 내려감

- `flex-flow`: `flex-direction` 과 `flex-wrap` 을 줄여서 쓸 수 있음

  - `flex-flow: flex-direction flex-wrap`

- **`justify-content`**: 주 축(main-axis)의 정렬  방법 설정

  - flexbox 주 축의 아이템들이 어떻게 정렬될 것인가
  - flex-start, flex-end, center
    - 정렬 기준(주축 방향)에 따라 container 왼쪽이 start 오른쪽이 end
      - reverse되면 start, end도 바뀜
    - 왼쪽 정렬, 오른쪽 정렬, 중앙 정렬
  - space-between: 아이템들 중 가장 첫 번째를 둘 수 있는 가장 왼쪽에 두고 아이템 마지막을 둘 수 있는 가장 오른쪽에 둔 다음에 나머지 아이템들은 간격이 일정하게 둠
    - 첫번째와 마지막 바깥은 간격 일정하지 않음
  - space-around: 아이템들의 여백을 균등한 여백으로 만들어서 정렬하는 것
  - space-evenly: 모든 여백을 균등한 여백으로 만들어서 정렬

- `align-content`: 교차 축(cross-axis)의 정렬 방법 설정 (2줄 이상)

  - 아이템 여러 줄일 때 사용
  - flex-wrap: nowrap(default값)이면 align-content의미 없어짐
  - 교차축을 기준으로 함

  - stretch, flex-start, flex-end, center, space-between, space-around
    - stretch: 교차 축을 꽉 채우기 위해 아이템을 늘림 default
    - center: 컨테이너 높이의 가운데, 수직 정렬

- `align-items`: 교차 축(cross-axis)의 정렬 방법 설정 (1줄) 
  - 아이템 한 줄일 때 사용
  - stretch, flex-start, flex-end, center, space-between, space-around, baseline
    - **baseline**: 아이템들 안에 글자의 문자 기준선에 맞춰서 정렬 
      - 문자의 크기가 다르면 박스의 크기도 달라짐 

#### Flex Item을 위한 속성들

- 각각의 아이템들에 주는 속성들

- `order`: Item의 순서를 설정

  - 개별 아이템의 우선순위를 정해주는 것 
  - 기본값 0, 음수도 가능 
    - 모든 요소 각각이 다 기본값이 0이기 때문에 하나의 요소에만 order:5를 줬다면 다섯번째 자리로 가는 것 아니라 맨 마지막으로 가게 됨
  - 숫자 클수록 flex-end쪽에 가까워짐

- `flex`:  `flex-grow` , `flex-shrink` , `flex-basis` 에 대한 단축 속성

  - flex를 쓸거라면 flex-grow 필수(생략 불가) 뒤의 값은 default값이 들어가 생략 가능

  - `flex-grow`: Item의 너비 증가(grow) 비율 설정

    - 커질때 비율
      - 늘릴 때 얼만큼 늘어나는 지
    - 기본값 1
    - 각각의 아이템이 너비 증가할 수 있는 상태여야 너비 옵션을 준 것이 의미가 있음
      - flex-wrap: nowrap이 아니면 의미가 없음

    ```html
    <body>
      <div class="container">
        <div class="box" id="box1">1</div>
        <div class="box" id="box2">2</div>
        <div class="box" id="box3">3</div>
      </div>
    ```

    ```css
    .container{
      display: flex
    }
    
    #box1 {
      flex-grow: 1;
    }
    
    #box2 {
      flex-grow: 2;
    }
    
    #box3 {
      flex-grow: 1;
    }
    ```

    - grow값을 1, 2, 1 로 주면 1:2:1 즉 25% 50% 25% 로 늘어남

      

  - `flex-shrink`: Item의 너비 감소(shrink) 비율 설정

    - 작아질때 비율 
      - 줄일 때 얼마만큼 줄어들건가
    - 기본값 1
    - 아이템이 줄어들 수 없는 상태면 의미가 없다
    - viewport가 줄어들다가 아이템의 너비의 영향을 미치는 시점부터 얼마만큼 viewport크기를 줄였는가를 기준으로 줄어듦 

  - `flex-basis`: Item의 기본 너비 설정
    - inline요소에도 줄 수 있음
    - 기본값 auto
    - 단축 속성 사용할 때 flex-basis를 생략하게 되면 auto아닌 0이 들어감 주의

- `align-self`: 교차축을 기준으로 Item을 정렬하는 방법을 설정

  - align-items: container 안에 모든 item들의 교차축으로 한 정렬 방법 설정
  - align-self: 개별 아이템, align-item보다 우선순위 높음
  - stretch, flex-start, flex-end, center, space-between, space-around, baseline
  - default 값 auto



