# Django Form

## Django Form Class

- 입력된 데이터의 유효성을 검증하고 필요시 검증 결과와 함께 다시 표시하는 과정 필요
  - 사용자가 입력한 데이터는 개발자가 요구한 형식이 아닐 수 있음
    - ex. 숫자를 요구했는데 문자 입력
- 유효성 검증: 사용자가 입력한 데이터를 검증하는 것
  - Django Form을 통해 작업 쉽게 가능

### Django's forms

- 장고의 유효성 검사 도구 중 하나
- 데이터 손상에 대한 방어 수단
- 장고는 Form과 관련한 유효성 검사를 단순화, 자동화 할 수 있는 기능 제공
- 역할
  - 렌더링을 위한 데이터 준비 및 재구성
  - 데어터에 대한 HTML forms 생성
  - form에서 작성된 데이터를 수신 및 처리

### Django 'Form Class'

- Form Class를 상속받아 subclass로 사용할 것
- field, field 배치, 디스플레이 widget, label, 초기값, 유효하지 않은 field에 관련된 에러 메세지
- 데이터 유효성 검증 등 과중한 작업에 대해 반복 코드를 줄여줌
- 재사용하기 쉬움
- for-id 자동으로 맞춰줌

#### Form 선언하기

- `ctrl + shift + p` select interpreter -> venv 선택: 가상 환경 활성화

- `pip install -r requirements.txt`

  ```python
  # articles/forms.py
  
  from django import forms
  
  class ArticleForm(forms.Form):
      title = forms.CharField(max_length=10)
      content = forms.CharField()
  ```

- 모델 필드와 유사한 구조

  - `models.Model / forms.Form`: 가져오는 것이 다름
  - textfield 자동완성 안 됨 -> 쓸 수 없는 건가?

  ```python
  # articles/views.py
  
  from .forms import ArticleForm
  
  def new(requeest):
  	form = ArticleForm()
      context = {
          'form': form,
      }
      return render(request, 'articles/new.html', context)
  ```

- form을 인스턴스로 만듦

#### Form rendering options

- 그냥 `{{ form }}`으로만 적을 경우 각각의 필드가 한 번에 묶여 가로로 배치
- `as_p()` 각각의 필드가 p태그로 감싸져서 렌더링
  - `{{ form.as_p }}` 형태로 사용

#### Django의 HTML input 요소 표현 방법

- Form fields

  - 각각의 필드 타입을 form fields를 이용해 표현
  - 유효성 검사 처리하는 input 태그를 생성해 주는 항목

- Widgets

  - [textarea 같은 것](https://docs.djangoproject.com/en/4.0/ref/forms/widgets/)은 form fields로 표현되지 않음 -> widgets 사용
  - widget에 따라 같은 form이래도 형식이 달라지게 됨
  
  ```python
  # articles/forms.py
  
  from django import forms
  
  class ArticleForm(forms.Form):
      REGION_A = "sl"
      REGION_B = "dj"
      REGION_C = "gj"
      REGION_D = "gm"
      REGION_E = "bu"
      REGION_CHOICES = [
          (REGION_A, '서울'),	# 데이터 베이스에 저장 / 사용자에게 보여지는 부분
          (REGION_B, '대전'),
          (REGION_C, '광주'),
          (REGION_D, '구미'),
          (REGION_E, '부산'),
      ]
      
      title = forms.CharField(max_length=10)
      content = forms.CharField(widget=forms.Textarea)
      region = forms.ChoiceField(choices=REGION_CHOICES, widget=forms.Select())
  ```
  
  - 단독으로 사용할 수 없고 field에 속해져 있는 상태
  - 단순히 input element의 단순 raw한 렌더링 처리
  
    - textarea로 바꿔준다거나 하는 것만 처리
    - input element의 표현을 바꿈
      - 태그, 인풋의 타입 속성 등
    - HTML 렌더링 처리
  - 유효성 검사와 관련 없음
  - [코딩 스타일](https://docs.djangoproject.com/en/dev/internals/contributing/writing-code/coding-style/)에 따라 작성



## Model form

- 폼에서 사용자에게 입력받기 위한 필드를 정의하지만 이 필드는 모델 필드를 작성할 때 이미 한 번 썼던 필드를 폼에서 다시 쓰는 것
  -  즉 재정의 하는 행위, 정의하는 행위가 중복됨
- Model Form은 모델에 정의된 데이터 타입 필드를 읽고 이를 기반으로 폼을 만들어주는 것
- 장고는 이미 만든 모델 구조에 맞춰 Form class를 만들어 중복을 방지
- 모델 폼이 쉽게 해주는 것
  - 모델 필드 속성에 맞는 html element를 만들어주고
  - 이를 통해 받은 데이터를 view 함수에서 유효성 검사를 할 수 있도록 함

### ModelForm Class

```python
# articles/forms.py

from django import forms
from .models import Article

class ArticleForm(forms.ModelForm):
    
    class Meta:
        model = Article
        fields = '__all__'
        # exclude = ('title',)
```

- `forms.ModelForm` 상속
- 정의한 클래스 안에 Meta 클래스 선언
  - model: 어떤 모델을 기반으로 Form을 작성할 것인지 지정
  - fields: 모델 필드 중 어떤 필드를 출력할 것인지 지정
  - exclude: 특정 필드를 제외할 때 사용
    - 클래스 변수 fields와 exclude는 동시에 쓸 수 없음

#### Meta class

- Model 정보를 작성
- ModelForm을 작성할 경우 사용할 모델이 있어야 하는데 메타 클래스가 이를 구성
  - 모델에 정의한 필드 정보를 폼에 적용하기 위함
- 필드 정의 따로 없이 모델만 등록하며 장고가 이 모델을 해석해서 필드 구성
- Inner Class
  - 클래스 내에 선언된 다른 클래스
- Meta 데이터
  - 데이터에 대한 데이터

- 모델 폼을 왜 쓰냐? 
  - form 사용자의 정보를 입력받는 역할 일반적으로 이 정보를 db에 저장하게 됨
    - form과 db는 밀접한 관련
  - db의 구조를 그대로 form에서 사용하면 편함 
  - db에 저장되는 input 구조에서 modelform 사용
  - 실제 db에 저장된 데이터를 받으려면 modelform 사용해야
- db와 연관 없지만 사용자의 입력을 받고 별도로 처리해야 한다면 form이 적합

HTML form / Form Class / Model form 나눠서 정리해보자

### is_valid() method

- 유효성 검사를 실행하고 데이터가 유효한지 여부를 boolean으로 반환
- 유효성 검사
  - 요청한 데이터가 특정 조건에 충족하는지 확인하는 작업
  - 데이터베이스 각 필드 조건에 반하는 데이터가 서버로 전송되거나 저장되지 않도록 하는 것
    - max_length 넘어가는 등 통과하지 못 하는 경우 있음
- 데이터 각각 받아서 변수에 저장x
- article form의 인자로서 한 번에 다 받아짐 

### The save() method

- 폼에 바인딩된(저장된) 데이터에서 데이터베이스 객체를 만들고 저장
  - 만들어진 객체를 반환하고 데이터 베이스에 저장

  ```python
  from .models import Article
  from .forms import ArticleForm
  
  form = ArticleForm(request.POST)
  
  # CREATE
  new_Article = f.save()
  
  # UPDATE
  article = Article.objects.get(pk=1)
  form = AritlceForm(request.POST, instance=article)
  form.save()
  ```

- ModelForm의 서브 클래스 article form

  - 기존 모델 인스턴스를 키워드 인자 instance로 받을 수 있음
    - 제공될 경우 save()는 해당 인스턴스를 수정하는 update 역할을 함
    - 제공되지 않은 경우 save()는 지정된 모델의 새 인스턴스를 만드는 create 역할을 함

- 유효성 검사를 통과하지 못 하는 경우 `save()` 호출할 때 `print(form.errors)`로 에러 메세지 확인 가능
  - 어떤 에러를 냈는지 확인 가능
