## Vue Instance

<br>

### Vue method

<br>

Vue Instance는 생성과 관련된 data 및 method의 정의 가능

method안에서 data를 `"this.데이터이름"` 으로 접근 가능

<br>

### Vue filter

<br>

뷰의 필터는 화면에 표시되는 텍스트의 형식을 쉽게 변환해주는 기능

filter를 이용하여 표현식에 새로운 결과 형식을 적용

전역 필터 (`Vue.filter()`)와 지역 필터 (`new Vue({ filters: { }})`) 사용 가능

중괄호 보간법 `{{}}` 또는 `v-bind` 속성에서 사용이 가능

```html
{{ value | filter }}

v-bind:id="rawId | formatId"
```

<br>

### Vue computed

<br>

특정 데이터의 변경사항을 실시간으로 처리

**캐싱**을 이용하여 **데이터의 변경이 없을 경우** 캐싱된 데이터를 반환

Setter와 Getter를 직접 지정할 수 있다.

따로 지정하지 않으면 default로 Getter

작성은 method 형태로 작성하지만 Vue에서 proxy 처리하여 property처럼 사용(하나의 값처럼 사용 가능)

**computed**
- Vue Instance가 생성될 때 data에서 해당하는 값을 받아 미리 계산하여 저장
- 메소드로 따지면 한 번만 실행하는 것과 같다.

**method**
- 해당 메소드를 사용하려고 할 때 마다 계산
- 사용횟수 만큼 실행

<br>

### Vue watch

<br>

Vue Instance의 특정 property가 변경될 때 실행할 콜백 함수 설정

computed는 종속된 data가 변경되었을 경우 그 data를 다시 계산하여 캐싱

watch의 경우 data가 변경되었을 경우 다른 data를 (변경하는) 작업

`newValue`, `oldValue` 이전 값과 현재 값 확인

<br>

### Vue event

<br>

DOM event를 청취하기 위해 **v-on** 디렉티브 사용

`v-on` 대신 `@` 사용 가능

inline event handling

method를 이용한 event handling

<br>

#### Vue event 청취 : v-on

`v-on `directive를 사용하여 DOM 이벤트를 듣고 트리거 될 때 JavaScript를 실행할 수 있다.

<br>

#### method event handler

`v-on`에서 이벤트 발생시 처리해야 하는 method의 이름을 받아 처리 가능

괄호가 없을 경우 자동으로 이벤트 객체가 넘어간다.

<br>

#### inline method handler

메소드의 이름을 직접 바인딩 하는 대신 인라인 JavaScript 구문에 메소드를 사용할 수도 있다.

원래의 DOM 이벤트에 접근해야 하는 경우 특별한 `$event` 변수를 사용해 직접적인 명시로 메소드에 전달할 수도 있다.

<br>

#### 이벤트 수식어(Event Modifier)

method는 DOM의 이벤트를 처리하는 것 보다 data 처리를 위한 로직만 작업하는 것이 좋다.

Vue는 `v-on` 이벤트에 이벤트 수식어를 제공한다.

수식어는 점으로 표시된 접미사

수식어는 체이닝이 가능하다.

단순히 수식어만 사용할 수 있다.

- `.prevent` : 이벤트 전파 중단
- `.stop` : 이벤트가 전파되는 것을 중단
- `.capture `: 이벤트 리스너를 추가할 때 캡쳐모드를 사용, 내부 엘리먼트를 대상으로 하는 이벤트가 해당 엘리먼트에서 처리되기 전에 현재 위치에서 처리
- `.self` : event.target이 엘리먼트 자체인 경우에만 처리, 자식 엘리먼트에서는 안된다.
- `.once` : 이벤트를 한 번만 실행
- `.passive` : 기본 이벤트를 취소할 수 없게 한다.

<br>

#### 키 수식어(Key Modifier)

Vue 는 키 이벤트를 수신할 때 `v-on`에 대한 키 수식어를 추가할 수 있다.

- `.enter` : 고유 키 값 13
- `.tab` : 고유 키 값 9
- `.delete` : 고유 키 값 8, delete와 backspace 키 모두 해당
- `.esc` : 고유 키 값 27
- `.space` : 고유 키 값 32
- `.up` : 고유 키 값 33
- `.down` : 고유 키 값 34
- `.left` : 고유 키 값 37
- `.right` : 고유 키 값 39

```html
<input @click.enter="...">
<input @click.ctrl.enter="...">
```

> 일부 키(.esc와 모든 화살표 키)는 IE9에서 일관성 없는 key 값을 가지고 있다. IE9를 지원해야하는 경우 내장 별칭이 선호 된다.

<br>

#### 시스템 수식어

- `.ctrl`
- `.alt`
- `.shift`
- `.meta` : 윈도우 키보드에서 windows 키, 맥 키보드에서 command 키

<br>

#### 마우스 버튼 수식어

- `.left` : 마우스 왼쪽 버튼
- `.right` : 마우스 오른쪽 버튼
- `.middle` : 마우스 가운데 휠 버튼

<br>

### ref, $refs

<br>

Vue에서는 `$ref` 속성을 이용해 DOM에 접근할 수 있다.

Vue의 가장 중요한 목적 중 하나는 개발자가 DOM을 다루지 않게 하는 것으로, 되도록 **`ref`를 사용하는 것을 피하는 것이 좋다.**