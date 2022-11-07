## Vue Instance

<br>

#### Vue method

Vue Instance는 생성과 관련된 data 및 method의 정의 가능

method안에서 data를 "this.데이터이름" 으로 접근 가능

<br>

#### Vue filter

뷰의 필터는 화면에 표시되는 텍스트의 형식을 쉽게 변환해주는 기능

filter를 이용하여 표현식에 새로운 결과 형식을 적용

전역 필터 (`Vue.filter()`)와 지역 필터 (`new Vue({ filters: { }})`) 사용 가능

중괄호 보간법 {{}} 또는 v-bind 속성에서 사용이 가능

```
{{ value | filter }}

v-bind:id="rawId | formatId"
```

<br>

#### Vue computed

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

#### Vue watch

Vue Instance의 특정 property가 변경될 때 실행할 콜백 함수 설정

computed는 종속된 data가 변경되었을 경우 그 data를 다시 계산하여 캐싱

watch의 경우 data가 변경되었을 경우 다른 data를 (변경하는) 작업

newValue, oldValue 이전 값과 현재 값 확인

<br>

### Vue event

<br>

DOM event를 청취하기 위해 **v-on** 디렉티브 사용

v-on 대신 @ 사용 가능

inline event handling

method를 이용한 event handling

<br>

#### Vue event 청취 : v-on

v-on directive를 사용하여 DOM 이벤트를 듣고 트리거 될 때 JavaScript를 실행할 수 있다.

<br>

#### method event handler

v-on에서 이벤트 발생시 처리해야 하는 method의 이름을 받아 처리 가능

괄호가 없을 경우 자동으로 이벤트 객체가 넘어간다.

<br>

#### inline method handler

메소드의 이름을 직접 바인딩 하는 대신 인라인 JavaScript 구문에 메소드를 사용할 수도 있다.

원래의 DOM 이벤트에 접근해야 하는 경우 특별한 $event 변수를 사용해 직접적인 명시로 메소드에 전달할 수도 있다.

<br>

#### 이벤트 수식어(Event Modifier)

method는 DOM의 이벤트를 처리하는 것 보다 data 처리를 위한 로직만 작업하는 것이 좋다.

page21