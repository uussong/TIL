# Django Model

- MTV / MVT: 모델이 중요하기 때문에 계속 맨 앞에 오는 것 
  - 뷰: 컨트롤러 / 템플릿: HTML / 모델: 데이터베이스 관련 
- 원래는 모델을 먼저 만들고 뷰와 템플릿을 만드는 순서로 진행

## Model

- 장고에서 사용할 데이터의 구조를 미리 잡아두는 것
  - 이러한 모델은 데이터 각각에 대한 필드가 존재 필드 여러개가 모여 하나의 구조를 이룸

- 장고는 **모델을 통해 데이터에 접근, 관리**

### Database

- DB
  - 체계화된 데이터의 모임, 어떠한 규칙을 가지고 모여있음
  - 데이터베이스는 결국 명령을 이용해서 데이터를 가져오는 것
- 쿼리
  - 데이터 베이스에서 데이터를 가져오기 위한 명령어를 SQL로 날림
  - 데이터 조회, 조건 맞는 데이터 추출, 조작
  - 쿼리를 날린다 = 데이터 베이스를 조작한다

#### Database의 기본 구조

- 스키마(Schema)

  - 데이터베이스가 있을 때 그 데이터베이스가 어떤 구조로 작성이 되어있는가, 안에 들어있는 각각의 필드가 어떠한 관계를 갖고 있는가를 정의한 구조 자체
  - 어떠한 데이터 베이스의 설계도 같은 것

- 테이블(Table) 표

  - 데이터 추가하는 건 항상 row가 늘어나는 것
  - col은 각각의 데이터의 속성들

  - pk: 각각의 데이터를 구분할 수 있는 key, 고유값 일반적으로 id라는 이름을 씀
    - 한 개 일수도 있고 여러 개 일수도 있음
    - 그러나 고유값이므로 중복되지 않고 각각의 값을 하나씩 가지고 있어야 함
    - 특정 값을 지목해 가져올 수 있음, 중복값x
  
- Model은 웹 어플리케이션(장고)의 데이터를 구조화하고 조작하기 위한 도구
  - 조작: CRUD

## ORM

- Object - Relational - Mapping 객체 관계 매핑

  - 데이터 베이스를 model 객체로 접근 
  - model을 사용해서 객체를 만들고 데이터 베이스를 그 객체로 접근해서 사용하는 것

- 객체 지향 프로그래밍 언어를 사용하여 호환되지 않는 유형의 시스템 간에(Django-SQL) 데이터를 변환하는 프로그래밍 기술

  - SQL 작성 않고 파이썬 문법을 가지고 데이터 베이스 조작할 수 있게 한 것

- 데이터 베이스

  ![image-20220308093516416](Model.assets/image-20220308093516416.png)

  - SQL

    - 테이블 존재
    - 데이터베이스를 조작하는 언어, 데이터베이스에서 데이터를 가져오기 위한 일종의 표기법
      - `select from where`
    - 보통의 데이터 베이스, 이를 RDBMS로 생각

  - NOSQL

    - 테이블 없음
    - 데이터 관계를 자유롭게 사용 
      - 채팅 등에서 사용


![image-20220308093542115](Model.assets/image-20220308093542115.png)

- 장고에선 SQL 필요 없이 ORM만으로 데이터베이스에 접근할 수 있음 
- 값을 쿼리셋으로 받음

### ORM의 장점과 단점

- 장점

  - SQL을 잘 알지 못해도 DB 조작 가능, 높은 생산성

- 단점

  - ORM은 SQL의 모든 기능을 다 사용할 수 없음, 대부분의 기능은 사용 가능하나 몇 가지 기능은 사용 힘듦
  - 효율성이 떨어짐

- 현대 웹 프레임워크의 요점은 웹 개발의 속도를 높이는 것(생산성)이 중요 -> ORM 채택

  - ORM으로 개발하고 속도저하일어나는 부분만 SQL로 코드를 바꾸기도

- 데이터 베이스를 객체로 조작하기 위해 ORM 사용

- SQL 모르는데 데이터베이스 쓰고 싶으니까 ORM 사용

### models.py 작성

```python
# articles/models.py
from django.db import models

class Article(models.Model):
    title = models.CharField(max_length=10)
    content = models.TextField()
```

- models.py에 데이터가 어떻게 생길지 / 어떠한 타입이 올지 즉 데이터의 구조를 적음
- class로 만들며 models.Model을 상속받음
- 장고는 따로 지정하지않으면 프라이머리키값을 id에 알아서 추가해줌 따로 지정할 필요가없음

#### 모델 필드

- 공식 문서 [field types](https://docs.djangoproject.com/en/4.0/ref/models/fields/#field-types) 참고

- CharField(max_length=None, **options)
  - 글자가 들어감 여기엔 반드시 최대 몇 글자가 들어갈 건지 적어줘야함 (max_length=)
  - form으로 부터 받은 데이터는 반드시 유효성 검사가 필요한데 이에 활용됨

- TextField(**options)
  - max_length 필요 없음 제한없이 적을 수 있음

- field options
  - null db에 저장될 때 해당 필드에 null값이 들어갈지말지 / blank 해당 필드를 비워둘 수 있는지 여부
  - null은 파이썬에서의 none과 같은 것 아무것도 없다는 것을 나타내는 자료구조
  - 표현 각각의 필드마다 null값을 허용할 건지 정하는 옵션 default=false 기본적으로 null값이 올 수 없음



## Migrations

- 모델을 조작(생성, 수정, 삭제) 하면 반드시 마이그레이션을 생성하고 마이그레이션을 반영(적용)해줘야함
- model을 조작할 때 model의 변경사항을 히스토리로 쌓는것
- 데이터베이스 테이블에 대한 설계도

- `$ python manage.py makemigrations` 
  - migrations>0001_initial.py 생성
- `$ python manage.py migrate` 
  - 실제 migrations을 데이터에 반영
    - 기본기능에 대한 데이터베이스를 반영해주기 위함
  - db.sqlite3 = 데이터베이스
- `$ python manage.py sqlmigrate <앱이름> <migartions 번호>`  
  - ORM이 실제로 어떻게 SQL로 변환됐는가를 확인 할 수 있음

![image-20220308103725887](Model.assets/image-20220308103725887.png)

- `$ python manage.py showmigrations` 

  - 현재 이 장고프로젝트의 모든 migrations 상태를 확인하기 위함

  - migration 파일들이 migrate 됐는지를 보여주는 것

    ![image-20220308104007403](Model.assets/image-20220308104007403.png)

  - 노랑 app 초록 migrations 

  - X가 적용됐다는 의미

#### model 수정

- 추가 모델 필드 작성 후 makemigrations 진행

- DataTimeField
  - 지금 시간 날짜 자동으로 입력// 저장해주는 옵션 있음
- auto_now 
  - 레코드가 변경될 때 마다, 업데이트될때마다 데이터 갱신, 시간 저장
- auto_now_add
  - 최초에 어떠한 레코드가 생성될 때, 최초 한번 자동으로 시간 저장

![image-20220308105117339](Model.assets/image-20220308105117339.png)

![image-20220308105246513](Model.assets/image-20220308105246513.png)

- 이전 row엔 없는데 모델 필드를 추가해달라고 했을 때 이전 row에 있을 수 있는 데이터들의 새로생긴 col 즉 속성에는 어떤 값을 넣어야 하는가?
  - 1 값을 제공해줌 
  - 2 추가하지마 migrations 안 만들어짐 -> default 값을 따로 넣어줘야지 만들 수 있음 

- migrate 해준 후 models.py에 데이터 필드를 추가해 데이터를 갱신한 경우 한 번 더 makemigrations와 migrate를 해줘야 함



## Database API

### DB API

- 실제로 장고에서 데이터베이스를 어떻게 조작하는 지
- `Article.objects.all()`
  - Class Name.Manager.QuerySet API
  - objects manager
    - 장고에 있는 데이터를 접근하게 해주는, 모델과 장고 내부의 model.orm에서 인터프리터 역할을 해준다고 생각하면 됨
  - queryset
    - DB로부터 받은 객체의 목록, 데이터베이스 조회한 결과

### Django shell

- 일반 Python shell을 통해서는 장고 프로젝트 환경에 접근할 수 없음
- ORM을 이용해  DB에서 어떤 데이터를 가져오고 추가하는지 등을 보여주는 기능에서 ORM 먼저 연습

- `pip install django_extensions`  `pip install ipython`(선택) 설치
  - django_extensions는 settings.py에 INSTALLED_APPS에 적어주기
  - `pip freeze`로 requirements.txt 생성
- `python manage.py shell_plus`
  -  장고에 모든 기능을 사용할 수 있는 shell 즉 ORM도 사용가능
  - 나갈땐 `exit()`
- `python manage.py shell`을 쓸 경우`from articles.models import Article` class Article를 따로 import 해줘야 하지만 shell_plus를 쓸 경우 그럴 필요가 없음



## CRUD

- Create Read Update Delete 생성 읽기 수정 삭제
  - 모든 프로그램의 가장 기본적인 기능
- 실제로 장고로 어떻게 crud 할 수 있는지

### CREATE

- 인스턴스를 만들고 하나하나 추가한 뒤 save()

  ```sh
  article = Article()
  article.title = "첫번째 글"
  article.content = "text"
  article.save()

- keyword인자를 넘기는 방식 

  - 처음 생성할 때 파라미터로 값을 넘겨줌

  ```shell
  article = Article(title="두번째 글", content="text")
  article.save()
  ```

- create() 이용하는 방법

  - save() 따로 해줄 필요 없이 한 번에 가능

  ```shell
  Article.objects.create(title="세번째 글", content="text")
  ```

### READ

- `Article.objects.all()` 

  - 현재 QuerySet의 복사본을 반환
  - 테이블의 데이터를 가져오는 것
  - python list 기능 모두 사용 가능

  ```shell
  >>> Article.objects.all()
  <QuerySet [<Article: 첫번째 글>, <Article: 두번째 글>, <Article: 세번째 글>]>
  
  >>> article_1 = Article.objects.all()[0]
  
  >>> article_1.id
  1
  ```

- `Article.objects.get()`

  - 딱 하나의 object만 가져옴 
  - 보통 프라이머리키를 사용해서 가져옴 id=1나 pk=1 같이 사용
    - 장고에서 id라는 값에 pk라는 별명 붙여줌

  ```shell
  >>> article = Article.objects.get(id=1)
  
  >>> article.title
  '첫번째 글'
  ```

- `Article.objects.filter()` 
  - 조건과 일치하는 모든 데이터 가져옴
- Field lookups 
  - `get()`, `filter()` 괄호 안에 어떤 필드를 찾을건지 조건을 씀
  - `속성__field lookups='값'`의 형태 
  - contains, in, isstartswith ... 등
  - [공식문서](https://docs.djangoproject.com/en/3.2/ref/models/querysets/#field-lookups) 참고

### UPDATE

- 다시 값을 주고 저장

```shell
>>> article = Article.objects.get(pk=1)
>>> article.title
'첫번째 글'

>>> article.title = "첫번째 글 수정"
>>> article.save()

>>> article.title
'첫번째 글 수정'
```

### DELETE

- `article.delete()`

```shell
>>> article = Article.objects.get(pk=1)
>>> article.delete()
(1, {'article.Article': 1})

>>> Article.objects.all()
<QuerySet [<Article: 두번째 글>, <Article: 세번째 글>]>
```



## Admin Site

- 기본적으로 제공되는 장고의 관리자 기능

- 계정 생성
  - `$ python manage.py createsuperuser`
  - 이메일 아무거나 적어도 됨 비밀번호의 경우 보안을 위해 치더라도 화면에 표시되지 않음

- admin 등록

  ```python
  from django.contrib import admin
  from .models import Article
  
  admin.site.register(Article)
  ```



## CRUD with views

- 모델을 이용해서 데이터를 가져옴
- 가져온 데이터를 조작
  - 템플릿으로 넘기거나 데이터 삭제, 수정 등 
- 템플릿에서 데이터를 보여줌

- `title = request.GET.get('title')`: GET 방식의 데이터 중에서 name이 title인 것을 가져오기
- `title = request.POST.get('title')`: POST방식일 경우

![image-20220308162707073](Model.assets/image-20220308162707073.png)

- 분홍색은 모델에 적어준 field 명

- 게시글 정렬 순서 변경
  - `articles = Article.objects.all()[::-1]`: 슬라이싱 가져와서 바꿔줌
  - `articles = Article.objects.order_by('-pk')`: 내림차순정렬 정렬된 상태로 가져옴
    - all이 포함되어 있다고 생각하면됨
    - 일부만 정렬하고 싶으면 filter() 사용: `Article.objects.filter().order_by('-pk')`

### HTTP method

#### GET

- 기본값, 서버에 특정 리소스를 요청할 때 사용
  - R역할
- URL에 Querystring 담김

#### POST

- 리소스를 생성, 수정, 삭제할 때 사용
  - C, U, D역할
- 데이터를 HTTP body에 담아 전송

### CSRF

- 사이트 간 요청 위조(Cross-site request forgery)
- 바로 url 쿼리스트링으로 접근하는 것을 CSRF Token으로 방지
- 데이터를 보내고 받는 과정에서 암호(token)를 주고 받는 것
- POST를 쓰려면 항상 `{% csrf_token %}`을 붙여줘야함

### redirect()

```python
# articles/views.py
from django.shortcuts import render

def create(request):
    title = request.POST.get('title')
    content = request.POST.get('content')
    
    article = Article(title=title, content=content)
    article.save()
    return render(request, 'articles/create.html')
```

- 글 작성 후 index 페이지 출력되지만 게시글이 조회되지 않고 URL이 여전히 create에 머물러 있는 문제 발생
- 단순히 index 페이지만 render 된 것
  - create에는 context가 없으니 render할게없음
  - create view 함수에서 다루고 있는 데이터로 index 페이지가 render 됨
  - render: template을 render해서 넘겨주는 것 

```python
# articles/views.py
from django.shortcuts import render, redirect

def create(request):
    title = request.POST.get('title')
    content = request.POST.get('content')
    
    article = Article(title=title, content=content)
    article.save()
    return redirect('articles:index')
```

- redirect
  - 새 URL로 요청을 다시 보냄
  - 브라우저는 현재 경로에 따라 전제 URL 자체를 재구성
  - redirect 사용하는 이유는 내용을 똑같이 적는 것이 불필요하기 때문
