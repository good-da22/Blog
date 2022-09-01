## HTML5 마크업 요소(Markup Elements)

<br>

### 여러 data 나열

<br>

#### dropdown

<br>

`<select>` 태그는 select box(dropdown)를 표시

`<option>` 태그는 select box에 포함될 항목들을 정의

selected 속성은 여러 개의 항목 중 선택된 항목을 표시

value 속성은 각 항목 값을 지정하기 위해 사용

사용자 입력이 아닌 여러 옵션 중에서 선택하는 목록

```html
<select 속성="속성값">
    <option value="값" [속성="속성값"]>내용1</option>
    <option value="값" [속성="속성값"]>내용2</option>
    ...
</select>
```

- `<select>` 속성
  - size : 화면에 표시될 dropdown 메뉴의 항목 개수 지정
  - multiple : 브라우저 화면에 여러 개의 옵션이 함께 표시되면서 ctrl 키를 누른 상태로 여러 항목을 선택(다중 선택)
  
<br>

- `<option>` 속성
  - value : 옵션을 선택했을 때 서버로 넘겨질 값을 지정
  - selected : 화면에 표시될 때 기본으로 선택되어 있는 옵션을 지정

<br>

`<optgroup>` : dropdown 목록에서 여러 항목들을 몇 가지 그룹으로 묶을 경우

label 속성을 이용하여 그룹의 제목을 지정

<br>

#### datalist

<br>

`<input>` 과 함께 사용하며 텍스트필드에 직접 값을 입력하는 것이 아니라 datalist의 선택 값이 텍스트 필드에 입력된다.

```html
<input type="text" list="datalist id">
<datalist id="datalist">
    <option>...</option>
    <option>...</option>
    ...
</datalist>
```

<br>

### 여러줄 입력 textarea

<br>

`<textarea>` 태그는 여러 줄을 입력할 수 있는 box를 표시

cols와 rows 속성은 text box의 크기를 지정

`<textarea></textarea>` 태그 사이 문자열은 text box에 표시

disabled 속성은 화면에 표시는 하지만 데이터를 수정할 수 없도록 비활성화 상태로 표시

<br>

### form control

<br>

#### button

<br>

`<button>` 태그의 type 속성은 버튼이 활성화 되었을 때 어떤 동작을 할지 지정, default는 **submit**

`<button [type="submit | reset | button"]>내용</button>`

input솨의 차이점은 `<button>`태그는 contents를 포함할 수 있기 때문에 아이콘 추가 가능, CSS를 이용하여 원하는 형태로 꾸밀 수 있다.

<br>

#### progress

<br>

작업의 진행 상태를 표시

작업의 시작을 0, 최종 완료를 최댓값으로 설정

`<progress value="값" [max="값"]></progress>`

- `<progress>` 속성
  - value
  
    작업 진행 상태를 나타내며 부동 소수점으로 표현
    
    0 보다 크거나 같고 max 값보다는 작거나 같아야 한다.

    만약 max 값이 지정되지 않았다면 1.0보다 작아야 한다

  - max
  
    작업이 완료되려먼 얼마나 많은 작업을 해야하는지 부동 소수점으로 표현

    0보다 커야한다.

<br>

#### meter

<br>

값이 차지하는 크기 표시

`<progress>`와 결과 화면은 비슷하지만 차이점은 `<progress>`는 작업의 진행 상황을 나타내는 반면, `<meter>`는 전체 크기 중에서 얼마나 차지하는지를 표현

`<meter value="값" [속성="속성값"]></meter>`

- `<meter>` 속성
  - min, max : 범위의 최솟값과 최댓값을 지정, 갑을 정하지 않으면 0과 1로 지정
  - value : 범위 내에서 차지하는 값
  - low : "이 정도면 낮다." 라고 할 정도의 값을 지정
  - high : "이 정도면 높다" 라고 할 정도의 값을 지정
  - optimum : "이 정도면 적당하다." 라고 할 정도의 값을 지정
    
    optimum 값이 high 값보다 크다면 value 값이 클수록 졸고 optimum 값이 low 값보다 작다면 값이 작을 수록 좋다.

<br>

### 공간 분할 태그

<br>

#### div & span

<br>

- `<div>`

    block 형식으로 공간을 분할, 웹 사이트의 layout(전체 틀)을 만들 때 사용

    div 태그를 사용하여 각각의 블록(공간)을 알맞게 배치하고 CSS를 활용하여 스타일 적용

- `<span>`

    inline 형식으로 공간을 분할

    `<div>` 와 `<p>` 태그와 함께 웹 페이지의 일부분에 스타일을 적용시키기 위해 사용

<br>

차이점

- div와 span을 여러 개를 만들어 나란히 나열했을 때

    div는 자동 줄 바꿈이 일어나면서 세로로 나열

    span은 줄 바꿈이 일어나지 않고 가로로 나열

- 동일한 문장을 감쌌을 때
  
    div는 박스 형태로 영역이 설정되고 그 안에 정렬

    span은 줄 단위로 영역이 설정되기 때문에 박스 형태가 아닌 텍스트가 노출되는 영역만 포함\

- margin 적용

    div의 margin은 4방향 모두 적용

    span의 margin은 양옆으로만 적용

<br>

#### block & inline 형식 태그

<br>

- block 형식 태그
  - div 태그
  - h1 ~ h6 태그
  - p 태그
  - 목록 태그
  - table 태그
  - form 태그

- inline 형식 태그
  - span 태그
  - a 태그
  - input 태그
  - 글자 형식 태그 