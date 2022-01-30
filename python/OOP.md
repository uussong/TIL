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

#### 매직 메소드

- Double underscore(__)가 있는 메소드는 특수한 동작을 위해 만들어진 특별한 기능을 하는 메소드
- 특정한 함수를 호출할 때 매직메소드를 쓰도록 되어있음
  - 특정 상황에서 자동으로 불리는 메소드
    - 내부적인 구현을 공통적으로 가져가기 위함 

- 스페셜 메소드 혹은 매직 메소드라고 불림

```python
class Person:
    
    def __init__(self, name, age, height):
        self.name = name
        self.age = age
        self.height = height
        
    def __str__(self):
        return f'<{self.name}> : {self.age}살'
        
    def __gt__(self, other):
        print(f'{self.name}: {self.age}살 / {other.name}: {other.age}살')
        return self.age > other.age
   
	def __len__(self):
        return self.height
    
p1 = Person('tom', 100, 190)
p2 = Person('john', 10, 185)
p1 > p2 
# tom: 100살 / john: 10살
# True
len(p1) # 190
len(p2) # 185

print(p1) # <tom>: 100살
```

- `__str__`
  - 해당 객체의 출력 형태를 지정
  - 객체 자체를 문자열로 바꿨을 때 어떻게 보였으면 좋겠는지에 방점을 찍고 구현
  - 프린트 함수를 호출할 때 자동으로 호출
    - 어떤 인스턴스를 출력하면 `__str__`의 return 값 출력
- `__repr__`
  - 해당 객체의 출력 형태를 지정
  - `__repr__`로 처리된 값을 보고 해당 객체를 구현할 수 있게 객체에 대한 정보를 담음
- `dir()`을 통해 매직 메소드 확인 가능
  - `__str__(self)`, `__len(self)__`, `__repr__(self)`
  - class간 비교를 구현해주기 위한 매직 메소드
    - `__lt__(self, other)`, `__le__(self, other)`, `__eq__(self, other)`, `__gt__(self, other)`, `__ge__(self, other)`, `__ne__(self, other)`  



### 클래스

#### 클래스 변수

- 한 클래스의 어떤 인스턴스라도 똑같은 값을 가지고 있는 속성 
  - 클래스로 만들어진 모든 인스턴스가 공유
- 클래스 영역 내부에서 정의
  - 설계를 할 때 클래스 변수가 있는 형태로 설계해야

- `<classname>.<name>`으로 접근 할당

```python
class Circle:
    pi = 3.14
    
    def __init__(self, r):
        self.r = r
    
    def area(self):
        return Circle.pi * self.r * self.r
    
Circle.pi # 3.14

c1 = Circle(2)
c1.area() # 12.56

c1.pi # 3.14

c2 = Circle(3)
c2.area() # 28.599

c2.pi # 3.14
```

#### 클래스 메소드

- `@classmethod` 데코레이터를 사용하여 정의
  - 데코레이터: 함수를 어떤 함수로 꾸며서 새로운 기능을 부여
- 클래스 자체에 정의되어있는 클래스 속성을 조작하고 싶을 때 사용
- 호출시 첫번째 인자로 클래스(cls)가 전달
  - 클래스를 조작할 아이니 내부적으로 호출되면서 클래스를 넘겨줌
  - 인스턴스의 self와 같은 역할

```python
class MyClass:
    var = 'Class 변수'
    
    @classmethod
    def class_method(cls):
        print(cls.var)
        return cls
    
MyClass.class_method() 
# Class 변수
# __main__.MyClass
MyClass #__main__.MyClass
```

#### 인스턴스와 클래스 간의 이름 공간(namespace)

```python
class Circle:
    pi = 3.14
    
    def __init__(self, r):
        self.r = r
        
c1 = Circle(2)
print(c1, r)
```

- 클래스를 정의를 하는 순간 클래스 공간이 생기며 이 안에 클래스 변수가 들어가 있음
- 인스턴스를 만드는 순간 (실제 init생성자가 호출되면서 생성될 때) 인스턴스 공간이 생성
- 인스턴스에서 특정 속성에 접근하면 인스턴스-클래스 순으로 탐색
  - 같은 이름이면 인스턴스의 namespace로만 접근할 수 있음
  - 인스턴스에 이름이 없으면 오브젝트에서 찾고 이를 통해 클래스 변수에 접근


#### 스태틱 메소드

- `@staticmethod` 데코레이터를 사용해 정의
- 인스턴스 변수나 클래스 변수를 가지고 어떠한 역할도 하지 않지만 클래스 안에 메소드를 정의하고 싶을 때 사용
- 호출 시 어떠한 인자도 전달되지 않음
- 클래스와도 인스턴스와도 관계없음을 보여줌

```python
class MyClass:
    
    @staticmethod
    def static_method(static):
        return static
    
MyClass.static_method()
# static_method() missing 1 required positional argument
# 1개 값을 왜 안 넘겨줘? 어떠한 인자도 자동으로 넘어가는 게 없음

class MyClass:
    
    @staticmethod
    def static_method(static):
        return 'static'
MyClass.static_method() # 'static'
```

```python
class MyClass:
    
    # 함수는 기본적으로 로컬 스코프
    # 내부에서 활용하고 싶으면 파라미터로 받도록 정의
    
    # 인스턴스 메서드: 인스턴스를 조작하고 싶어
    # 함수 내부에 인스턴스를 던져주도록 설계
    # 메서드를 정의할 때 self로 받도록 
    def instance_method(self):
        return self
    
    @staticmethod
    def static_method(static):
        return static
    
    # 클래스 메서드: 클래스를 조작하고 싶어
    # 함수 내부에 클래스를 던져주도록 설계
    # 메서드를 정의할 때 cls로 받로록
    @classmethod
    def class_method(cls):
        return cls
    
    # 스태틱 메서드: 클래스나 인스턴스를 조작할 생각은 없는데 함수를 쓸거야
    # 아무 것도 넘겨주지 않도록 설계
    @staticmethod
    def static_method():
        return ''
```

### 메소드 정리

#### 인스턴스 메소드

- 각각의 만들어진 인스턴스를 조작할 때 사용
- 호출한 인스턴스를 의미하는 self 매개 변수를 통해 인스턴스 조작

#### 클래스 메소드

- 클래스를 의미하는 cls 매개 변수를 통해 클래스 조작
- 클래스 종속적

#### 스태틱 메소드

- 인스턴스나 클래스를 의미하는 매개변수는 사용하지 않음 
  - 객체 상태나 클래스 상태를 수정할 수 없음
- 일반 함수처럼 동작하지만 클래스의 이름공간에 귀속
- 해당 클래스로 한정하는 용도로 사용

```python
class MathUtility:
    
    @staticmethod:
    def get_pi():
        return 3.141592
    
    @staticmethod
    def get_e():
        return 2
```

```python
class PersonUtility:
    
    @staticmethod
    def get_phone_number(phone_number):
        return phone_number[:2] + ')' + phone_number[2:]
    
PersonUtility.get_phone_number('0215775588')#02)15775588
```



### 객체 지향의 핵심개념

#### 추상화

- 어떠한 것을 만들고 싶을 때 이를 만들어놓고 사람들이 쓸 수 있도록 내 프로그램에서 정의가 되어있는 클래스를 만들고 그 행동들을 정의
- 내부로직을 모르더라도 사용자들은 추상화된 class를 쓸 뿐

#### 상속

- 클래스는 상속이 가능
- 두 클래스 사이의 부모-자식 관계를 정립

```python
class ChildClass(ParentClass):
    pass
```

- 하위클래스(자식클래스)는 상위클래스(부모클래스)에 정의된 속성을 모두 상속 받음
- 상속을 통해 메소드 재사용 가능, 코드의 재사용도 높아짐 
  - DRY원칙 (Don't Repeat Yourself)
  - 특성을 그대로 가져오고 커스터마이징 하고 싶은 건 커스터 마이징 함

- 계층구조를 계속 만들어 나갈 수 있음
- 실제 개발에선 클래스의 계층구조를 최대한 다양하게 나누는 경우가 많음

##### 상속 관련 함수와 메소드

```python
class Person:
    
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def talk(self):
        print(f'반갑습니다. {self.naame}입니다.')
        
p1 = Person('김', 30)
p1.talk() #반갑습니다. 김입니다.
```

```python
class Professor:
    
    def __init__(self, name, age, department):
        self.name = name
        self.age = age
        self.department = department
        
prof1.Professor('김교수', 50, '컴공')
prof1.talk() # AttributeError: 'Professor' object has no attribute 'talk' 
```

```python
class Professor(Person):
    
    def __init__(self, name, age, department):
        self.name = name
        self.age = age
        self.department = department
        
prof1.Professor('김교수', 50, '컴공')
prof1.talk() # 반갑습니다. 김교수입니다.
```

```python
class Student(Person):
    
    def __init__(self, name, age, gpa):
        self.name = name
        self.age = age
        self.gpa = gpa
        
    def talk(self):
        print(f'{self.name}입니다. 교수님. ^^7')
s1 = Student('김', 20, 4.5)
s1.talk() # 김입니다. 교수님. ^^7
```

- `isinstance(object, classinfo)`
  - classinfo의 instance거나 subclass인 경우 True
- `issubclass(class, classinfo)`
  - class가 오른쪽의 클래스(classinfo)의 subclass인가를 확인

```python
class Person:
    pass

class Student(Person):
    pass

class Professor(Person):
    pass

p1 = Person()
s1 = Studnet()
prof1 = Professor()

isinstance(p1, Person) # True
isinstance(s1, Person) # True
isinstance(p1, Student) # False
issubclass(Student, Person) # True
issubclass(bool, int) # True 
					  # bool 0, 1 int 1, 2, 3, 4, 5, ...
issubclass(float, int) # Flase
					   # float 실수.. 정수 + 소수..
```

- super()
  - 자식클래스에서 부모클래스를 사용하고 싶은 경우 상위클래스에 직접 접근하고 싶을 때 사용
    - super()를 통해 실제 부모 클래스를 받아 내부적으로 쓸 수 있음
    - 메소드 오버라이딩을 통해 재정의 가능

```python
class Person:
    
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def talk(self):
        print(f'반갑습니다. {self.naame}입니다.')
        
class Student(Person):
    
    def __init__(self, name, age, studnet_id):
        super().__init__(name, age)
        self.student_id = student_id

s1 = Student('이', 26, '20220101')
s1.name #이
s1.age #26
```

##### 다중 상속

- 클래스를 두 개 이상 받는 것
  - 상속 받은 모든 클래스 요소 활용 가능

- 중복된 속성이나 메서드의 경우 상속 순서에 의해 결정
  - 먼저 상속한 것의 영향받음

- mro 메소드 (Method Resolution Order) 
  - 메소드를 뭐를 먼저 할 것인지 해결해나가는 순서가 있음
  - 먼저 상속받은 것이 앞 순서
  - 모든 것의 끝에는 object

```python
class A:
    name = 'A'
    
class B(A):
    name = 'B'
   
class C(A):
    name = 'C'
    
class D(B, C):
   pass

d = D()
print(d.name) #B 먼저 선언된 것 따름
```

#### 다형성

- 동일한 메소드가 클래스에 따라 다르게 행동할 수 있음
  - 서로 다른 클래스에 속해있는 객체들이 동일한 메시지에 대해 다른 방식으로 응답될 수 있음

- 상속 받은 메소드를 재정의 (메소드 override)
  - 클래스 상속시 부모클래스에서 정의한 메소드를 자식 클래스에서 변경할 수 있음
  - 특정 기능을 바꾸고 싶을 때 사용
  - 부모 클래스 메소드를 실행시키고 싶은 경우 `super()` 활용

#### 캡슐화

- 은닉성, 접근에 대한 권한
- 암묵적으로 존재하지만 언어적으로 존재하지 않음

##### 접근제어자

- Public Access Modifier 
  - 어디서나 접근 가능
    - 일반적인 형태

- Protected Access Modifier 
  - 상속관계에서만 접근 가능
  - 언더바 1개로 시작
  - 암묵적 규칙으로 내부에서만 호출 가능


```python
class Person:
    
    def __init__(self, name, age):
        self.name = name
        self._age = age
       
    def get_age(self):
        return self._age
    
p1 = Person('김', 23)
p1._age # '_' 암묵적으로 이렇게 직접적으로 접근하지 말자는 것
```

- Private Access Modifier 
  - 내 클래스 안에서만 접근 가능
  - 언더바 2개로 시작
  - 해당 클래스 바깥에서 호출 불가능
    - 직접 접근하지 않고 메서드를 통해 조작해야함

- 파이썬에서 public과 protected는 언어 차원에서 접근을 막아주지 않아 어디서 접근하여도 에러가 없는 반면 private은 언어 차원에서 접근을 막아줌(name mangling을 통해 기능)
- 코드의 은닉성을 띄게하고 싶을 땐 protected를 위주로 사용
  - protected에 잘못 접근하여도 에러가 나지 않아 코드의 문제가 생기지 않음
    - 그렇더라도 `_`를 통해 protected라 언급해줬다는 걸 기억해야함


```python
class Person:
    
    def __init__(self, name, age):
        self.name = name
        self.__age = age
       
    def get_age(self):
        return self._age

p1 = Person('김', 23)
p1.__age #접근 불가능
p1.get_age() #접근 가능
```

- getter 메소드
  - 무언가를 주는 메서드
    - 변수 값을 읽음
  - `@property`
- setter 메소드
  - 새로 값을 받아 가지고 있는 속성에 할당하는 메서드
    - 변수 값을 설정

  - `@변수.setter`


```python
class Person:
    
    def __init__(self, age):
        self._age = age
   
	@property
    def age(self):
        return self._age 
    
    @age.setter
    def age(self, new_age):
        self._age = new_age - 10
   
p1 = Person(10)
#p1.age() TypeError
p1.age # 메서드를 정의했는데 속성처럼 쓰도록 한다

p2 = Person(40)
p2.age # 30
```

