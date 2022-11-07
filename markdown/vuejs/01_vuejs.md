## Vue.js

<br>

create by. Evan You

Google에서 Angular로 개발하다 가벼운 걸 만들어 보고 싶은 생각으로 시작한 개인 프로젝트

사용자 인터페이스를 만들기 위해 사용하는 오픈 소스 Progressive Framework

CDN, NPM, CLI 방식으로 installation

<br>

### Vue.js 특징

<br>

Approachable (접근성)

Versatile (유연성)

Performant (고성능)

<br>

### MVVM Pattern

<br>

Model + View + ViewModel

Model : 순수 자바스크립트 객체

View : 웹페이지의 DOM

ViewModel : Vue의 역할

기존에는 자바스크립트로 view에 해당하는 DOM에 접근하거나 수정하기 위해 jQuery와 같은 library 이용

Vue 는 View와 Model을 연결하고 자동으로 바인딩하므로 양방향 통신을 가능하게 한다.

![](../../img/inner%20ing/mvvm.png)

<br>

### MVC vs MVVM

<br>

![](../../img/inner%20ing/mvc_vs_mvvm.jpg)

<br>

### Vue Instance 생성

<br>

```
<script>
    new Vue({
        속성
    })
```

#### 속성

**el**
- Vue가 적용될 요소 지정
- CSS Selector or HTML Element

**data**
- Vue에서 사용되는 정보 저장
- 객체 또는 함수 형태

**template**
- 화면에 표시할 HTML, CSS 등의 마크업 요소를 정의하는 속성
- 뷰의 테이터 및 기타 속성들도 함계 화면에 그릴 수 있다.

**methods**
- 화면 로직 제어와 관계된 method를 정의하는 속성
- 마우스 클릭 이벤트 처리와 같이 화면의 전반적인 이벤트와 화면 동작과 관련된 로직을 추가

**created**
- 뷰 인스턴스가 생성되자 마자 실행할 로직을 정의, life cycle

<br>

### Vue Instance 유효범위

<br>

Vue Instance를 생성하면 특정 범위 안에서만 옵션 속성들이 적용

el 속성과 밀접한 관계

인스턴스가 화면에 적용되는 과정
1. 뷰 라이브러리 파일 로딩
2. 인스턴스 객체 생성(옵션 속성 포함)
3. 특정 화면 요소에 인스턴스를 붙임
4. 인스턴스 내용이 화면 요소로 변환
5. 변환된 화면 요소를 사용자가 최종 확인

Vue()로 인스턴스 생성

el 속성에 지정한 화면 요소(돔)에 인스턴스가 부착

el 속성에 인스턴스가 부착된 후 data 속성이 el 속성에 지정한 화면 요소와 그 이하 레벨의 화면 요소에 적용되어 값이 치환

<br>

### Vue Instance Life-Cycle

<br>

![](../../img/inner%20ing/vue-life-cycle.png)

<br>

Life Cycle은 크게 나누면 Instance의 **생성**, 생성된 Instance를 화면에 **부착**, 화면에 부착된 Instance의 내용이 **갱신**, Instance가 제거되는 **소멸**의 4단계로 나뉜다.

**Life Cycle Hooks**

**beforCreate**
- Vue Instance가 생성되고 각 정보의 설정 전에 호출
- DOM과 같은 화면요소에 접근 불가

**created**
- Vue Instance가 생성된 후 데이터들의 설정이 완료된 후 호출
- Instance가 화면에 부착하기 전이기 때문에 template 속성에 정의된 DOM 요소는 접근 불가
- 서버에 데이터를 요청(HTTP 통신)하여 받아오는 로직을 수행하기 적합

**beforeMount**
- 마운트가 시작되기 전에 호출

**mounted**
- 지정된 element에 Vue Instance 데이터가 마운트 된 후에 호출
- template 속성에 정의한 화면 요소에 접근할 수 있어 화면 요소를 제어하는 로직 수행

**beforeUpdate**
- 데이터가 변경될 때 virtual DOM 랜더링, 패치 되기 전에 호출

**updated**
- Vue에서 관리하는 데이터가 변경되어 DOM이 업데이트된 상태
- 데이터 변경 후 화면 요소 제어와 관련된 로직을 추가

**beforeDestroy**
- Vue Instance 가 제거되기 전에 호출

**destroyed**
- Vue Instance 가 제거된 후에 호출

<br>

### 보간법 interpolation

<br>

#### 문자열

데이터 바인딩의 가장 기본 형태는 "Mustache" 구문(이중 중괄호)을 사용한 텍스트 보간
- {{속성명}}

v-once 디렉티브를 사용하여 데이터 변경 시 업데이트 되지 않는 일회성 보간을 수행
- v-once

<br>

#### 원시 HTML

이중 중괄호(mustaches)는 HTML이 아닌 일반 텍스트로 데이터를 해석

실제 HTML을 출력하려면 v-html 디렉티브를 사용

<br>

#### JavaScript 표현식 사용

Vue.js는 모든 데이터 바인딩 내에서 JavaScript 표현식의 모든 기능을 지원

각 바인딩에 단일 표현식만 포함될 수 있다.(구문 사용 불가, 삼항 연산자 사용)

<br>

### Directive

<br>

디렉티브는 **v-** 접두사가 있는 특수 속성

디렉티브 속성 값은 단일 JavaScript 표현식이 된다.(v-for) 제외

디렉티브의 역할은 표현식의 값이 변경될 때 사이드 이펙트를 반응적으로 DOM에 적용

<br>

#### v-model

양방향 바인딩 처리를 위해서 사용(form의 input, textarea)

<br>

#### v-bind

엘리먼트의 속성과 바인딩 처리를 위해서 사용

약어로 ":"로 사용 가능

<br>

#### v-show

조건에 따라 엘리먼트를 화면에 렌더링

style의 display를 변경, false일 경우 display: none 적용

항상 렌더링 된다.

<br>

#### v-if, v-else-if, v-else

조건에 따라 엘리먼트를 화면에 렌더링

false일 경우 렌더링 자체가 되지 않는다. 엘리먼트 삭제

<br>

#### v-for

배열이나 객체의 반복에 사용

`v-for="요소변수 이름 in 배열"`

`v-for="(요소변수 이름, 인덱스)" in 배열"`

<br>

#### template

여러 개의 태그를 묶어서 처리해야 할 경우 template 사용

v-if, v-for, component등과 함께 많이 사용

<br>

#### v-cloak

Vue Instance가 준비될 때까지 mustache 바인딩을 숨기는데 사용

`[v-cloak]`, `{display: none;}`과 같은 CSS 규칙과 함께 사용

Vue Instance가 준비되면 v-cloak은 제거됨

<br>

### Vue method

<br>

Vue Instance는 생성과 관련된 data 및 method의 정의 가능

method안에서 data를 "this.데이터이름" 으로 접근 가능