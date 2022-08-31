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

page65