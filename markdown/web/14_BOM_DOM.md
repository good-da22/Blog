## Window 객체

<br>

window 객체는 웹 브라우저에서 작동하는 JavaScript의 최상위 전역 객체

window 객체에는 브라우저와 관련된 여러 객체와 속성, 함수가 존재

JavaScript에서 기본으로 제공하는 프로퍼티와 함수도 포함 (ex. Number 객체, setInterval() 함수 등)

BOM(Browser Object Model)으로 불린다.

<br>

### window 객체 사용

<br>

#### alert, confirm, prompt

<br>

window 객체의 함수를 호출하면 브라우저에서 제공하는 창을 open

alert() : 브라우저의 알림 창

confirm() : 브라우저의 확인/취소 선택 창

prompt() : 브라우저의 입력 창

<br>

#### navigator

<br>

navigator 객체는 브라우저의 정보가 내장된 객체

navigator의 정보로 서로 다른 브라우저를 구분할 수 있으며, 브라우저 별로 다르게 처리 가능

HTML5에서는 위치 정보를 알려주는 역할 가능

<br>

#### location, history

<br>

location 객체를 이용하여 현재 페이지 주소(URL)와 관련된 정보들을 알 수 있다.

location.href : 프로퍼티에 값을 할당하지 않으면 현재 URL을 조회하고 값을 할당하면 할당된 URL로 페이지 이동

location.reload() : 현재 페이지를 새로고침

history 객체는 브라우저의 페이지 이력을 담는 객체

history.back() : 브라우저의 뒤로 가기 버튼과 같은 동작

history.forward() : 브라우저의 앞으로 가기 버튼과 같은 동작

<br>

### 새 창 열기

<br>

window 객체의 open() 함수를 사용하면 새 창을 열 수 있다.

window.open('페이지 URL', '창 이름', '특성', 히스토리 대체여부);

창 이름(string) : open 할 대상(_blank, _self 등) 지정 혹은 창의 이름

특성(string) : 새로 열릴 창의 너비, 높이 등의 특성 지정

히스토리 대체 여부(boolean) : 현재 페이지 히스토리에 덮어 쓸지 여부(true/false)

창 특성
- width : 픽셀, All, 창의 너비
- height : 픽셀, All, 창의 높이
- top : 픽셀, All, 창의 세로(y) 좌표 위치
- left : 픽셀, All, 창의 가로(x) 좌표 위치
- menubar : yes || no, IE, FireFox, Opera, 메뉴 표시줄
- status : yse | no, IE, FireFox, Opera, 상태 표시줄
- scrollbars : yse | no, IE, FireFox, Opera, 스크롤바
- toolbar : yse | no, IE, FireFox, 도구모음
- resizable : yse | no, IE 전용, 창 크기 조절 가능 여부
- location : yse | no, Opera 전용, 주소 입력란

<br>

#### 창 열고 닫기

<br>

이벤트를 이용하여 특정 시점에 창을 열 수 있다.

페이지 로딩 완료 후 새 창 열기, 클릭할 때 새 창 열기 등

window 객체의 close() 함수로 현재 창을 닫을 수 있다.

특히 브라우저에 내장된 창이 아닌 JavaScript로 자체 구현한 팝업에서 필요

<br>

#### 부모 창 컨트롤

<br>

window 객체의 opener 속성을 이용하면 부모 창(새 창을 연 창)을 컨트롤 가능

부모 창에 값 전달

부모 창을 새로 고침 하거나 페이지 이동

opener 객체는 부모 창의 window 객체

<br>

### window 객체 프로퍼티

<br>

window 객체는 웹 브라우저에서는 구동 되는 JavaScript 전역 객체

document 객체는 HTML 문서와 관련된 객체로 가장 많이 사용하는 객체

screen 객체는 화면의 가로, 세로 크기 정보를 알 수 있다.

pageYOffsets 등과 scroll() 함수를 이용하면 현재 화면의 크기를 계산하여 페이지 단위로 스크롤 제어가 가능

- self : 현재 창 자신, window와 같다.
- document : documnet 객체
- history : history 객체
- location : location 객체
- opener : open()으로 연릴 창에서 볼 때 자기를 연 창
- parent : 프레임에서 현재프레임의 상위프레임
- top : 현재프레임의 최상위프레임
- frames : 창안의 모든 프레임에 대한 배열 정보
- locationbar : location 바
- menubar : 창 메뉴바
  
- statusbar : 창의 상태 바
- toolbar : 창의 툴 바
- personalbar : 창의 퍼스널 바
- scrollbars : 창의 스크롤 바
- innerHeight : 창 표시 영역의 높이(픽셀, IE 지원 X)
- innerWidth : 창 표시 영역의 너비(픽셀, IE 지원 X)
- outerHeight : 창 바깥쪽 둘레의 높이(IE 지원 X)
- outerWidth : 창 바깥쪽 둘레의 너비(IE 지원 X)
- pageXOffset : 현재 나타나는 페이지의 x 위치(IE 지원 X)
- pageYOffset : 현재 나타나는 페이지의 y 위치(IE 지원 X)

<br>

### window 객체 함수

<br>

브라우저에서 버튼으로 제공하는 기능인 find, stop, print와 같은 함수 존재

move 함수로 현재 열려 있는 창의 위치를 이동 가능

resize 함수로 현재 열려 있는 창의 크기 조절

window 객체에는 브라우저와 관련된 함수 뿐만 아니라 순수 JavaScript에서 필요한 객체나 함수 존재

setTimeout() 함수와 setInterval() 함수로 함수를 특정 시간 후 혹은 특정 시간마다 호출 가능

eval() 함수는 문자열로 된 JavaScript 코드를 해석한 후 실행

- alert() : 경고용 대화 상자를 보여준다.
- confirm() : 확인, 취소를 선택할 수 있는 대화 상자를 보여줌
- prompt() : 입력창이 있는 대화 상자를 보여줌
- open() : 새로운 창을 오픈
- scroll() : 창을 스크롤
- find() : 창안에 지정된 문자열이 있는지 확인, 있으면 true, 없으면 false (IE 지원 X)
- stop() : 불러오기 중지 (IE 지원 X)
- print() : 화면에 있는 내용을 프린터로 출력
- moveBy() : 창을 상대적 좌표로 이동, 수평방향과 수직방향의 이동량을 픽셀로 지정
- moveTo() : 창을 절대적 좌표로 이동, 창의 왼쪽 상단 모서리를 기준으로 픽셀을 지정

- resizeBy() : 창의 크기를 상대적인 좌표로 재설정
- resizeTo() : 창의 크기를 절대적인 좌표로 재설정, 창 크기를 픽셀로 지정
- scrollBy() : 창을 상대적인 좌표로 스크롤, 창의 표시영역의 수평방향과 수직방향에 대해 픽셀로 지정
- scrollTo() : 창을 절대적인 좌표로 스크롤, 창의 왼쪽 상단 모서리를 기준으로 픽셀로 지정
- setTimeout() : 지정한 밀리초 시간이 흐른 후에 함수 호출
- clearTimeout() : setTimeout() 함수를 정지
- setInterval() : 지정한 밀리초 주기마다 함수를 반복적으로 호출
- clearInterval() : setInterval() 함수를 정지
- eval() : 문자열을 JavaScript 코드로 변환하여 실행

<br>

## DOM(Document Object Model)

<br>

DOM(Document Object Model)은 HTML과 XML문서의 구조를 정의하는 API 제공

DOM은 문서 요소 집합을 트리 형태의 계층 구조로 HTML을 표현

DOM으로 HTML 문서의 검색과 조작(추가, 수정, 삭제) 가능

HTML 계층 구조의 제일 위에는 document 노드

그 아래로 HTML 태그나 요소(element)들을 표현하는 노드와 문자열을 표현하는 노드 존재

document는 HTML 또는 XML 문서를 표현

HTMLDocument는 HTML 문서와 요소만을 표현

HTMLElement의 하위 타입은 HTML 단일 요소나 요소 집합의 속성에 해당하는 JavaScript 프로퍼티를 정의

Comment 노드는 HTML이나 XML의 주석을 표현

<br>

### 문서 객체 만들기

<br>

문서 객체는 text node를 갖는 객체와 갖지 않는 객체로 나뉜다.

- createElement(tagName) : element node를 생성
- createTextNode(text) : text node를 생성
- appendChild(node) : 객체에 node를 child로 추가

<br>

객체의 속성 설정

- setAttribute(name, value) : 객체의 속성을 지정, 웹 브라우저가 지원하지 않는 태그의 속성도 지정 가능
- getAtrrtibute(name) : 객체의 속성값을 가져옴

<br>

innerHTML & innerText

- innerHTML : 문자열을 HTML 태그로 삽입
- innerText : 문자열을 text node로 삽입

<br>

### 문서 객체 가져오기

<br>

객체 가져오기

- getElementById(id) : 태그의 id 속성이 id와 일치하는 element **객체** 얻기
- getElementsByClassName(classname) : 태그의 class 속성이 classname과 일치하는 element **배열** 얻기
- getElementsByTagName(tagname) : 태그이름이 tagname과 일치하는 element **배열** 얻기
- getElementsByName(name) : 태그의 name 속성이 name과 일치하는 element **배열** 얻기  

<br>

- querySelector(selector) : selector에 일치하는 첫 번째 element **객체** 얻기
- querySelectorAll(selector) : selector에 일치하는 모든 element **배열** 얻기

<br>

### 문서 객체 제거

<br>

객체 제거

- removeChild(childnode) : 객체의 자식 노드를 제거