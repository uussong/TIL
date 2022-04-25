# JavaScript 기초

## JavaScript Intro

- 자바스크립트는 브라우저를 동적으로 움직이게 하기 위해 필요
- 브라우저를 조작할 수 있는 유일한 언어
  - 브라우저가 이해할 수 있는 프로그래밍 언어는 자바스크립트 뿐
  - HTML, CSS는 프로그래밍 언어가 아님



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
    - 에러가 나야하는 게 정상이나 일단 undefined 넘겨주는 것
      - 현재는 없지만 뒤에 있으니 끌어 올려서 메모리 상에서 처리
    - let, const로 선언할 경우 Uncaught ReferenceError 발생
- `console.log()` = `print()`
- shift+enter 여러 줄 입력 가능



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
  - 다른 변수에 복사할 때 참조 값이 복사됨
    - call by reference 얕은 복사
  - 같은 존재를 두 개의 이름으로 부르고 있었다..

### 원시 타입

- 숫자(Number)

  - 정수, 실수 구분 없는 하나의 숫자 타입
  - 무한대 개념 Infinity 
    - 1/0 에러가 나는 것 아닌 infinity
    - -1/0 -infinity
  - 산술 불가 NaN(Not a Number)
    - 계산 불가능한 경우 반환하는 값
    - 숫자가 아니라고 하는 것이 숫자 자료형에 포함
  - Infinity와 NaN 사용하는 것은 에러를 내지 않게 하기 위함

- 문자열(String)

  - 템플릿 리터럴
    - 문자열을 만들 때 따옴표 대신 백틱 ``` ` 사용해 `${ }` 형태로 사용

- `undefined` / `null`

  - 둘 다 값이 없음을 의미
    - 파이썬의 None이 두 개로 쪼개진 것
  - 설계 미스..
  - `undefined` 
    - 개발자 의도가 담기지 않음
    - 함수 리턴값 없을 때 / 변수 선언하고 값을 안 줬을 때 자동으로 할당
  - `null` 
    - 의도적으로 값이 없음을 표현하고 싶을 때
      - 여긴 값이 없어야 해! 표시
    - 자동생성되지 않음, null이라는 말을 직접 입력하지 않으면 볼 일 없음
    - typeof null은 object 객체형 ... ㅎ

- Boolean

  - true / false 첫글자 대문자 아닌 소문자

- 자동 형변환

  - 조건문 또는 반복문에서 boolean이 아닌 데이터 타입은 자동 형변환 규칙에 따라 true나 false로 변환됨

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
- 암묵적 형변환 `1 == '1'`의 결과가 true가 됨
- 사용하지 말자..

### 일치 비교 연산자 

- `===`
- 엄격한 비교가 이뤄져 암묵적 타입 변환이 발생하지 않음
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
- break 구문이 각 case마다 들어가 있음 없다면 만족하는 조건 뒤에 오는 값이 다 출력이 되게 되어있음
- 항상 break를 써주어야 해당 값만 출력되게 됨
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
  - initialization 최초 반복문 진입 시 1회만 실행
  - condition 매 반복 시행 전 평가
  - expression 매 반복 시행 후 평가

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

- 반복 가능한 객체를 순회 value값 나옴

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





