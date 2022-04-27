# JavaScript 기초

## JavaScript Intro

- 자바스크립트는 브라우저를 동적으로 움직이게 하기 위해 필요
- 브라우저를 조작할 수 있는 유일한 언어
  - 브라우저가 이해할 수 있는 프로그래밍 언어는 자바스크립트 뿐
  - HTML, CSS는 프로그래밍 언어가 아님

### 브라우저

- 웹 브라우저
- 웹 문서를 받아서 우리 화면에 보여주는 역할
- URL입력하면 웹 탐색해 서버와 통신하는 걸 자동으로 해줌
- 서버에서 조작을 하면 결국엔 웹문서를 주게 된다. 그럼 이것을 브라우저가 받는다. 웹문서를 브라우저가 받아서 화면에 보여주게 됨

## Browser

- DOM(Document Object Model) 조작
  - 문서 객체 모델
  - head와 body로 이루어져있고 등등 각각을 DOM 즉 문서 객체, 각각을 객체로 봐서 소스 코드 자체를 트리 구조로 나타낸 것이 DOM
- BOM
  - 브라우저를 이 구조로 나눈 것
  - 거의 조작하지 않음
- 트리구조로 나타내면 계층 구조가 명확해져 요소에 바로 접근할 수 있게 됨
- DOM해석을 브라우저가 해줌 이러한 과정을 파싱이라고 함
  - 웹 문서를 구문 분석해서 DOM Tree로 만드는 과정
  - 브라우저마다 분석하는 엔진이 달라 속도 차이가 나는 것
    - 크롬 V8엔진, 굉장히 빠름 -> 이걸 개발할 때 쓸 수 없나..? Node.js
- ECMAScript = JavaScript = (현재)ES6

- script를 변경하자마자 script태그로가서 자바스크립트를 봄

## 변수와 식별자

### 식별자 정의와 특징

- 식별자 = 변수명
  - 문자, $, _ 로 시작할 수 있음
- 대소문자 구분, 클래스명 외에는 소문자로 시작

### 식별자 작성 스타일

- 카멜 케이스(camelCase)
  - 시작이 소문자, 중간의 띄어쓰기가 대문자
  - 자바스크립트에서 기본적으로 사용
- 파스칼 케이스(PascalCase)
  - 모든 단어의 첫 번째 글자가 대문자
  - 파이썬 클래스명에서 사용하던 방식
- 대문자 스네이크 케이스(SNAKE_CASE)
  - 상수에 사용
    - API_KEY와 같이 바뀌면 안 되는 중요한 값
    - 변경될 가능성이 없는 값

### 변수 선언 키워드 (`let`, `const`)

- `let`
  - 재할당 할 예정인 변수 선언 시 사용
  - 재할당 가능
    - 정말 변수의 의미
  - 재선언 불가능
  
- `const`
  - 재할당 할 예정이 없는 변수 선언 시 사용
  - 재할당 불가능 
    - `=`(할당기호)가 다시 들어올 수 없음
  - const 상수란 의미\지만 진짜 상수는 아님
  - 값을 바꾸는 걸 못 하는 게 아닌 재할당을 못 하는 것
    - mutable한 개체를 바꾸는 것 가능
    - 기존에 가지고 있던 값을 조작하는 것은 가능
  
  - 한번 참조한 객체는 끝가지 그것만 참조
  
  - 재선언 불가능
  
- 언제 let const 쓰는 게 맞을까?
  - 선언하는 순간 판단하는 건 어려움
  - 그래서 기본적으로 const 사용
    - 의외로 재할당하는 경우 거의 없음
  
- 선언 / 할당 / 초기화
  - 선언: 변수를 생성하는 행위 또는 시점
  - 할당: 선언된 변수에 값을 저장하는 행위 또는 시점
  - 초기화: 선언된 변수에 처음으로 값을 저장하는 행위 또는 시점
  - 자바스크립트는 선언과 할당을 분리할 수 있음
    - 값 없이 선언만 할 수 있음
      - 예약하듯이 이름만 선점
  - 키워드가 있어야 변수를 선언하고 할당할 수 있구나
  
- 블록 스코프(block scope)
  - if, else, 함수 블록을 표현할 때 사용하는 중괄호 내부
  - 블록 안에서 일어난 일은 밖에서 접근할 수 없음
  - indent와 관련
  - 자바스크립트에서는 스코프가 함수가 아니라 중괄호 기준으로 움직인다는 걸 기억
    - cf) 함수 스코프
  
- `var`
  - 구버전 자바스크립트는 let, const 대신 var로 변수 표현
    - 현재 사용하지 않음
  - 함수 스코프
    - 함수의 중괄호 내부
    - 함수 바깥에서 접근 불가능
      - 조건문 안에서 변수 선언했으면 밖에서 그대로 이어짐
  - 호이스팅
    - 변수를 선언 이전에 참조할 수 있는 현상
      - 내가 사용하는 변수나 함수를 값은 아직 안 적지 않은 채 위쪽 레벨로 올려놓음 
    - 에러가 나야하는 게 정상이나 일단 `undefined` 넘겨주는 것
      - 현재는 없지만 뒤에 있으니 끌어 올려서 메모리 상에서 처리
    - `let`, `const`로 선언할 경우 Uncaught ReferenceError 발생
  
- `console.log()` = `print()`

- shift+enter 여러 줄 입력 가능

- `log`쓰고 tab `console.log`



## 데이터 타입

- 변수에 무언가를 할당했을 때 값이 담기는 모양으로 나오는지 / 화살표를 그리며 특정 다른 곳을 가리키는 지로 원시 / 참조 타입 나뉨
- 참조 타입 객체를 기반으로 하는 배열 객체, 함수 객체 등등으로 표시

### 원시 타입과 참조 타입 비교

- 원시 타입
  - 객체(object)가 아닌 기본 타입
  - 변수에 해당 타입의 값이 담김
  - 다른 변수에 복사할 때 실제 값이 복사됨
    - call by value
- 참조 타입
  - 객체(object) 타입의 자료형
  - 여러 개의 원시타입이 모인 덩어리 느낌
    - Array, Function 등
    - Function도 하나의 데이터 타입
  - 다른 변수에 복사할 때 참조 값이 복사됨
    - call by reference 얕은 복사
  - 같은 존재를 두 개의 이름으로 부르고 있었다..

### 원시 타입

- 숫자(`Number`)

  - 정수, 실수 구분 없는 하나의 숫자 타입
  - 무한대 개념 `Infinity`
    - 1/0 에러가 나는 것 아닌 `Infinity`
    - -1/0 `-Infinity`
  - 산술 불가 `NaN`(Not a Number)
    - 계산 불가능한 경우 반환하는 값
    - 숫자가 아니라고 하는 것이 숫자 자료형에 포함
  - `Infinity`와 `NaN` 사용하는 것은 에러를 내지 않게 하기 위함

- 문자열(String)

  - 템플릿 리터럴
    - 문자열을 만들 때 따옴표 대신 백틱 ``` ` 사용해 `${ }` 형태로 사용

- `undefined` / `null`

  - 둘 다 값이 없음을 의미
    - 파이썬의 None이 두 개로 쪼개진 것
  - `undefined` 
    - 개발자 의도가 담기지 않음
    - 함수 리턴값 없을 때 / 변수 선언하고 값을 안 줬을 때 자동으로 할당
  - `null` 
    - 의도적으로 값이 없음을 표현하고 싶을 때
      - 여긴 값이 없어야 해! 표시
    - 자동생성되지 않음, null이라는 말을 직접 입력하지 않으면 볼 일 없음
    - typeof null은 object 객체형 ... 

- `Boolean`

  - `true` / `false` 첫글자 대문자 아닌 소문자

- 자동 형변환

  - 조건문 또는 반복문에서 boolean이 아닌 데이터 타입은 자동 형변환 규칙에 따라 `true`나 `false`로 변환됨
  - 거짓의 값을 갖은 것 falsy value / 참 값을 갖는 것 truthy value 라고 부르기도 함
  
  | 데이터 타입 |    거짓    |        참        |
  | :---------: | :--------: | :--------------: |
  |  Undefined  | 항상 거짓  |        X         |
  |    Null     | 항상 거짓  |        X         |
  |   Number    | 0, -0, NaN | 나머지 모든 경우 |
  |   String    | 빈 문자열  | 나머지 모든 경우 |
  |   Object    |     X      |     항상 참      |
  
  - 비어있는 배열도 true



## 연산자

### 할당 연산자

- `=`
- `++` `--`
  - 1을 더하겠다 / 1을 빼겠다
  - while 문에서 종료 조건을 위해 1을 더해주거나 빼주게 되는데 이 때 num+=1 쓰는 대신 num++으로 활용

### 비교 연산자

- 알파벳끼리도 비교 가능 정확히는 아스키코드 값을 비교하는 것 또 정확히 말하면 유니코드..
  - 글자마다 숫자가 할당되어 있고 그 숫자를 비교하는 것

### 동등 비교 연산자 

- `==`
- 암묵적 형변환 
  - `1 == '1'`의 결과가 true가 됨

- 사용하지 말자..

### 일치 비교 연산자 

- `===`
- 엄격한 비교가 이뤄져 암묵적 타입 변환이 발생하지 않음
- 타입과 값을 모두 비교함
  - 우리가 기대하는 비교 연산

### 논리 연산자

- `&&` and 연산 
- `||` or 연산
- `!` not 연산
  - `!!` 두 번 뒤집으면 true
- 단축 평가 지원

### 삼항 연산자

- 항이 세 개가 필요

  - (단항연산자 - 이항연산자 -, + 등등)

- 전체가 하나의 값으로 변수에 할당 가능

- 가장 왼쪽의 조건식(?앞의 식)이 참이면 : 앞의 값 그렇지 않으면 : 뒤의 값

  ```javascript
  let x = 1 > 2  // false
  x ? 1 : 2 // 2
  
  10 > 1 ? '큽니다' : '아닙니다' // 큽니다 통째로 큽니다라는 값이 됨
  ```

  - 조건 ? if : else 느낌

- `if`와 `else`를 쓸 때 삼항연산자를 쓰는 걸 이쁜 코드라고 함



## 조건문

### `if` statement

- `if`, `else if`, `else`

  ```javascript
  const numOne = 5
  const numTwo = 10
  let operator = '+'
  
  if (operator == '+') {
      console.log(numOne + numTwo)
  } else if (operator == '-') {
      console.log(numOne - numTwo)
  } else if (operator == '*') {
      console.log(numOne * numTwo)
  } else if (operator == '/') {
      console.log(numOne / numTwo)
  } else {
      console.log('유효하지 않은 연산자 입니다.')
  }
  ```

  - 조건은 소괄호 안에 작성
  - 실행할 코드는 중괄호 안에 작성
    - 중괄호로 블럭을 만들어서 코딩을 한다고 생각
  - 닫히는 중괄호 뒤에 바로 `else (if)`가 옴

### `switch` statement

```javascript
const numOne = 5
const numTwo = 10
let operator = '+'

switch(operator) {
    case '+': {
        console.log(numOne + numTwo)
        break
    }
    case '-': {
        console.log(numOne - numTwo)
        break
    }
    case '*': {
        console.log(numOne * numTwo)
        break
    }
    case '/': {
        console.log(numOne / numTwo)
        break
    }
    default: {
        console.log('유효하지 않은 연산자 입니다.')
    }
}
```

- ()안에 값만 비교를 하겠단 의미, 어떤 값(case)에 해당하는지 판별
- 아무것도 처리가 안된다면 default문 실행
  - 선택적 사용
- break 구문이 각 case마다 항상 마지막에 넣어줘야 함 그래야 해당 값만 출력되게 됨
  - 없다면 만족하는 조건 뒤에 오는 값이 다 출력이 되게 되어있음

- 조건이 복합적이면 쓰기 어려움



## 반복문

### `while`

```javascript
let i = 0
while (i < 6) {
    console.log(i) // 0, 1, 2, 3, 4, 5
    i += 1
}
```

- 조건 소괄호 안에 작성, 실행할 코드 중괄호 안에 작성
- 블록 스코프 생성

### `for`

- for문은 범위를 정해주고 그 안에서만 iteration을 도는 것
  - 파이썬은 보통 해당 객체 리스트, range를 알아서 돌지만 자바스크립트는 시작과 끝 값 증가를 설정해야함

```javascript
const arr = [1, 2, 3]

for (let i=0; i<arr.length; i++) {
    console.log(arr[i]) // 1, 2, 3
}
```

- `for (initialization; condition; expression)`
  - initialization 초기화: 최초 반복문 진입 시 1회만 실행
  - condition 조건: 매 반복 시행 전 평가
  - expression 표현식: 매 반복 시행 후 평가
  - 각각을 `;`세미콜론으로 구분

### `for...in`

- 객체의 속성(key)을 순회할 때 사용
  - 여기서 객체는 class의 instance를 말하는 것 아님 
  - 자바스크립트에서 말하는 객체는 딕셔너리와 같이 key-value로 이루어진 자료구조
  - 딕셔너리의 key를 순회할 때 사용한다고 생각하면 됨

```javascript
const capitals = {
    Korea: '서울',
    France: '파리',
    USA: '워싱턴 D.C.'
}

for (let capital in capitals) {
    console.log(capital) // Korea, France, USA
}
```

- `for (let key값 in 객체)` 형태
- 배열 순회 가능하나 권장하지 않음
- 배열을 `for...in`으로 돌릴 경우 index 값이 나옴
  - 배열의 key값이 index라고 판단한 것

### `for...of`

- 반복 가능한 객체를 순회하며 value값을 참조하는 옵션

  - 배열 순회

  ```javascript
  const = fruits = ['딸기', '사과', '수박', '메론']
  for (let fruit of fruits) {
      console.log(fruit)
  }
  for (const fruit of fruits) {
      console.log(fruit)
  }	// const 재할당 안되지만 블럭 스코프가 다시 선언되기 때문에 가능함
  // 내부에서 재할당하고 싶다면 in 사용
  ```

- 파이썬에서의 for문 `for fruit in fruits`



## 함수

- **자바스크립트의 함수는 값이다**

  - 숫자, 문자열, 배열, object를 다 값이라 하는데 여기에 함수도 들어감
  - 파이썬의 함수도 값이지만 자바스크립트에선 그 특징이 더 두드러짐
- `const myFunc = function test() {}`
- 함수란 소괄호를 통해서 실행할 수 있는 특징이 있는 값

- 일급 객체
  - 자연스럽게 변수에 할당이 가능함
  - 변수에 들어갈 수 있다는 것은 다른 함수의 인자로 들어갈 수 있다는 의미
  - 다른 함수의 return 값이 될 수도 있음
  - 위와 같은 조건을 가진 객체를 일급객체라고 함

### 함수 선언식

```javascript
function name(params) { // 함수명(파라미터)
  // do~~                  로직
}

함수명(파라미터)()
```

- `let a = 1`, `const b = 5` 등으로 `let`, `const`를 사용하듯이 `function`을 앞에 써주는 것

### 함수 표현식

```javascript
// 1
let 함수명 = function 함수명2(파라미터){
  로직
}
// 2
let 함수명 = function (파라미터) {
  로직
}

함수명(파라미터)
```

- 정의한 함수를 별도의 변수에 할당하는 것
- 함수의 이름이 필요가 없기 때문에 보통 2번의 형태로 사용
- 자바스크립트에선 익명함수를 쓰는 데, 함수의 인자를 쓰는데 제약이 없음 코드 열 줄을 쓰기도 함
  - 익명함수는 한 번 선언하고 나서 부르지 않겠다는 것

### 기본인자 

```javascript
기본인자
let sayHi = function (name = 'noName'){
  console.log(`${name} 하이하이`);
}

sayHi() // noName 하이하이
sayHi('uusong') // uussong 하이하이
```

- default 값을 넣을 수 있는 것

### 매개변수와 인자의 개수 불일치허용

- 매개변수보다 인자의 개수가 많을 경우

  ```javascript
  const noArgs = function () {
      return 0
  }
  noArgs(1, 2, 3) // 0
  
  const twoArgs = function (arg1, arg2) {
      return [arg1, arg2]
  }
  twoArgs(1, 2, 3) // [1, 2]
  ```

  - 매개변수 개수만큼만 값을 넘겨줌

- 매개변수보다 인자의 개수가 적을 경우

  ```javascript
  const threeArgs = function (arg1, arg2, arg3) {
      return [arg1, arg2, arg3]
  }
  threeArgs()	// [undefined, undefined, undefined]
  threeArgs(1) // [1, undefined, undefined]
  threeArgs(1, 2) // [1, 2, undefined]
  ```

  - 부족한 만큼 `undefined` 반환

### Rest Parameter

```javascript
const restOpr = function (arg1, arg2, ...restArgs) {
    return [arg1, arg2, restArgs]
}
restArgs(1, 2, 3, 4, 5) // [1, 2, [3, 4, 5]]
restArgs(1, 2)	// [1, 2, []]
```

- `...`를 사용해 매개변수보다 인자가 더 많은 것을 배열로 받음
  - 인자가 부족할 경우 `undefined`가 아닌 빈 배열로 처리

### Spread operator

```javascript
const spreadOpr = function(arg1, arg2, arg3){
  return arg1 + arg2 + arg3
}
const numbers = [1, 2, 3]
spreadOpr(...numbers) // 6


const spreadOpr2 = function(arg1, arg2, arg3, arg4){
  return arg1 + arg2 + arg3 + arg4
}
const numbers = [1, 2, 3]

console.log(twoArgs(...numbers, 4)); // 10
```

- `...`를 사용해 배열 인자를 전개함, 펼쳐줌
- 전개하고 남은 매개변수는 들어오는 인자로 처리

```javascript
const array = [1, 2, 3]
const newArray = [0, ...array, 4]

console.log(newArray) // [0, 1, 2, 3, 4]
```

- 배열 내부에서 배열 전개 가능
- 얕은 복사

### 호이스팅(hoisting)

#### 함수 선언식

```javascript
console.log(myFunc()) // true

function myFunc(arg1) {
  return true
}
```

- 함수 선언식으로 선언한 함수에선 호이스팅이 일어남

  - 함수를 통째로 브라우저가 실행하기 전에 메모해놓음
- 함수 호출 이후에 선언해도 동작

#### 함수 표현식

```javascript
console.log(myFunc()) // Uncaught ReferenceError: myFunc is not defined

const myFunc = function(arg1, arg2, arg3, ar4) {
    return arg1 + arg2 + arg3 + arg4
}
```

- 함수 표현식으로 선언한 함수에선 호이스팅이 일어나지 않고 에러 발생

  - 함수를 표현식으로 쓰는 순간 더 이상 함수라기 보다는 변수의 스코프 규칙을 따르게 되기 때문 

    - const 스코프에 종속

- var로 함수 표현식을 작성하면 호이스팅이 일어날까?

  ```javascript
  console.log(testFunc()) // Uncaught ReferenceError: myFunc is not defined
  
  var testFunc = function(arg1, arg2, arg3, arg4) {
    return arg1 + arg2 + arg3 + arg4
  }
  
  // 위 함수는 밑의 함수의 로직과 같음
  
  var testFunc
  console.log(testFunc());
  testFunc = function(arg1, arg2, arg3, arg4) {
    return arg1 + arg2 + arg3 + arg4
  }
  ```

  - 함수가 아니라는 오류가 뜸

  - testFunc이 있긴 하다는 걸 적어두었으나 단순히 이름만 적어둔 것, 변수 선언만 호이스팅 됨

  - 실행시점에선 내부적으로 `undefined` 타입, `undefined()`를 수행하는거나 마찬가지

    

## Arrow Function

- 화살표 같은 형식의 함수
- 함수를 비교적 간결하게 정의할 수 있는 문법

```javascript
// 일반적인 함수 표현식
const arrow1 = function (name) {
  return `${name}님 안녕하세요?`
}

const arrow2 = (name) => {
  return `${name}님 안녕하세요?`
}

const arrow3 = name => {
  return `${name}님 안녕하세요?`
}

const arrow4 = name => `${name}님 안녕하세요?`
```

- `=>` 형태로 쓰면 function이라는 키워드를 생략할 수 있음
- 매개변수가 한 개이면 소괄호마저 생략할 수 있음
- return, 로직이 한 줄이라면 `return`, `{ }` 생략할 수 있음

- Lexical Scope 함수를 어디에서 호출했는지가 중요한 게 아니라 어디에서 선언(=정의)했는지가 중요



## 문자열 (String)

- 문자열: 각각의 문자가 하나로 모여있는것
- [문자열 관련 메서드 정보](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String#%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4_%EB%A9%94%EC%84%9C%EB%93%9C)

## 배열 (Arrays)

- 순서가 있는 자료형
- 앞에서부터 인덱스가 부여되어 있음
- 음수 인덱스 활용 불가 `undefined`
- 마지막 원소를 알기 위해선 `arr.length` 로 길이를 알아내 접근
  - `arr[arr.length-1]`

- [배열 관련 메서드 정보](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array#%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4_%EB%A9%94%EC%84%9C%EB%93%9C)

### 배열을 순회하며 특정 로직을 수행하는 메서드

- 메서드 호출 시 인자로 콜백함수를 받음
  - 배열을 순회하며 특정메서드를 수행하는데 이 때 콜백함수를 실행하려 하는 것
- 콜백함수란 그냥 함수인데 메서드 호출할 때 인자로 넘겨받는 함수
  - 메서드에 인자값으로 전달되는 함수
  - `myFunc(myFunc2)` 마이펑션 내부에서 마이펑션2 실행

#### forEach

````javascript
myArr.forEach( (elem, idx, arr) => {
  // 로직
  console.log(elem, idx)
  // console.log(arr) // 원본 배열이 넘어옴
} )

const images = [
  { height: 10, width: 30 },
  { height: 20, width: 90 },
  { height: 54, width: 32 },
]

const areas = []
images.forEach((elem) => {
    // console.log(elem['height'])
    console.log(elem.height)  // <<<<<< 추천 형식
    // areas.push(elem['height']*elem['width'])
    areas.push(elem.height * elem.width) 
  }
)

console.log(areas)
````

- 배열을 순회하며 특정메서드를 수행하는데 이 때 콜백함수를 실행하려 하는 것
- `forEach`에서 사용한 콜백함수를 밖에서 쓸일 없음 `forEach` 내에서 끝냄 
- 콜백함수는 사용하는 인자가 정해져 있음
  - arr 잘 쓰지 않음 보통 elem, index
- 리턴 값 없음

#### map

```javascript
const newArr = myArr.map( (elem, idx) => {
   // 로직
   return ~~
 })

const images = [
    { height: '34px', width: '39px' },
    { height: '54px', width: '19px' },
    { height: '83px', width: '75px' },
]

const heights = images.map((elem) => {
  return elem.height
})

console.log(heights)
```

- 콜백 함수의 반환 값을 요소로 하는 새로운 배열을 반환
  - 기존 배열 전체를 다른 배열로 바꿀 때 유용
  - 리턴 값을 각각 받아서 새로운 배열을 return
- 배열을 순회하며 콜백함수 실행  한개 씩 한개씩 실행한 결과를 새로운 배열에 담아주는 것
- 원본 배열을 건들지 않음

#### filter

```javascript
const myArr = [1, 2, 3, 4, 5, 6, 7, 8, 9]

const newArr = myArr.filter( (elem, idx, arr) => {
  return elem % 2		// 홀수 조건
  // return !(elem % 2)  // 짝수 조건
} )

console.log(newArr) // [1, 2, 5, 7, 9]

const numbers = [15, 25, 35, 45, 55, 65, 75, 85, 95]

const newArr = numbers.filter((elem) => {
  return 50 < elem
})

console.log(newArr) // [55, 65, 75, 85, 95]
```

- 모든요소를 반복해서 콜백함수 실행하며 작성한 로직을 통과해서 true가 return 되는 애들만 모아서 새로운 배열로 반환

#### reduce

```javascript
myArr.reduce((acc, elem, idx, arr) => {
   // 로직을 처리
}, init )

const myArr = [1, 2, 3, 4, 5]

const rlt = myArr.reduce((acc, elem, idx, arr) => {
  // console.log(acc)
  return (elem * 2) + acc
}, 0 )

console.log(rlt) // 30
```

- acc accumulate 누적값을 모아줌
- 최초의 arr 요소 하나씩 반복하며 콜백함수를 실행하며 return값을 하나하나 accumulate함(acc에 누적) 
  - acc 값을 반환
- `myArr.reduce((acc, elem, idx, arr) => {}, init )`
- acc가 최초의 어떤 값일지를 저장해줘야 함 맨 마지막에 두번째 인자(`init`)로 들어감
- `reduce`메소드에는 콜백함수 / 초기값(init) 두 개의 값이 들어가게 됨
- 콜백함수 시행 독립시행 서로에게 영향 안 미치나 acc로 인해 기억하게됨 
- acc를 이용해 누적시키거나 빼거나 할 수 있게 됨

#### find

```javascript
const myArr = [1, 2, 3, 4, 5]

myArr.find(() => {})
const rlt = myArr.find((elem, idx, arr) => {
  return elem > 3
})

console.log(rlt) // 4

const avengers = [
  {name: 'Tony Stark', age: 45},
  {name: 'Steve Rogers', age: 32},
  {name: 'Thor', age: 40},
]

const avenger = avengers.find((elem)=>{
  return elem.age > 39
})

console.log(avenger.name) // Tony Stark
```

- 배열의 각 요소에 대해 콜백함수를 실행하며 콜백 함수의 반환 값이 true인 경우를 딱 하나를 찾는 순간 return하고 끝남
- 찾는 값이 배열에 없으면 `undefined` 반환
- 조건을 만족하는 값을 다 찾고 싶으면 `filter` 써야함

#### some

```javascript
const myArr = [1, 2, 3, 4, 5]

const rlt = myArr.some((elem) => {
  // console.log(elem) // 1, 2, 3, 4
  return elem > 3
})

console.log(rlt) // true
```

- 배열의 요소중에서 하나라도 콜백 함수의 반환 값이 true가 나오면 true를 리턴
  - 체크하는 느낌 
- return값이 `true` or `false`
- 빈 배열은 항상 거짓

#### every

```javascript
const myArr = [1, 2, 3, 4, 5]

const rlt = myArr.every((elem) => {
  // console.log(elem) // 1
  return elem > 3
})

console.log(rlt) // false
```

- 배열의 모든 요소가 콜백 함수를 통과하면 true 하나라도 통과 못하면 false
- 빈 배열은 항상 참



## 객체 (Objects)

```javascript
const me = {
  // 'firstName': 'John', // 속성
  firstName: 'John',
  lastName: 'Doe',
  // fullName: this.firstName + this.lastName, // NaN
  getFullName: function() { // 메서드
    return this.firstName + this.lastName
  }
}
```

- JSON이 자바스크립트의 객체를 표현하는 방법
  - 중괄호 내부의 key-value 쌍으로 표현
  - key 문자열 타입만 가능
  - value 모든 타임(함수도) 가능
- `.`이나 `[ ]`로 접근 가능
  - `.`을 보통 사용하나 띄어쓰기가 되어있다면 `[ ]`로만 접근 가능
- 메서드는 객체 안에 들어가 있는 함수, JSON안에 들어가 있는 함수 형태
  - value에 함수를 넣은 것
- 메서드 내부에서 `this` 키워드는 객체를 의미
  - `fullname`은 메서드가 아니기 때문에 `NaN`이 출력
  - `getFullName`은 메서드이기 때문에 객체의 `firstName`과 `lastName`을 반환
- key값이 문자열이어야 하는데 따옴표 없이 (문자열로 안) 써도 똑같은 의미
  - key값에 띄어쓰기가 들어간다면 무조건 문자열로 써야 함

### 속성명 축약 

```javascript
const books = ['Learning JS', 'Learning Python']
const magazines = ['Vogue', 'Science']

const bookShop_before = {
  books: books,
  magazines: magazines,
}
// 속성명 축약
const bookShop_after = {
  books,
  magazines,
}
```

- 객체를 정의할 때 key와 할당하는 값의 이름이 같으면 줄여쓸 수 있음

### 메서드명 축약 

```javascript
const books = ['Learning JS', 'Learning Python']
const magazines = ['Vogue', 'Science']

const bookShop_after = {
  books,
  magazines,

  greeting_1: function () {
    console.log('hola!')
  }, 
 // 메서드명 축약
  greeting_2() {
    console.log('hola!')
  },
}

bookShop_after.greeting_2()
```

- 메서드 선언시 function 키워드 생략 가능

### 계산된 속성 (computed property name)

- 동적으로 key의 이름을 바꿀 수 있음
- key값이 따라 바뀜
- 객체를 선언할 때 key-value를 동적으로 변환 가능
- `[ ]` 안쪽에 내가 넣고 싶은 변수를 넣어주면 됨

### 구조 분해 할당 (destructing assignment)

```javascript
const userInformation = {
  name: 'ssafy kim', 
  userId: 'ssafyStudent1234',
  phonenumber: 010-1234-1234,
  email: 'ssafy@ssafy.com',
}

userInformation.name = 'uussong'

// 기존 방식
const name = userInformation.name
const userId = userInformation.userId
const phonenumber = userInformation.phonenumber
const email = userInformation.email

// 구조 분해 할당
const {name} = userInformation
const {userId} = userInformation
const {phonenumber} = userInformation
const {email} = userInformation

const {name, userId, phonenumber, email} = userInformation
const {userId, email} = userInformation

```

```javascript
getUserInfo_bad(userObj) {
  // 기존 방법
  const userId = userObj.userId
  const email = userObj.email
  // 구조 분해 할당
  const {userId} = userObj
  const {email} = userObj
  // 여러 개 한 번에도 가능
  const {userId, email} = userObj

  console.log(`User ID: ${userId}`);
  console.log(`User Email: ${email}`);
}
```

```javascript
// 완전한 방식
function getUserInfo ({userId, email}) {
  console.log(`User ID: ${userId}`);
  console.log(`User Email: ${email}`);
}

getUserInfo(userInformation)
```

- 배열 또는 객체를 분해하여 속성을 변수에 쉽게 할당 가능

### Spread Operator (...)

- 객체 내부에서 객체 전개 가능
- 변수가 아니라 참조라면 리스트가 들어간다면 얕은 복사가 됨

### JSON (JavaScript Object Notation)

- key-value쌍의 형태
- 자바스크립트 객체와 유사하나 실제로는 문자열 타입이기 때문에 JS 객체로 조작하기 위해선 parsing 필수
- `JSON.parse()`
  - JSON을 자바스크립트 객체로 만듦
  - 장고에서 주고 받던 JSON은 JSON형태이지만 문자열로 주고 받음 이것을 자바스크립트의 Obj로 변환
  - `"{'name': 'john', 'age': '23'}"` 이를 JS Obj로 변환
  - `const obj = JSON.parse()`로 받아주면 됨
- `JSON.stringify()`
  - 자바스크립트 객체를 JSON형태의 포멧인 문자열로 변환하는 것

## this

```javascript
function getFullName() {
  return this.firstName + this.lastName
}

const me = {
  firstName: 'John',
  lastName: 'Doe',
  getFullName: getFullName, // this === me
}

const you = {
  firstName: 'zzulu',
  lastName: 'lim',
  getFullName: getFullName, // this === you
}

me.getFullName()  //JohnDoe
you.getFullName() //zzululim
getFullName()     // NaN    // this === window=
```

- JS의 `this`는 실행 문맥에 따라 다른 대상을 가리킴

- 어떠한 객체 안에 있는 메소드에서 사용하는 `this`는 현재 메소드가 속해있는 객체 자체를 의미

- 객체에서 바로 쓰는 객체는 window를 의미

  - window: 보고 있는 브라우저 자체의 객체
    - 브라우저 탭
    - 보고 있는 브라우저에 대한 모든 정보가 담겨있음

  - document (dom 최상위 모델)도 존재

  ```javascript
  const obj = {
      name: 'uusong',
      test: this
  }
  
  obj.name
  'uusong'
  obj.test
  Window {window: Window, self: Window, document: document, name: '', location: Location, …}
  ```

### function 키워드와 화살표 함수 차이

- .bind(this)까지 한 번에 처리한 것이 화살표 함수
- forEach는 콜백함수 / obj 메서드 아님 // printArea는 메서드
  - 메서드가 아니기 때문에 this가 obj로 접근이 안 됨
  - .bind(this)를 써야 메서드 안에 있는 디스와 콜백함수 this를 바인딩해줌
    - 콜백함수 안 쪽에서도 this란 키워드에 접근하기 위함
- 화살표 함수를 사용하면 콜백함수 내에서도 this 접근 가능



## lodash

- _dash 아래있는 dash로 기능을 하는 라이브러리 [공식문서](https://lodash.com/docs/4.17.15)
- sortBy, range, random, cloneDeep -> deepcopy
- `_` 가 lodash 패키지 이름
  - `_.sample()`형태 랜덤하게 한 개의 엘리먼트를 뽑아줌
  - `const myRange = _.range(1, 11, 2)`
  - `const copyArr = _.cloneDeep(myArr)` 참조 타입도 알아서 딥 카피를 해주는 메소드





문자열 / 배열 API 배운 것
