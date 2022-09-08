## 이벤트(Event)

<br>

웹 페이지에서 여러 종류의 상호작용이 있을 때 마다 이벤트가 발생

사용자가 마우스를 클릭했을 때, 키보드를 눌렀을 때 등, 다양한 종류의 이벤트가 존재

JavaScript를 사용하여 DOM에서 발생하는 이벤트를 감지하여 이벤트에 대응하는 여러 작업 수행

이벤트는 일반적으로 함수와 연결이 되고, 함수는 이벤트가 발생되기 전에는 실행되지 않다가 이벤트가 발생할 경우 실행

**이벤트 핸들러(Event Handler)** 또는 **이벤트 리스너(Event Listener)**라 하며 함수에 이벤트 발생시 실행해야 하는 코드 작성

**이벤트 발생 종류**
- 웹 페이지가 로딩되었을 때
- 페이지를 스크롤 했을 때
- 브라우저 창의 크기를 조절 했을 때
- 마우스를 클릭 했을 때
- 키보드로 키를 입력 했을 때
- form이 submit 되었을 때
- input의 내용이 변경 되었을 때
- 마우스를 움직여서 element를 이동할 때

<br>

### 마우스 이벤트

<br>

웹 초기에는 lad, click 등 소수의 이벤트만 사용

마우스 이벤트는 웹 어플리케이션에서 가장 많이 사용하는 이벤트

마우스 이벤트 핸들러에 전달되는 이벤트 객체에는 마우스 위치와 버튼 상태 등의 정보를 담고 있다.

- onclick : 마우스로 element를 클릭 했을 때 발생
- ondbclick : 마우스로 element를 더블 클릭 했을 때 발생
- onmouseup : 마우스로 element에서 마우스 버튼을 올렸을 때 발생
- onmousedown : 마우스로 element에서 마우스 버튼을 눌렀을 때 발생
- onmouseover : 마우스를 움직여서 element 밖에서 안으로 들어 올 때 발생
- onmouseout : 마우스를 움직여서 element 안에서 밖으로 나갈 때 발생
- onmousemove : 마우스를 움직일 때 발생

<br>

### 키보드 이벤트

<br>

키보드의 커서가 웹 브라우저에 나타나는 지점에서 키보드를 조작할 때 이벤트 발생

키보드 조작은 운영체제에 영향을 받으므로 특정 키가 이벤트 핸들러에게 전달되지 않을 수 있다.

키보드 커서가 나타내는 요소가 없다면 document에서 이벤트가 발생

- onkeypress : 키보드가 눌려 졌을 때 발생(ASCII)
- onkeydown : 키보드를 누르는 순간 발생(KeyCode)
- onkeyup : 키보드의 누르고 있던 키를 뗄 때 발생

<br>

### Frame(UI) 이벤트

Frame 관련 이벤트는 특정 DOM 문서에 관련된 이벤트가 아니라 Frame 자체에 대한 이벤트

Frame 이벤트 중에서는 load 이벤트가 가장 많이 사용

load는 문서 및 자원들이 모두 웹 브라우저에 탑재되면 이벤트를 수행

unload는 사용자가 브라우저를 떠날 때 이벤트가 발생하지만, 사용자가 브라우저를 떠나는 것을 막을 수는 없다.

- onload : document, image, frame 등이 모두 로딩 되었을 때 발생
- onabort : 이미지 등의 내용을 로딩하는 도중 취소 등으로 중단 되었을 대 발생
- onerror : 이미지 등의 내용을 로딩하는 중 오류가 발생 했을 때 발생
- onresize : document, element의 크기가 변경 되었을 경우 발생
- onscroll : document, element가 스크롤 되었을 때 발생
- onselect : 텍스트를 선택했을 때 발생

<br>

### 폼(form) 이벤트

<br>

form 관련 이벤트는 웹 초기부터 지원되어 여러 웹 브라우저에서 가장 안정적으로 동작하는 이벤트

자주 사용되는 이벤트로 form이 전송될 때에는 submit 이벤트가 발생

form을 초기화할 때는 reset 이벤트가 발생

submit과 reset은 이벤트 핸들러에서 취소할 수 있다.

- onsubmit : form이 전송될 때 발생
- onreset : 입력 form이 reset될 때 발생
- oninput : input 또는 textarea의 값이 변경 되었을 때 발생
- onchange : select box, check box, radio button의 상태가 변경 되었을 때 발생
- onfocus(focusin) : input과 같은 요소에 입력 포커스가 들어 올 때 발생
- onblur(focusout) : input과 같은 요소 등에서 입력 포커스가 다른 곳을 이동할 때 발생
- onselect : input, textarea에 입력 값 중 일부가 마우스 등으로 선택될 때 발생

<br>

### 이벤트 핸들러 등록

<br>

하나의 DOM 엘리먼트에 복수의 이벤트 핸들러 등록 가능

DOM에서 발생되는 이벤트에 대한 핸들러(리스너)를 등록하여 특정 이벤트에 대응하는 작업 가능

<br>

#### 인라인 이벤트 핸들러

<br>

이벤트를 감지하고 대응하는 작업을 등록하는 방법은 여러가지 제공

어떤 이벤트를 처리할 작업을 등록하는 것을 '이벤트 핸들러(혹은 리스너)를 등록한다.' 라고 표현

JavaScript의 초기에는 **HTML 요소의 내부에서 직업 이벤트 핸들러를 등록**

HTML 코드를 JavaScript 코드가 침범하는 문제 발생

여러 개의 함수를 한 번에 호출 가능

**CBD(Component Based Development)** 방식의 Angular / React/ Vue.js 와 같은 framwork / library에서는 인라인 방식으로 이벤트 처리

CBD에서는 html, css, js를 view의 구성 요소로만 본다.

<br>

#### 이벤트 핸들러 프로퍼티 방식

<br>

HTML에 직접 이벤트 핸들러를 등록하는 방법 대신 JavaScript에서 이벤트 핸들러를 등록하는 방법

JavaScript에서 이벤트 핸들러를 등록함으로써 HTML 코드와 JavaScript 코드를 분리

이벤트 대상이 되는 특정 DOM을 선택하고 이벤트 핸들러 등록

인라인 이벤트 핸들러 방식처럼 HTML과  JavaScript가 혼용되어 있는 문제를 해결 할 수 있는 방식

이벤트 핸들러 프로퍼티에 하나의 이벤트 핸들러만을 바인딩 할 수 있다는 단점 존재

<br>

#### addEventListener 메소드 방식

<br>

2000년에 발표된 DOM 레벨 2 이벤트 명세의 addEventListener(arg1, arg2[, arg3])를 이용하여 좀 더 세밀한 이벤트 제어가 간으

전달 인자의 첫 번째에는 이벤트 이름, 두 번째에는 이벤트 핸들러, 세 번째에는 캡쳐링 여부를 사용

첫 번째 전달인자의 이벤트 이름에는 'on'을 제거한 이벤트 이름을 사용

addEventListener 메소드를 이용하여 대상 DOM 요소에 이벤트를 바인딩하고 해당 이벤트가 발생했을 때 실행될 콜백 함수(이벤트 핸들러)를 지정

장점
- 하나의 이벤트에 대해 하나 이상의 이벤트 핸들러를 추가 가능
- 캡처링과 버블링 지원
- HTML 요소 뿐만 아니라 모든 DOM(HTML, XML, SVG)에 대해 동작

<br>

공통 로직(규칙)이 있는 경우, 공통 규칙에 해당하는 값을 상수로 만들고 functionname(arg) 함수 선언한 뒤 callback 함수 호출

두 번째 매개변수의 함수를 직접 호출할 경우 이벤트 발생 시까지 대기하지 않고 바로 실행

해결하기 위해 함수 호출이 아닌 함수 지정을 선택, 해결을 되지만 인자 전달 불가

이벤트 핸들러 내부에서 함수를 호출하는 방식으로 인수 전달 해결

<br>

### 버블링 & 캡쳐링

<br>

이벤트가 발생한 요소를 포함하는 부모 HTML로부터 이벤트 근원지인 자식요소까지 검사하는 것을 캡쳐링이라 한다.

이벤트 캡쳐링에서 캡쳐 속성의 이벤트 핸들러가 등록되어 있으면 수행

이벤트 발생 요소부터 요소를 포함하는 부모요소까지 올라가면서 이벤트를 검사하는 것을 이벤트 버블링이라 한다.

이벤트 버블링에서 버블 속성의 이벤트 핸들러가 등록되어 있으면 수행

<br><br>

## Web Storage

<br>

localStorage, sessionStorage 존재

키(key)와 값(value)을 하나의 세트로 저장

도메인과 브라우저별로 저장

값은 반드시 문자열로 저장

**공통 메소드와 프로퍼티**
- setItem(key, value) : key - value 를 쌍으로 저장
- getItem(key) - key에 해당하는 값을 리턴
- removeItem(key) - key에 해당하는 값을 삭제
- clear() : 모든 값 삭제
- key(index) : index에 해당하는 key
- length : 저장된 항목의 개수

<br>

### localStorage

<br>

데이터를 사용자 로컬에 보존하는 방식

데이터를 저장, 덮어쓰기, 삭제 등 조작 가능

자바스크립트로만 조작

모바일에서도 사용 가능

<br>

#### Cookie와의 차이점

<br>

유효 기간이 없고 영구적으로 이용 가능

5MB까지 사용 가능(쿠키는 4KB까지, 브라우저 별 상이)

쿠키와는 다르게 네트워크 요청 시 서버로 전송되지 않음

서버가 HTTP 헤더를 통해 스토리지 객체를 조작할 수 없음

Web Storage는 origin(프로토콜, 도메인, 포트)이 다르면 접근 불가

<br>

#### localStorage에 데이터 얻기

<br>

localStorage.KEY_NAME

localStorage["KEY_NAME"]

loaclStorage.getItem("KEY_NAME")

<br>

### sessionStorage

<br>

sessionStorage는 현재 떠 있는 탭에서만 유지(같은 페이지라도 탭이 다르면 다른 곳에 저장)

페이지 새로고침시에는 데이터 유지, 탭을 닫고 새로 열었을 경우 제거

<br>

#### localStorage vs sessionStorage

<br>

localStorage : 세션이 끊겨도 사용 가능

sessionStorage : 같은 세션만 사용 가능

sessionStorage의 경우에는 동일한 세션에서만 사용 가능하지만 localStorage는 세션이 끊기거나 동일한 세션이 아니더라도 사용 가능