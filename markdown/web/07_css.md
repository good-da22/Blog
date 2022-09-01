## CSS

<br>

웹 페이지 디자인 담당(표현)

Cascading Style Sheets의 약자

웹 문서의 내용과 상관 없이 디자인만 바꿀 수 있다.

다양한 기기에 맞게 탄력적으로 바뀌는 문서를 만들 수 있다.

[w3schools](http://www.w3schools.com/css/css_intro.asp)

웹 페이지를 표현하기 위한 스타일 규칙을 모아 놓은 문서

웹 브라우저 별 CSS3 지원

[테스트 사이트](http://css3test.com)

<br>

CSS 규칙은 선택자(selector)와 선언(declaration) 두 부분으로 구성

선택자는 규칙이 적용되는 엘리먼트

선언 부분에서는 선택자에 적용될 스타일을 작성

선언은 중괄호로 감싸며, 속성(property)과 값(value)로 이루어짐

속성(property)은 선택자에서 바꾸고 싶은 요소(color, font, width, height, border ...)

값(value)은 속성에 적용할 값

여러 선택자에 동일한 스타일을 적용할 때, comma(,)로 구분하여 나열(선택자 그룹화)

선언 안에 하나 이상의 속성을 작성할 수 있으며, 각 속성은 semi-colon(;)으로 구분

주석 `/*내용*/`

<br>

### 외부 스타일 시트 적용

<br>

`<link>`를 사용하여 외부 스타일 시트를 적용

`<link>`는 `<head>`안에 작성하며 rel, type, href 3가지 속성을 주로 사용

rel은 HTMl 페이지와 링크된 파일간의 관계를 의미

href는 CSS file 경로를 의미

`<link rel="stylesheet" type="text/css" href="filepath/*.css">`

<br>

`@import`를 통해 link와 달리 `<style>` 태그 안에 설정 가능, 이는 css 파일 내부에서도 사용가능하다는 뜻

`@import`는 스타일 시트 중 최상단에 위치해야 한다

`@import url("file path");` 또는 `@import "file path";` 형태로 사용

`<link>`와 달리 `<style>`의 media 속성을 통해 보여지는 미디어 타입을 설정

<br>

### 내부 스타일 시트 적용

<br>

`<style>` 을 사용하여 내부 스타일 시트를 적용

`<style>` 태그 내부에 CSS 규칙을 작성

외부 스타일 시트보다 우선 적용

`<head>` 태그 내부에 작성

<br>

### 인라인 스타일 적용

<br>

개별 elements 마다 스타일을 지정, 유지보수에 불리하다.

스타일 적용 우선순위는 **인라인 스타일 > 내부 스타일 시트 > 외부 스타일 시트** 순서

style 속성을 사용하고 속성값으로 CSS 규칙을 작성

<br>

### CSS 선택자

<br>

HTML 문서에서 CSS 규칙 적용 타겟이 되는 다양한 종류의 CSS 선택자(selector) 존재

일반 선택자는 전체 선택자, 타입 선택자, 클래스 선택자, ID 선택자로 분류

복합 선택자는 자식 선택자, 하위 선택자, 인접 형제 선택자, 일반 형제 선택자로 분류

그 외 가상 클래스 선택자, 가상 엘리먼트 선택자, 속성 선택자가 존재

- 일반 선택자
  - 전체 선택자
    
    HTML 문서 내 모든 element 선택

    `* {}`

  - 타입 선택자
    
    매칭되는 element 선택

    `E1, E2, E3 {}`

  - 클래스 선택자

    class 속성 값과 매칭되는 element 선택

    `.class-name {}`

  - ID 선택자
    
    id 속성 값과 매칭되는 element 선택

    `#id-name {}`

---

- 복합 선택자
  - 하위 선택자
  
    하위 element 선택

    `E1 E2 {}`

  - 자식 선택자

    직속 하위 element 선택

    `E1 > E2 {}`

  - 인접 형제 선택자

    인접 형제(sibling) 관계인 element 선택

    `E1 + E2 {}`

  - 일반 형제 선택자

    형제(sibling) 관계인 element 선택

    `E1 ~ E2 {}`

page118