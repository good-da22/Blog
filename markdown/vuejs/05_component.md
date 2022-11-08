## 컴포넌트(Component)

<br>

Vue의 가장 강력한 기능 중 하나

HTML element를 확장하여 재사용 가능한 코드를 캡슐화

Vue Component는 Vue Instance이기도 하기 때문에 모든 옵션 객체를 사용

Life Cycle Hook 사용 가능

전역 컴포넌트와 지역 컴포넌트, 상하관계 존재

<br>

### 전역 컴포넌트 등록

<br>

전역 컴포넌트를 등록하려면 `Vue.component(tagName, options)` 사용

권장하는 컴포넌트 이름 : 케밥 표기법(전부 소문자, - 사용)

```JavaScript
Vue.component('my-component', {
  // 옵션
})
```

<br>

### 지역 컴포넌트 등록

<br>

컴포넌트를 `components` 인스턴스 옵션으로 등록함으로써 다른 인스턴스 / 컴포넌트의 범위에서만 사용할 수 있는 컴포넌트를 만들 수 있다.

```JavaScript
var Child = {
  template: '<div>사용자 정의 컴포넌트 입니다!</div>'
}

new Vue({
  // ...
  components: {
    // <my-component> 는 상위 템플릿에서만 사용할 수 있습니다.
    'my-component': Child
  }
})
```

<br>

### Component data 함수

<br>

Vue Component 생성 시 `data`는 함수로 정의해야 한다.

```JavaScript
<div id="example-2">
  <simple-counter></simple-counter>
  <simple-counter></simple-counter>
  <simple-counter></simple-counter>
</div>

var data = { counter: 0 }

Vue.component('simple-counter', {
  template: '<button v-on:click="counter += 1">{{ counter }}</button>',
  // 데이터는 기술적으로 함수이므로 Vue는 따지지 않지만
  // 각 컴포넌트 인스턴스에 대해 같은 객체 참조를 반환합니다.
  data: function () {
    return data
  }
})

new Vue({
  el: '#example-2'
})
```

세 개의 컴포넌트가 모두 같은 `data`객체를 공유하고 있어 하나의 카운트를 증가 시키면 모두 증가한다.

새로운 데이터 객체를 반환하여 문제 해결

```JavaScript
data: function () {
  return {
    counter: 0
  }
}
```

<br>

## Component 통신

<br>

상위(부모) - 하위(자식) 컴포넌트 간의 data 전달 방법

부모에서 자식 : `props`라는 특별한 속성을 전달 ( Pass Props )

자식에서 부모 : `event`로만 전달 가능 ( Emit Event )

![](../img/../../img/inner%20ing/vue-component.png)

<br>

### 상위에서 하위 컴포넌트로 data 전달

<br>

하위 컴포넌트는 상위 컴포넌트의 값을 직접 참조 불가능

`data`와 마찬가지로 `props` 속성의 값을 `template`에서 사용이 가능

하위 컴포넌트는 `props` 옵션을 사용하여 수신 할 것으로 기대되는 `props`를 명시적으로 선언

```javascript
Vue.component('child', {
  // props 정의
  props: ['message'],
  // 데이터와 마찬가지로 prop은 템플릿 내부에서 사용할 수 있으며
  // vm의 this.message로 사용할 수 있습니다.
  template: '<span>{{ message }}</span>'
})

<child message="안녕하세요!"></child>
```

<br>

#### 렌더링 과정

1. `new Vue()`로 상위 컴포넌트인 인스턴스를 하나 생성
2. `Vue.component()`를 이용하여 하위 컴포넌트인 child-component를 생성
3. `<div id="app">` 내부에 `<child-component>`가 있기 때문에 하위 컴포넌트가 된다.
   
    처음 생성한 인스턴스 객체가 `#app`의 요소를 가지기 때문에 부모와 자식 관계가 성립한다.

4. 하위 컴포넌트에 `props` 속성을 정의 한다. `['propsdata']`
5. html에 컴포넌트 태그(child-component)를 추가
6. 하위 컴포넌트에 `v-bind` 속성을 사용하면 상위 컴포넌트의 `data`의 `key`에 접근이 가능하다. (message)
7. 상위 컴포넌트의 `message` 속성 값인 String 값이 하위 컴포넌트의 `propsdata`로 전달된다.
8. 하위 컴포넌트의 `template` 속성에 정의된 `<span>{{ propsdata }}</span>`에 전달된다.

<br>

#### 동적 props

`v-bind`를 사용하여 부모의 데이터에 `props`를 동적으로 바인딩 할 수 있다.

데이터가 상위에서 업데이트 될 때마다 하위 데이터로도 전달

```html
<div>
  <input v-model="parentMsg">
  <br>
  <child v-bind:my-message="parentMsg"></child>
</div>
```

`v-bind`에 대한 단축 구문을 사용하는 것이 더 간단하다.

```html
<child :my-message="parentMsg"></child>
```

<br>

#### 객체의 속성(properties) 전달 props

오브젝트의 모든 속성을 전달 할 경우, `v-bind:prop-name` 대신 `v-bind`만 작성함으로써 모든 속성을 `prop`으로 전달할 수 있다.

```javascript
todo: {
  text: 'Learn Vue',
  isComplete: false
}

<todo-item v-bind="todo"></todo-item>
```

위의 코드와 아래의 코드는 같은 동작

```html
<todo-item
  v-bind:text="todo.text"
  v-bind:is-complete="todo.isComplete"
>
</todo-item>
```

<br>

### 사용자 정의 이벤트 (Custom Events)

<br>

이벤트 이름
- 컴포넌트 및 `props`와는 달리, 이벤트는 자동 대소문자 변환을 제공하지 않는다.
- 대소문자를 혼용하는 대신에 `emit`할 정확한 이벤트 이름을 작성하는 것을 권장
- `v-on` 이벤트 리스너는 항상 자동으로 소문자 변환되기 때문에 `v-on:myEvent`는 자동으로 `v-on:myevent`로 변환된다.
- 이름이 `my-event`일 경우 `myEvent` 이벤트를 들을 수 없다.
- 이벤트 이름에는 **kebab-case** 사용을 권장

```javascript
// 이벤트 발생
vm.$emit("이벤트명", [...파라미터]);

// 이벤트 수신
vm.$on("이멘트명", 콜백함수(){});
```

<br>

### 하위에서 상위 컴포넌트로 event 전달

<br>

하위 컴포넌트에서 상위 컴포넌트가 지정한 이벤트를 발생 `$emit`

상위 컴포넌트는 하위 컴포넌트가 발생한 이벤트를 수신 `v-on` 하여 `data` 처리

```javascript
// 이벤트 발생
this.$emit("이벤트명");

// 이벤트 수신
<child v-on:이벤트명="상위 컴포넌트 메소드명"></child>
```

공식적으로 vue.js에서는 하위에서 상위로 data 전달 방법을 다루지 않는다. ( 단방향 통신에 어긋나기 때문 )

단, Event Bus를 이용하여 이벤트 인자로 data를 전달하는 방법이 존재

<br>

### 비 상하위간 통신

<br>

비어 있는 Vue Instance 객체를 Event Bus로 사용

복잡해질 경우 상태관리 라이브러리인 Vuex 사용 권장