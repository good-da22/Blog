## CSS

<br>

CSS(Cascading Style Sheets)란 HTML 문서를 화면에 표시하는 방식을 정의한 언어

W3C에서 공인한 표준

<br>

### CSS 규칙

<br>

**선택자(selector)** 와 **선언(declaration)** 두 부분으로 구성

선택자는 규칙이 적용되는 엘리먼트

선언 부분에서는 선택자에 적용될 스타일을 작성

선언은 중괄호로 감싸며, **속성(property)** 과 **값(value)** 로 구성

<br>

속성(property)은 선택자에서 바꾸고 싶은 요소 (ex. color, font, width, height...)

값(value)은 속성에 적용할 값

여러 선택자에 동일한 스타일을 적용할 때, comma(,)로 구분하여 나열(선택자 그룹화)

선언 안에 하나 이상의 속성을 작성할 수 있으며, 각 속성은 semi-colon(;)으로 구성

<br>

### CSS 적용 방법

<br>

**외부 스타일시트**, **내부 스타일시트**, **인라인 스타일** 3 가지로 분류

**외부 스타일시트(External Style Sheet)** 는 *.css 파일을 `<link>`나 `@import` 로 html 문서에 연결하여 사용

하나의 css 파일만 수정하면 해당 스타일시트를 사용하는 모든 페이지에 변경 내용 적용

세 가지 방법 중 가장 많이 사용

`<link rel="stylesheet" type="text/css" herf="path/filename.css">`

`<style type="text/css">@import url("path/filename.css");</style>`

<br>

**내부 스타일시트(Embedded Style Sheet)** 는 `<style>` 을 이용하여 html 페이지 내부에 css 적용

`<style>` 은 `<head>` 안에 작성

페이지 마다 반복해서 작성하는 단점이 존재

`<style type="text/css"> ...css작성... </style>`

<br>

**인라인 스타일(inline style)** 은 style attribute를 사용하여 개별 엘리먼트에 스타일 적용

style 속성의 값은 css 규칙의 선언(declaration)과 같다.

하나 이상의 속성을 적용할 수 있으며, semi-colon(;)으로 구분

세 가지 스타일을 모두 사용했을 때 가장 먼저 반영

`<tagname style="속성: 값;"></tagname>`