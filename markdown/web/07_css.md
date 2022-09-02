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
  - 전체 선택자 (2)
    
    HTML 문서 내 모든 element 선택

    `* {}`

  - 타입 선택자 (1)
    
    매칭되는 element 선택

    `E1, E2, E3 {}`

  - 클래스 선택자 (1)

    class 속성 값과 매칭되는 element 선택

    `.class-name {}`

  - ID 선택자 (1)
    
    id 속성 값과 매칭되는 element 선택

    `#id-name {}`

---

- 복합 선택자
  - 하위 선택자 (1)
  
    하위 element 선택

    `E1 E2 {}`

  - 자식 선택자 (2)

    직속 하위 element 선택

    `E1 > E2 {}`

  - 인접 형제 선택자 (2)

    인접 형제(sibling) 관계인 element 선택

    `E1 + E2 {}`

  - 일반 형제 선택자 (3)

    형제(sibling) 관계인 element 선택

    `E1 ~ E2 {}`

<br>

#### 일반 선택자 요소

<br>

전체 선택자(Universal Selector) 사용법은 `* {}`

HTML 문서 내 모든 element를 선택

잘 사용되지 않으며  우선 순위가 가장 낮다.

일반 선택자의 우선 순위는 **전체 선택자 < 타입 선택자 < 클래스 선택자 < ID 선택자**

<br>

타입 선택자(Type Selector) 사용법은 `elementName {}`

태그 명을 이용해서 스타일을 적용할 태그를 선택

1개 이상의 HTML 엘리먼트를 사용할 수 있다.

여러 엘리먼트를 선택할 때에는 **컴마(,)**로 구분

<br>

클래스 선택자(Class Selector) 사용법은 `.class-name {}` 이다.

클래스 명은 공백 없이 대소문자 또는 Hypen(-), UnderScore(_)로 시작(기호나 숫자 시작 X)

HTML 문선에서 동일한 클래스 명을 중복해서 사용 가능(공통 속성 적용)

class 속성 값에 하나 이상의 클래스를 적용 가능(공백으로 구분)

<br>

ID 선택자(ID Selector) 사용법은 `#id-name {}` 이다.

HTML 문서에서 동일한 ID를 중복 사용할 수 없다. (Class와 달리 ID는 **유일**해야 함)

id 속성 값엔 1개의 id만 사용 가능

**일반 선택자 중 가장 우선순위가 높다**

<br>

#### 복합 선택자 요소

<br>

하위 선택자(Descentdant Selector) 사용법은 `element element {}` 이다.

하위 선택자는 1단계 하위 요소(child)와 2단계 이상 하위요소(descendant)에 모두 적용

자식 선택자(Child Selector) 사용법은 `element > element {}` 이다.

자식 선택자는 **1단계 하위 요소(child)에만** 적용

<br>

인접 형제 선택자(Adjacent Sibling Selector) 사용법은 `element + element {}` 이다.

형제(sibling) 관계인 엘리먼트가 여러 개 존재할 경우 **첫 번째 엘리먼트만** 선택

일반 형제 선택자(General Sibling Selector) 사용자는 `element ~ element {}` 이다.

형제(sibling) 관계인 엘리먼트가 여러 개 존재할 경우 **모든 엘리먼트** 선택

<br>

#### 가상 클래스 선택자 요소

<br>

가상 클래스 선택자(Pseudo-Classes Selector)는 User Agent가 제공하는 가상의 클래스를 지정

사용법은 `가상 클래스 {}` 이다.

- `:link` : 방문하지 않은 링크를 선택 (1)
- `:visited` : 방문한 링크를 선택 (1)
- `:hover` : 지정된 요소에 마우스가 올라간 경우 선택 (1)
- `:active` : 지정된 요소가 활성화 된 경우 선택 (1)
- `:focus` : 지정된 요소가 포커스를 가질 경우 선택 (2)
- `:first-child` : 지정된 요소 중 부모의 첫 번째 자식 선택 (2)
- `:last-child` : 지정된 요소 중 부모의 마지막 자식 선택 (3)
- `:nth-child(n)` : 지정된 요소 중 n 번째 자식 선택(n = 0, 1, ...) (3)
- `:enabled` : 지정된 요소 요소가 enabled인 경우 선택 (3)
- `:disabled` : 지정된 요소 요소가 disabled인 경우 선택 (3)
- `:checked` : 지정된 요소 요소가 checked인 경우 선택 (3)

<br>

#### 가상 엘리먼트 선택자 요소

<br>

가상 엘리먼트 선택자(Psuedo-Element Selector)는 보이지 않는 가상의 엘리먼트를 선택

사용법은 `::가상 엘리먼트 {}` 이다.

CSS1, CSS2 에서는 single colon(::) 사용했었다.

CSS3에선 가상 클래스ㅘ 가상 엘리먼트를 구별하기 위해 double colon(::)으로 대체

- `::after` : 지정된 요소 뒤에 content 추가(IE9.0 부터) (2)
- `::befor` : 지정된 요소 앞에 content 추가(IE9.0 부터) (2)
- `::first-letter` : 지정된 요소의 첫 번째 문자 선택(IE9.0 부터) (1)
- `::first-line` : 지정된 요소의 첫 번째 라인 선택(IE9.0 부터) (1)
- `::selection` : 사용자에 의해 선택된 요소(텍스트 드래그)의 위치 선택(IE9.0 부터) (3)

<br>

#### 속성 선택자 요소

<br>

특정한 속성을 가지거나 속성 값을 갖는 엘리먼트를 선택

Existence([]), Equality([=]), Space([~=]), Substring([*=]) 등이 있다.

속성 선택자를 사용하기 위해서는 HTML 문서를 작성할 때에 name, title 등의 속성값을 규칙적으로 정의

화면에 같은 분류의 많은 항목들을 일괄적으로 선택할 때 유용(ex. 특정이름을 갖는 체크박스)

- `[A]` : A 속성이 포함된 엘리먼트 선택 (2)
- `[A=V]` : A 속성 값이 V와 정확히 일치하는 엘리먼트 선택 (2)
- `[A~=V]` : A 속성 값이 V 단어(word)를 포함하는 엘리먼트 선택, space로 구분 (2)
- `[A^=V]` : A 속성 값이 V로 시작하는 엘리먼트 선택 (3)
- `[A*=V]` : A 속성 값이 V를 포함하는 엘리먼트 선택, V는 단어가 아니어도 된다. (3)
- `[A$=V]` : A 속성 값이 V로 끝나는 엘리먼트 선택 (3)
- `[A|=V]` : A 속성 값이 정확히 V이거나, V- (V Hyphen(-))로 시작하는 엘리먼트 선택 (2)

<br>

#### CSS 규칙 적용 우선순위

<br>

같은 엘리먼트에 두 개 이상의 CSS 규칙이 적용된 경우 **마지막 규칙, 구체적인 규칙, !important가 우선 적용**

CSS 규칙들 중 하단에 작성한 규칙이 마지막 규칙이다.

p {} 보단 p b {} 가 더 구체적이므로 p b {}가 적용된다.

속성 값 뒤에 !important를 작성하면, 같은 엘리먼트에 대해 보다 우선적으로 스타일 적용