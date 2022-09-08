## HTML

<br>

웹 페이지 문서 구조 담당

마크업 언어(markup language)로 웹 문서를 작성하며, tag를 사용하여 문서의 구조 등을 기술하는 언어

<br>

### tag와 속성

<br>

HTML 문서는 **tag**로 만들어진다.

시작 태그와 종료 태그 사이 바디가 없는 경우 시작 태그만 존재

HTML 문서의 전체 구성은 html, head, body tag로 구성

<br>

tag는 시작 tag와 종료 tag로 쌍을 이루거나 시작 tag만 존재하는 tag도 있다.

시작 tag `<tagname>` 와 종료 tag `</tagname>` 은 '/'로 구분하며 중첩되지 않도록 한다.

각각의 tag는 속성과 속성의 값이 존재

<br>

HTML tag에는 어느 tag에나 사용할 수 있는 **글로벌 속성(global attribute)** 이 있다.

- **class** : tag에 적용할 스타일의 이름을 지정
- **dir** : 내용의 텍스트 방향을 지정 왼쪽 맞춤(default, ltr), 오른쪽 맞춤(rtl)
- **id** : tag에 유일한 ID를 지정, 자바 스크립트에서 주로 사용
- **style** : 인라인 스타일을 적용하기 위해 사용
- **title** : tag에 추가 정보를 지정, tag에 마우스 포이터를 위치시킬 경우 title의 값을 표시

<br>

### 주석

<br>

주석의 내용은 브라우저에 출력되지 않는다.

HTML tag의 내용을 설명하기 위한 용도

`<!-- 주석 작성 -->`

<br>

### Root 요소

<br>

`<html>` tag는 HTML 문서 전체를 정의

**Head** `<head> ... </head>` 와 **Body** `<body> ... </body>` 로 구성

<br>

### Head 요소

<br>

#### 문서 머리글(head), 제목(title)

<br>

`<head>` 태그는 브라우저에게 HTML 문서의 head 부분임을 인식

`<title>`, `<meta>`, `<style>`, `<script>`, `<link>` 태그를 포함 가능

`<title>` 태그는 문서의 제목을 의미, 브라우저의 제목 표시줄에 태그 내용이 나타남

`<title>` 태그 이외의 다른 태그로 표현한 정보는 화면에 출력되지 않는다.

<br>

#### 메타 데이터(meta)

<br>

문서의 작성자, 날짜, 키워드 등 브라우저 본문에는 나타나지 않는 일반 정보를 표현

name과 content 속성을 이용하여 다양한 정보를 나타냄

http-equiv 속성을 이용하여 인코딩 설정 및 문서 이동, 새로 고침이 가능

cahrset 속성을 이용하여 문서의 인코딩 정보를 설정

```html
<meta name="name" content="value">
- name 속성 : description(문서 요약), keyword(검색어 입력, 콤마로 분리), author(제작자) 등

<meta name="description" content="문서 요약">
- 페이지 설명. 검색엔진 로봇이 수집

<meta name="keyword" content="키워드1, 키워드2, ..">
- 페이지의 키워드를 , 로 구분해서 나열, 검색엔진 로봇이 수집

<meta name="author" content="제작자">
- 페이지 제작자 정보

<meta http-equiv="refresh" content="30">
- http-equiv 속성: refresh(문서를 자동으로 업데이트), content-type(인코딩 설정) 등.

<meta charset="UTF-8">
- 인코딩 정보를 설정
```

<br>

### Body 요소

<br>

웹 브라우저에 보여질 문서의 내용을 작성

`<head>` 태그 다음에 위치하고 `<head>` 내부에 위치하는 태그와 `<html>` 을 제외한 모든 태그

id 속성을 이용하여 문서 내에서 태그를 유일하게 식별 가능 (id 속성은 중복 X)

중복 작성은 가능하지만 동작에서 논리적인 문제 발생

class 속성을 이용하여 여러 태그에 공통적인 특성(CSS) 부여(class 속성은 중복 O)

<br>

#### heading

<br>

문단의 제목을 지정할 때 사용, `<h1>` 부터 `<h6>` 까지 구분, 숫자가 커질수록 글자는 작아진다.

`<section>` 태그를 이용하면 같은 태그를 서로 다르게 표현

문서 구조를 `<section>` 태그를 이용하여 구분하면 각 문단의 제목을 하나의 태그로 작성 가능

동일한 `<h1>` 태그를 사용해도 `<section>` 으로 구분되는 문단의 제목을 단계별로 표현

<br>

### 특수문자

<br>

- `&nbsp;` : Non-breaking space(공백)
- `&lt;` : Less than <
- `gt;` : Greater than > 
- `&amp;` : Ampersand &
- `&quot;` : Quotation mark "
- `&copy;` : Copyright &copy;
- `&reg;` : registered trademark &reg;