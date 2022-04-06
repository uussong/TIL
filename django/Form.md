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

#### Form 선언하기

- `ctrl + shift + p` select interpreter -> venv 선택

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
  - input 유효성 검사 처리

- Widgets

  - [textarea 같은 것](https://docs.djangoproject.com/en/4.0/ref/forms/widgets/)은 form fields로 표현되지 않음 -> widgets 사용

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
          (REGION_A, '서울'),
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

