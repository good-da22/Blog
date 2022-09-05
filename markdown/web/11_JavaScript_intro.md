## JavaScript

<br>

웹 페이지 이벤트 담당(동작)

JavaScript는 프로토타입 기반의 스크립트 프로그래밍 언어로 객체지향 개념을 지원한다.

웹 브라우저가 JavaScript를 HTML과 함께 다운로드하여 실행

웹 브라우저가 HTML 문서를 읽어 들이는 시점에 JavaScript Engine이 실행된다.

대부분의 JavaScript Engine은 ECMAScript 표준을 지원한다.

<br>

JavaScript는 HTML, CSS와 함께 웹을 구성하는 요소 중 하나로 웹 브라우저에서 동작하는 유일한 프로그래밍 언어

JavaScript는 개발자가 별도의 컴파일 작업을 수행하지 않는 인터프리터 언어

각 브라우저별 JavaScript 엔진(ex. Chrome의 V8 엔진...)은 인터프리터와 컴파일의 장점을 결합하여 비교적 처리 속도가 느린 인터프리터의 단점을 해결

명령형(imperative), 함수형(functional), 프로토타입 기반(prototype-based) 객체지향 프로그래밍을 지원하는 멀티 패러다임 프로그래밍 언어

<br>

웹 브라우저는 JavaScript를 HTML과 함께 다운로드하고, 브라우저의 JavaScript Engine이 JavaScript를 실행

JavaScript는 클래스가 존재하지 않는 프로토타입 기반의 객체지향 언어(Edition 6에서는 Class 개념 지원)

Netscape에서 처음 만들었으며, 이후 ECMA에서 ECMAScript라는 이름으로 표준화

각 브라우저에서는 ECMAScript 스펙을 준수하는 방식으로 JavaScript를 지원한다

<br>

### JavaScript 선언

<br>

HTML에서 JavaScript를 사용하려면 `<script>` 태그를 사용

`<script>` 태그는 **'src'**와 **'type'** 속성을 사용하여 JavaScript를 선언 (HTML5부터는 type 속성 생략 가능)

src 속성은 외부의 JavaScript 파일(*.js)을 HTML 문서에 포함할 때 사용하며, 생략할 수 있다.

type 속성은 미디어 타입을 지정할 때 사용. JavaScript 코드는 'text/javascript'로 지정

<br>

`<script>` 태그는 HTML 파일 내부의 `<head>`나 `<body>` 안 어느 곳에서나 선언 가능

하지만 `<body>` 안의 끝 부분에 `<script>` 태그를 둘 것을 권장함

`<head>` 안에 위치한 JavaScript는 브라우저의 각종 입/출력 발생 이전에 초기화 되므로 브라우저가 먼저 점검함

`<body>` 안에 위치하면 브라우저가 HTML부터 해석하여 화면에 그리기 때문에 사용자가 빠르다고 느낄 수 있음

웹 브라우저가 HTML 문서를 순차적으로 해석(parsing)하므로, script 위치에 따라 로드와 실행 시점이 달라진다.