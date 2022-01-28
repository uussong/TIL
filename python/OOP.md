# OOP

### 객체지향 프로그래밍(OOP)

#### 객체

- 파이썬은 모든 것이 객체(Object)로 이뤄져 있다
- 객체 = 상태(속성data: value, attribute) + 동작(기능method:어떠한 객체의 함수)
  - 속성과 동작이 같이 있는 어떤 것, 개념 그 자체
  - 파이썬 내부적으로 속성과 동작이 정의가 되어 있는 것이 객체
- (대상의 정보와 동작 S+V) 주어파트가 객체
- 객체는 특정 타입의 인스턴스(instance)
  - 인스턴스: 객체의 사례, 개별 예시들, 클래스로(를 이용해) 만들어진(생성된) 객체, 메모리에 객체가 실제로 만들어지면 그것을 인스턴스라 함
    - 클래스는 이를 담는 틀
  - 'int/string/list'라는 클래스로 만들어진 객체가 인스턴스
    - `a = 123  type(a)  <class 'int'>`
      - int 앞에 **class**에 주목 
- 객체의 특징
  - 타입: 어떤 **클래스**로 만들어졌는지
  - 속성(attribute): 상태(데이터)
  - 조작법(method): 행위(함수)

#### 객체지향 프로그래밍

- 객체가 중심이 되는 프로그래밍 

  - 컴퓨터 프로그래밍의 패러다임 중 하나

- 객체 지향 프로그래밍은 컴퓨터 프로그램을 명령어의 목록으로 보는 시각에서 벗어나 여러 개의 독립된 단위 즉 객체들의 모임으로 파악하고자 함
  - 속성+메소드(속성을 가지고 조작하는 함수)를 객체로 묶음

- 객체 안에 데이터 메소드들이 있고 객체들 간의 서로 상호작용이 가능하도록 구성

  - 데이터가 중심이 되서 변화시킬 수 있는 메소드들을 구성

  - 기능을 분리시키고 데이터를 직접적으로 조작할 수 있는 형태

- 객체지향 프로그래밍이 필요한 이유

  - 현실 세계를 프로그램 설계에 반영(추상화)
  - 공통된 속성을 모아놓고 각각 뽑아내는 형태
    - 데이터, 행동들을 각각의 맞춰서 정의할 수 있음

```python
#절차지향 프로그래밍
#단순 변수
x_01 = 100
y_01 = 200

area_01 = x_01 * y_01
print(area_01)

x_02 = 10
y_02 = 10

area_02 = x_02 * y_02
print(area_02)

#함수지향 프로그래밍
def area(x, y):
    return x * y
print(area(x_01, y_01))
print(area(x_02, y_02))
```

```python
#객체지향 프로그래밍
class Rectangle:
    
    def area(self):
        return self.x * self.y
    
r1 = Rectangle()
r1.x = 100
r1.y = 200
r1.area()

r2 = Rectangle()
r2.x = 10
r2.y = 10
r2.area()
```

- 클래스: 종류, 어떠한 것을 나누는 기준
  - 어떠한 객체의 타입, 객체를 만들어내는 설계도
  - 클래스를 만드는 건 새로운 타입을 만드는 것과 같음
- 인스턴스: 각각의 사례 
  - 어떠한 클래스로 만들어낸 객체, 클래스 타입을 가진 하나하나의 객체
- 속성: 정보
- 메소드: 어떤 것을 구하는 행동
  - 정보, 행동을 직접적으로 다룰 수 있게 됨
- 객체지향의 장점
  - 프로그램을 유연하고 변경이 용이하게 만듦
  - 소프트웨어 개발과 보수 간편, 직관적인 코드 분석
    - '주어가 동사한다'는 구조가 잘 보임



### OOP 기초

#### 기본 문법

- 클래스 정의 `class MyClass: `  PascalCase
- 인스턴스 생성 `my_instance = MyClass()`
  - 클래스 호출하듯이

- 메소드 호출 `my_instance.my_method()`  snake_case
- 속성 `my_instance.my_attribute()`
  - 메소드와 속성 . 연산자 이용해 접근

#### 클래스와 인스턴스

- 객체의 틀(클래스)을 가지고 객체(인스턴스)를 생성
- 클래스: 객체들의 분류
- 인스턴스: 하나하나의 실체/예
- 파이썬은 모든 것이 객체, 모든 객체는 특정 타입의 인스턴스

#### 속성

- 특정 데이터 타입/클래스의 객체들이 가지게 될 상태/데이터
  - 변수의 값으로 생각

#### 메소드

- 클래스 내부에서 정의된 함수, 공통적으로 적용 가능한 행위 
  - 함수 개념 정의 때 사용한 모든 개념(호출하는 것, 값을 넘겨주는 것) 그대로 적용

#### 객체 비교하기

- ==
  - 동등한 내용, 값들을 가리키는 경우 True
  - 실제로 동일한 대상을 가리키고 있다는 건 아님
- is
  - 동일한 객체를 가리키는 경우 True
  - 객체는 일반적으로 is를 통해 비교
    - `if a is None` 어떠한 값이 None인지를 비교

```python
a = [1, 2, 3]
b = [1, 2, 3]

a == b, a is b # True False

a = [1, 2, 3]
b = a

a == b, a is b # True True
```



### 인스턴스 

#### 인스턴스 변수

- 인스턴스가 가지고 있는 변수
  - 하나하나의 인스턴스의 종속적인 변수, 즉 인스턴스마다 독립적으로 기능

- 인스턴스가 생성된 이후 `instance.name`과 같은 형태로 접근 및 할당
  - . 연산자 활용


#### 인스턴스 메소드

- 인스턴스 변수를 사용하거나 인스턴스 변수에 값을 설정하는 메소드
- 호출시 첫번째 인자로 인스턴스 자기자신(self)이 전달됨
  - 인스턴스 변수를 조작하기 위함


```python
class MyClass:
    def instance_method(self, arg1, ...):
```

#### self

- 인스턴스 자기자신
- 호출시 첫 번째 인자로 인스턴스 자신이 전달되게 설계
  - self라는 이름으로 첫번째 인자를 정의
    - 파이썬의 암묵적 규칙
- 각각의 인스턴스를 조작하기 위해 파이썬이 자동으로 인스턴스 그 자체를 첫번째 인자로 넘겨주는 것
  - 이를 넘겨주지 않으면 인스턴스를 조작할 수 없음

- self를 쓰지 않으면 오류

``` python
# 클래스 정의 (Person)
class Person:
    # 인스턴스 메서드
    #def test():
    #   return 'test'
    def test(self):
        return self
    
# 인스턴스 생성 (p1)
p1 = Person()

# p1.test()
# TypeError: test() takes 0 positional arguments but 1 was given

# <__main__.Person object at ~~
# Python 내부적으로 Person.test(p1)
s = p1.test()
print(s, p1) # 같은 결과

```

#### 생성자 메소드

- `__init__` 

  - 인스턴스 객체가 생성될 때 계속해서 자동으로 호출되는 메소드

  - 인스턴스 변수들의 초기값 설정

  - self가 들어감


```python
class Person:
    
    def __init__(self, name, age):
        # 인스턴스 변수를 정의하기 위해 사용
        self.name = name
        self.age = age
        
#p1 = Person()
#TypeError : __init__()missing 2 required positional arguments
#Person()인스턴스를 만들면 __init__메서드가 호출되는 구나
p1 = Person('길동', 100)
print(p1.name, p1.age) # 길동 100
```

```python
class Person:
    
    def __init__(self, name, age=1):
        # 인스턴스 변수를 정의하기 위해 사용
        self.name = name
        self.age = age
p2 = Person('길동')
print(p2.name, p2.age) # 길동 1
p3 = Person('민지', 999)
print(p3.name, p3.name) # 민지 999
```

#### 소멸자 메소드

- `__del__`
  - 인스턴스 객체가 소멸되기 직전에 호출되는 메소드


```python
class Person:
    
    def __init__(self):
        print('응애')
        
   	def __del__(self):
        print('으억...')
        
p1 = Person() # 응애
del p1 # 으억...
```

