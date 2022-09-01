## HTML5 마크업 요소(Markup Elements)

<br>

### form control 요소

<br>

사용자로부터 데이터를 입력받아 서버에서 처리하기 위한 용도로 사용

사용자의 요청에 따라 서버는 HTML form을 전달(회원가입 양식, 검색 양식 등)

사용자는 HTML form에 적절한 데이터를 입력한 후 서버로 전송, submit

서버는 사용자의 요청을 분석한 후 데이터를 등록하거나, 원하는 데이터를 조회하여 결과를 반환

Request : 값을 전달, 서버에 요청

Response : 해당 서버로부터 값을 받음

<br>

사용자가 입력하기 위한 control 요소들은 모두 `<form>` 태그 하위에 위치해야 서버로 전송된다.

각 control 요소마다 텍스트 입력, 버튼 클릭 등 다양한 형식으로 입력을 받는다.

- `<form>` : 사용자에게 입력 받을 항목을 정의, form 태그 내부에 여러 개의 control 요소를 포함
- `<input>` : 텍스트 박스, 체크 박스, 라디오 버튼 등 사용자가 데이터를 입력할 수 있도록 한다.
- `<textarea>` : 여러 줄의 문자를 입력할 수 있도록 함
- `<button>` : 버튼을 표시
- `<select>` : select box(dropdown, combobox)를 표시
- `<optgroup>` : select box의 각 항목들을 그룹화
- `<option>` : select box의 각 항목들을 정의
- `<label>` : 마우스를 이용하여 `<input>` 항목을 선택 시 편리함을 제공, for 속성을 이용하여 다른 control 요소와 텍스트를 연결시켜서 더 편리하게 선택할 수 있도록 한다.
- `<fieldset>` : 입력 항복들을 그룹화
- `<legend>` : `<fieldset>`의 제목을 지정

<br>

#### form

<br>

사용자가 입력한 자료들을 어떤 방식으로 서버로 전달할 것인지 결정

서버에서 어떤 프로그램을 이용해 처리할 것인지 결정

`<form [속성="속성값"]> form control </form>`

속성
- **method** : 사용자가 입력한 내용을 서버 쪽 프로그램으로 어떻게 넘겨줄지 지정
    - GET
        
        default, 주소 표시줄에 사용자가 입력한 내용 표시
            
        256 ~ 2048bytes(길이 제한)의 데이터만 서버로 전송(길이 초과시 초과된 부분은 제외된다)
    - POST
    
        HTTP 메세지의 Body에 담아서 전송하기 때문에 전송 내용의 길이에 제한이 없다.

        사용자가 입력한 내용이 표시되지 않는다.
-  **name** : form의 이름을 지정, 한 문서 안에 여러 개의 `<form>` 태그가 있을 경우 구분자로 사용
- **action** : `<form>` 태그 안의 내용들을 처리해 줄 서버상의 프로그램 지정(URL)
- **target** : `<action>` 태그에서 지정한 스크립트 파일을 현재 창이 아닌 다른 위치에 열도록 지정
- **autocomplete** : 자동완성 기능, 기본값 on

<br>

#### label

<br>

form control에 레이블(텍스트)을 연결

`<label [속성="속성값"]>레이블<input...></label>`

`<label for="id 이름"><input id="id이름" [속성="속성값"]></label>`

<br>

### 사용자 입력을 위한 input

<br>

`<input>` 태그는 type 속성에 따라 여러 가지 형태로 화면에 표시

`<input type="유형" [속성="속성값"]>`

**id** 속성은 여러 번 사용된 폼 요소를 구분하기 위해 사용

id 속성 값은 최소한 한 개 이상의 문자여야 하며 공백은 허용하지 않는다.

같은 html document에서 id는 하나의 값만 가능하고, name은 중복이 허용된다.

<br>

#### type 속성

<br>

- text : 한 줄의 텍스트를 입력할 수 있는 텍스트 상자
- password : 비밀번호를 입력할 수 있는 필드(text가 '*'로 표시)
  - textfiedl에서 사용 가능한 속성 
    - name : textfield를 구별할 수 있도록 이름을 정함
    - size : textfield의 길이를 지정, 화면에 몇 글자가 보이도록 할 것인지 지정(글자수 제한 X)
    - value : textfield가 화면에 보일 때, textfield 부분에 표시될 내용
    - maxlength : textfield에 입력할 수 있는 최대 문자수 지정

- search : 검색 상자

  - 박스 오른쪽에 x가 있어 텍스트를 쉽게 지울 수 있다.

- tel : 전화번호를 입력할 수 있는 필드
- url : URL 주소를 입력할 수 있는 필드

  - 영문자와 마침표(.), 슬래시(/)로만 이루어진 텍스트. http://로 시작하는 사이트 주소 입력

- email : 메일 주소를 입력할 수 있는 필드
- datetime : 국제 표준시(UTC)로 설정된 날짜와 시간(년, 월, 일, 시, 분, 초, 분할 초)
- datetime-local : 사용자 지역을 기준으로 날짜와 시간(년, 월, 일, 시, 분, 초, 분할 초)
- date : 사용자 지역을 기준으로 날짜(년, 월, 일)
- month : 사용자 지역을 기준으로 날짜(년, 월)
- week : 사용자 지역을 기준으로 날짜(년, 주)
- time : 사용자 지역을 기준으로 시간(시, 분, 초, 분할 초)\
  - 날짜, 시간에서 공통으로 사용할 수 있는 속성
  - min : 날짜나 시간의 최솟값을 지정
  - max : 날짜나 시간의 최댓값을 지정
  - step : 스핀 박스의 화살표를 누를 때마다 날짜나 시간을 얼마나 조절할지 지정
  - value : 화면에 표시할 초기값 지정
- number : 숫자를 조절할 수 있는 화살표
  - 사용자가 입력한 내용을 숫자로 인식
  - 직접 숫자를 입력하거나 브라우저에 따라 스핀박스 표시
- range : 숫자를 조절할 수 있는 슬라이드 막대

  - number, range 필드에서 사용할 수 있는 속성 
    - min : 필드에 입력할 수 있는 최솟값을 지정 type="range" 일 때 기본 최솟값은 0
    - max : 필드에 입력할 수 있느 최댓값을 지정 type="range" 일 때 기본 최댓값은 100
    - step : 짝수나 홀수 등 특정 숫자로 제한하려 할 때 숫자 간격을 지정, 기본값은 1
    - value : 페이지 로딩 시 필드에 표시할 초기값
- color : 색상 표
  - 지원 브라우저 : 파이어폭스, 크롬, 오페라, 안드로이드 브라우저
  - 그 외 브라우저는 텍스트 필드로 표시 
- checkbox : 주어진 항목에서 2개 이상 선택 가능한 체크박스(다중선택)
  - name 속성의 값과는 상관없이 다중 선택 가능 
- radio : 주어진 항목에서 1개만 선택 가능한 라디오 버튼(단일선택)
  - name 속성의 값이 모두 일치해야 한다(name 속성이 같은 항목들 중 단일 선택) 
  - checkbox와 radio는 checked 속성으로 여러 개 항목 중 선택된 항목 표시
- file : 파일을 첨부할 수 있는 버튼
- submit : 서버 전송 버튼
  - 사용자가 입력한 form 정보를 서버로 전송
- image : submit + image
- reset : 리셋 버튼
  - input 요소에 입력한 모든 정보 초기화
- button : 기능이 없는 버튼
  - 자체 기능은 없으며 스크립트 함수와 연결해 사용
- hidden : 사용자에게는 보이지 않지만 서버로 넘겨지는 값을 설정

<br>

#### 속성

<br>

- autofocus

    페이지 로딩 후 폼의 요소 중에서 해당 요소에 마우스 커서 표시
    
    html5 이전에는 자바스크립트로 구현

- placeholder

    텍스트를 입력할 때 도움이 되도록 입력란에 적당한 힌트 내용 표시
    
    클릭 시 자동으로 내용 사라짐

- readonly

    입력란에 텍스트를 사용자가 직접 입력하지 못하기 읽기 전용으로 지정

    readonly, readonly="readonly", readonly="true"

- required

    form에 data를 입력한 후 submit 클릭 시 data를 서버로 전송하기 전 필수 입력 항목 체크

    required, required="required"

- min, max, step

    min, max는 해당 필드의 최대, 최소 값 지정

    step은 일정 간격 지정

    type이 date, datetime, datetime-local, month, week, time, number, range 에서 사용

- size, minlength, maxlength

    minlength, maxlength는 텍스트 입력 시 최소, 최대 길이 지정

    size는 화면에 보여지는 글자 길이 지정

- height, width

    type="image" 일 때 이미지의 너비와 높이를 지정

- list

    `<datalist>`에 미리 정의해 놓은 옵션 값을 `<input>` 안에 나열해 보여준다.

- multiple

    type="email" 이나 type="file" 일 때 두 개 이상의 값을 입력

    `<input>` 태그 안에 속성 이름만 표시