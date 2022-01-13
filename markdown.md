# Markdown 실습 



# 헤딩(Heading)  #

문서의 제목이나 소제목으로 사용

- #의 개수에 따라 제목의 수준을 구별 (h1~h6: #~######)
- 문서 구조의 기본
- 글자 크기를 키우기 위해서 사용하면 안 됨 - 각각의 태그가 갖는 의미가 있기 때문!

# 리스트(List) 

순서가 있는 리스트와 순서가 없는 리스트 1. 2. 3.(1) 2) 3) ) // * -

- 목록을 표시하기 위해 사용, 많이 사용하는 태그 중 하나 

(shift+tab 들여쓰기 없앰)

# 코드 블럭(Code Block)

일반 텍스트와 다르게 코드를 이쁘게 출력

 ```code block``` `3개

`inline code block` `1개

출력을 하는 파이썬 문법은 `print()`를 이용한다.

```python
def test():
    print("git")
```

- 사용하는 프로그램에 따라 특정 언어를 명시하면 구문 강조(Syntax Highlighting) 지원 (code block만!)

# 링크(link)

[string] (url)

string은 보여지는 부분, url은 연결할 곳을 나타냄

[Google](https://www.google.com)

- 다른 페이지로 이동하는 링크를 삽입
- 필요하다면 파일의 경로를 넣어 다운로드 가능한 링크로 만들 수 있음

# 이미지(image)

![string](img_url)

링크와 비슷하지만 이미지를 삽입

![고양이](test.assets/cat.jpg)

왜 test.assets을 만드는가? 한 곳에 모아두지 않으면 마크다운 파일을 옮길 때 참조하고 있는 이미지 파일 링크가 다 깨지게 될 수 있음 -> 마크다운 문서를 옮길 때 test.assets파일까지만 들고 옮기면 됨

- 이미지의 너비와 높이는 조절할 수 없음
- 조절이 필요하다면 HTML을 사용해야함

# 텍스트 강조 (Text Emphasis)

**Bold** *Italic* ~~strikeout~~

순서대로 굵게, 기울임, 취소선

- *를 _(underbar)로 대체 할 수 있다
- 취소선은 프로그램에 따라 없을 수도

# 수평선(horizontal line)

단락을 구분할 때 사용

---

- -(hypen)을 *나 _(underbar)로 대체 가능

- 3개 이상만 적으면 똑같이 작동

# 인용문 (Blockqoute)

> 인용문 >
>
> > 인용의 인용 >>

인용을 위한 단락을 생성 > >>

# 표 (Table)

typora에서 본문-표-표 삽입-열, 행 지정