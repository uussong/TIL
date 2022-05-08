# 데이터베이스 관계(M:N)

- 항상 모델링을 먼저 고민
- 현실 세계의 상황을 모델링을 통해 어떻게 구현, 반영을 얼마나 할 수 있느냐가 문제
- 1: N의 한계
  - 다른 곳에 또 방문하고자 하면 인스턴스를 새로 만들어야 함 
    - 새로운 객체를 생성해야 함
  - 한 번에 두 곳을 방문할 수가 없음
    - 하나의 외래 키에 두 개의 데이터를 넣을 수 없기 때문

## ManytoManyField

- 다대다(M:N) 관계 설정 시 사용하는 모델 필드

- M:N 관계로 설정한 모델 클래스를 필수 인자로 받음

- 다대다 관계를 나타내는 중개 테이블이 자동으로 생성되어 중개 모델을 따로 작성하지 않아도 됨

  - 중개 모델 혹은 중개 테이블
    - 양 모델과 1:N을 맺고 있는 즉 각각의 모델에 대한 외래 키를 모두 갖고 있는 모델

- 클래스 이름은 복수형으로 작성

  - 1:N과 구별

- 필드 작성은 어느 곳에 해도 상관 없음

  - 테이블 이름, 컬럼 순서가 바뀌긴 하나 기능이 달라지는 것 아님
  - 서로 종속되는 관계 아닌 대등한 관계
  - 1:N의 경우 N에 무조건 외래키 필드가 있어야 함, 종속적 관계

  ![image-20220418104434583](데이터베이스 관계(M-N).assets/image-20220418104434583.png)

  - 필드 위치에 따라 참조와 역참조 관계가 달라질 수 있음
    - 우리 생각에 편한 곳에 ManyToManyField를 두면 됨

- 1:N 외래키필드 작성한 테이블에 foreign key column이 생기나 M:N 중개 테이블이 생김 

  - M:N관계를 맺는 모델에겐 변화 없음

- 중개 모델(테이블) in Django

  - 자동 생성된 중개 테이블은 class 간의 관계만 표현 가능
    - 외래키 컬럼 두 개로만 만들어짐
  - 추가적인 컬럼을 작성해야 하는 경우에는 중개 테이블을 직접 작성해야함
    - through 옵션 사용
  - 테이블 이름은 다대다 필드의 이름과 이를 포함하는 모델의 테이블 이름을 조합해 생성됨

### Arguments

- `related_name`

  - target model(관계 필드를 가지지 않은 모델)이 source model(관계 필드를 가진 모델) 을 참조할 때 즉 역참조시에 사용하는 manager의 이름을 설정
    - 어느 쪽이 역참조인지 고려할 필요 없어짐
    - 이름 바꾸면 기존 `_set` 명령어 사용 불가
  - `related_name`만 추가 시에 데이터 초기화 할 필요 없이 `migrate`만 다시 해주면 됨
    - `makemigrations` -> `migrate`
  - 일반적으로 M:N에서는 역참조 명령어의 이름을 바꾸나 1:N은 잘 바꾸지 않음
    - 1:N과 구분

- `through`

  - 중개 테이블을 직접 작성/구현하는 경우 through 옵션을 사용해 중개 테이블을 나타내는 장고 모델 지정
  - 중개 테이블에 추가 데이터를 사용하는 다대다 관계와 연결하려는 경우에 주로 사용
    - 추가적으로 중개 모델에 데이터가 있을 경우
  - `through_defaults`를 사용해 `add(), create(), set()` 사용해 관계 생성

  ```python
  # models.py
  
  class Doctor(models.Model):
      name = models.TextField()
  
      def __str__(self):
          return f'{self.pk}번 의사 {self.name}'
  
  
  class Patient(models.Model):
      doctors = models.ManyToManyField(Doctor, through='Reservation')
      name = models.TextField()
  
      def __str__(self):
          return f'{self.pk}번 환자 {self.name}'
  
  
  class Reservation(models.Model):
      doctor = models.ForeignKey(Doctor, on_delete=models.CASCADE)
      patient = models.ForeignKey(Patient, on_delete=models.CASCADE)
      # 추가 데이터
      symptom = models.TextField()
      reserved_at = models.DateTimeField(auto_now_add=True)
  
      def __str__(self):
          return f'{self.doctor.pk}번 의사의 {self.patient.pk}번 환자'
  ```

  ```sql
  doctor1 = Doctor.objects.create(name='justin')
  patient1 = Patient.objects.create(name='tony')
  patient2 = Patient.objects.create(name='harry')
  
  reservation1 = Reservation(doctor=doctor1, patient=patient1, symptom='headache')
  reservation1.save()
  
  patient2.doctors.add(doctor1, through_defaults={'symptom': 'flu'})
  ```

- `symmetrical`

  - 대칭이라는 의미
  - ManyToManyField가 동일한 모델을 가리키는 정의에서만 사용
    - 모델이 self인 경우
  - symmetrical = True(기본값)일 경우 역참조가 동시에 일어나 역참조 매니저(`_set`)가 필요 없어짐
  - source 모델(관계 필드를 가진 모델)의 인스턴스가 target 모델(관계 필드를 가지지 않은 모델)의 인스턴스를 참조하면 target모델 인스턴스도 source 모델 인스턴스를 자동으로 참조하도록 함
    - 즉 팔로우를 하게 될 경우 바로 맞팔이 됨
    - 대칭을 원하지 않는 경우 False로 설정
  - User 모델을 대체해놓았기 때문에 사용 가능

### Related Manager

- 1:N 또는 M:N 관련 컨텍스트에서 사용되는 manager

  - 1:N에서는 target 모델(관계 필드를 가지지 않는 모델) 인스턴스만 사용 가능
  - M:N에서는 관련된 두 객체에서 모두 사용 가능

- `add()`

  - 지정된 객체를 관련 객체 집합에 추가
  - 이미 모델 관계가 되어 있다면, 다대다 관계가 이미 형성되어 있다면 관계가 복제되지 않음

- `remove()`

  - 관련 객체 집합에서 지정된 모델 객체 제거
  - 내부적으론 QuerySet.delete()가 호출됨

  ```sql
  doctor1 = Doctor.objects.create(name='justin')
  patient1 = Patient.objects.create(name='tony')
  patient2 = Patient.objects.create(name='harry')
  
  patient1.doctors.add(doctor1)
  doctor1.patient_set.add(patient2)
  
  doctor1.patient_set.remove(patient1)
  patient2.doctors.remove(doctor1)
  ```



## Like

- User와 Article 간의 좋아요에 대한 관계는 M:N
  - 한 명의 유저는 여러 게시글에 좋아요를 누를 수 있고 게시글은 여러 유저의 좋아요를 받을 수 있음
  - User와 Article은 이미 게시글 작성에 대한 1:N관계
- MantyToManyField 어느 class 두던 상관 없음
  - User에 별다른 작성을 하고 있지 않으니 Article에 작성하자
  - 필드명은 복수형으로 작성
    - `like_users`로 필드명을 지은 것은 보다 직관적으로 어떤 기능인지 알게하기 위함

```python
from django.db import models
from django.conf import settings

class Article(models.Model):
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    like_users = models.ManyToManyField(settings.AUTH_USER_MODEL, related_name='like_articles')
    title = models.CharField(max_length=10)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    def __str__(self):
        return self.title
```

- models.py 에서 유저 모델 참조할 땐 무조건 `settings.AUTH_USER_MODEL`사용

![image-20220418141020566](데이터베이스 관계(M-N).assets/image-20220418141020566.png)

- 기존의 1:N 관계에서의 역참조 manager 이름이 M:N과 겹침 
  - 역참조는 자동으로 `article_set` manager 설정
  - M:N 관계에서의 역참조 manager 이름을 바꾸면 해결됨 
    - `related_name`사용
  - 혹은 User 모델에 작성했다면 이런 문제는 발생하지 않았음
- migrate 한 후에는 Article과 User간의 다대다(M:N) 관계를 저장하기 위한 중개 테이블이 작성됨

```python
@require_POST
def likes(request, article_pk):
    if request.user.is_authenticated:
        article = get_object_or_404(Article, pk=article_pk)
        # 이 게시글에 좋아요를 누른 유저 목록에 현재 요청하는 유저가 있다면 좋아요 취소
        # if request.user in article.like_users.all():
        if article.like_users.filter(pk=request.user.pk).exists():
            article.like_users.remove(request.user)
        else:
            article.like_users.add(request.user)
        return redirect('articles:index')
    return redirect('accounts:login')
```

- 어떤 게시글에 좋아요가 눌릴지 조건을 살펴봐야함
  - 게시글에 좋아요를 누른 유저 목록에 현재 요청하는 유저가 있는지 여부로 좋아요/좋아요 취소 기능을 나눠 구현
  - `like_users` 이 게시글에 좋아요를 누른 유저 목록
- `exists()`
  - 쿼리셋에 결과가 포함되어 있으면 True 그렇지 않으면 False 반환
  - 규모가 큰 쿼리셋에서 특정 개체 존재 여부와 관련된 검색에 유용
  - 고유한 필드가 있는 모델이 쿼리셋의 구성원인지 여부를 찾는 가장 효율적인 방법
    - in 보다 더 효율적, in은 모든 객체를 다 가져온 뒤 거기서 특정 개체가 있는지 확인해 오래 걸림



## Profile Page

```python
# accounts/urls.py

from django.urls import path
from . import views

app_name = 'accounts'
urlpatterns = [
    path('login/', views.login, name='login'),
    path('logout/', views.logout, name='logout'),
    path('signup/', views.signup, name='signup'),
    path('delete/', views.delete, name='delete'),
    path('update/', views.update, name='update'),
    path('password/', views.change_password, name='change_password'),
    path('<username>/', views.profile, name='profile'),
    path('<int:user_pk>/follow/', views.follow, name='follow'),
]
```

- 문자열 변수를 사용하는 url을 맨 위에 만들 경우 문제 발생
- 아래의 url 또한 문자열이므로 맨 위의 view함수에 걸리게 됨
  - url 요청이 들어올 경우 위에서부터 아래로 탐색하기 때문
  - username으로 인식 
    - login유저 페이지, logout유저 페이지 ...
- variable routing이 문자열일 경우 맨 나중에, 맨 밑에서 처리해야 함

```python
def profile(request, username):
	User = get_user_model()
    person = get_object_or_404(User, username=username)
```

- User가 참조하는 AbstractUser에 username이라는 필드가 있음
- username은 유일한 값이므로 기존의 pk역할을 대체할 수 있음



## Follow

- user와 user간 self

```python
class User(AbstractUser):
    followings = models.ManyToManyField('self', symmetrical=False, related_name='followers')
```

- 중개 테이블 필드 생성 규칙에 따라 자기 자신을 참조 할 때는 필드 이름에 from/to가 붙게 됨
  - `from_<model>_id` / `to_<model>_id`

```python
@require_POST
def follow(request, user_pk):
    if reqeust.user.is_authenticated:
        person = get_object_or_404(get_user_model(), pk=user_pk)
        if person != request.user:
            if person.followers.filter(pk=request.user.pk).exists():
                person.followers.remove(request.user)
            else:
                person.follwers.add(request.user)
        return redirect('accounts:profile', person.username)
	return redirect('accounts:login')
```

- `if person != request.user:`
  - 자기 자신을 팔로우 하는 걸 막아야 함