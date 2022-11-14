## binding

<br>

### class binding

element의 class와 style을 변경

`v-dind:class`는 조건에 따라 class를 적용할 수 있다.

`v-bind:class="{ active: boolean }"`

<br>

### Form Input Binding

<br>

`v-model` directive를 사용하여 `form input`과 `textarea element`에 양방향 데이터 바인딩을 생성할 수 있다.
- `text`와 `textarea` 태그는 `value` 속성과 `input` 이벤트를 사용한다.
- `checkbox`와 `radio` 태그는 `checked` 속성과 `change` 이벤트를 사용한다.
- `select` 태그는 `value`를 `prop`으로 `change`를 이벤트로 사용한다.

<br>

#### form - text, textarea

**문자열(text)**

```html
<input v-model="message" placeholder="여기를 수정해보세요">
<p>메시지: {{ message }}</p>
```

**여러 줄을 가진 문장(textarea)**

텍스트 영역의 보간(`<textarea>{{ text }}</textarea>`)은 작동하지 않는다.

`v-model`를 사용

```html
<span>여러 줄을 가지는 메시지:</span>
<p style="white-space: pre-line">{{ message }}</p>
<br>
<textarea v-model="message" placeholder="여러줄을 입력해보세요"></textarea>
```

<br>

#### form - checkbox

하나의 체크박스는 단일 boolean 값을 갖는다.

```JavaScript
<input type="checkbox" id="checkbox" v-model="checked">
<label for="checkbox">{{ checked }}</label>
```

여러 개의 체크박스는 같은 배열을 바인딩 할 수 있다.

배열의 값과 `checkbox`의 `value`속성이 같을 경우 체크 처리된다.

```JavaScript
<div id='example-3'>
  <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
  <label for="jack">Jack</label>
  <input type="checkbox" id="john" value="John" v-model="checkedNames">
  <label for="john">John</label>
  <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
  <label for="mike">Mike</label>
  <br>
  <span>체크한 이름: {{ checkedNames }}</span>
</div>

new Vue({
  el: '#example-3',
  data: {
    checkedNames: []
  }
})
```

<br>

#### form - radio

`radio`의 경우 선택된 항목의 `value` 속성의 값을 관리

```javascript
<input type="radio" id="one" value="One" v-model="picked">
<label for="one">One</label>
<br>
<input type="radio" id="two" value="Two" v-model="picked">
<label for="two">Two</label>
<br>
<span>선택: {{ picked }}</span>
```

<br>

#### form - select

`select`일 경우 선택된 항목의 `value` 속성의 값을 관리

`v-model` 표현식의 초기 값이 어떤 옵션에도 없으면 `<select>` element는 "선택없음" 상태로 렌더링

사용하지 않는 옵션에 빈 값을 넣는 것이 좋다.

```javascript
<select v-model="selected">
  <option disabled value="">Please select one</option>
  <option>A</option>
  <option>B</option>
  <option>C</option>
</select>
<span>선택함: {{ selected }}</span>

new Vue({
  el: '...',
  data: {
    selected: ''
  }
})
```

`v-for`를 이용한 동적 `option` 렌더링

```javascript
<select v-model="selected">
  <option v-for="option in options" v-bind:value="option.value">
    {{ option.text }}
  </option>
</select>
<span>Selected: {{ selected }}</span>

new Vue({
  el: '...',
  data: {
    selected: 'A',
    options: [
      { text: 'One', value: 'A' },
      { text: 'Two', value: 'B' },
      { text: 'Three', value: 'C' }
    ]
  }
})
```

<br>

#### form - 수식어(Modifiers)

##### `.lazy`

기본적으로 `v-model`은 각 입력 이벤트 후 입력과 데이터를 동기화

`.lazy` 수식어를 추가하여 `change` 이벤트 이후 동기화 할 수 있다.

```html
<!-- "input" 대신 "change" 이후에 동기화 -->
<input v-model.lazy="msg" >
```

<br>

##### `.number`

`v-model`이 관리하는 input에서 사용자 입력이 자동으로 숫자로 형변환 된다. 

```html
<input v-model.number="age" type="number">
```

`type="number"` 를 사용하는 경우에도 HTML 입력 엘리먼트의 값은 항상 문자열을 반환

`.number`를 통해 숫자로 형변환

숫자로 형변환 할 수 없는 입력일 경우 원본 문자열을 반환한다.

<br>

##### `.trim`

`v-model`이 관리하는 input에서 자동으로 trim(공백 제거)

```html
<input v-model.trim="msg">
```