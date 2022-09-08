## AJAX(Asynchronous Javascript And XML)

<br>

Ajax(Asynchronous Javascript And XML)은 언어나 프레임 워크가 아닌 구현하는 방식을 의미

AJax는 웹(Web)에서 화면을 갱신하지 한고 데이터를 서버로부터 가져와 처리하는 방법을 의미

JavaScript의 XMLHttpRequest(XHR) 객체로 데이터를 전달하고 **비동기 방식**으로 결과를 조회

화면 갱신이 없으므로 사용자 입장에서는 편리하지만, 동적으로 DOM을 구성해야 하므로 구현이 복잡

<br>

**일반 요청에 대한 응답**

data를 입력 후 event 발생

Ajax를 적용하지 않은 요청은 서버에서 data를 이용하여 logic 처리

logic 처리에 대한 결과에 따라 응답 page를 생성하고 client에 전송(화면 전환 발생)

<br>

**Ajax 요청에 대한 응답**

data를 입력 후 event 발생

Ajax를 적용하면 event 발생시 서버에서 요청을 처리한 후 text, XML 또는 JSON으로 응답

client(browser)에서는 이 응답 data를 이용하여 화면 전환없이 현재 페이지에서 동적으로 화면을 재구성

<br>

### 서버와 클라이언트의 상호작용

<br>

웹 화면을 구성하는 방식은 서버 중심의 상호작용 방식과 클라이언트 중심의 상호 작용 방식으로 구분

SSR - 모든 작업을 서버가 처리, html(응답 페이지)를 만들어서 전송

서버 중심의 개발방식은 화면 구성이 서버에서 이루어 진다. (프리젠테이션 영역의 JSP, PHP, ASP 등)

CSR- 화면을 만들기 위한 데이터만 만들어서 전송

클라이언트 중심의 개발방식은 클라이언트(웹 브라우저)에서 화면을 구성(주로 JavaScript)

Ajax는 클라이언트 중심의 개발 방식이며 비동기 요청보다는 동적 화면 구성이 관건

<br>

### AJAX 사용방식

<br>

#### XMLHttpRequest 이용 방식(Browser)

<br>

```javascript
// 비동기 통신을 위해 새로운 xmlhttp 요청 생성
const xhr = new XMLHttpRequest();
// 요청 method
const method = "GET";
// 파일 위치
const url = "data/user.json";
// 위의 method 와 url 로 비동기 요청 초기화
xhr.open(method, url);
// 요청 헤더 설정
xhr.setRequestHeader("Content-Type", "application/text");
// 요청 동작 설정
xhr.onreadystatechange = function () {
  if (xhr.readyState === xhr.DONE) {
    // 요청 상태가 OK 이면
    if (xhr.status === 200) {
        // 작업 수행
        xhr.responseText
        xhr.responseXML
        JSON.parse(xhr.responseText)
    }
  }
};
// 요청 보내기
xhr.send();
```
<br>

XMLHttpRequest는 자바스크립트가 AJAX 방식으로 통신할 때 사용하는 객체

XMLHttpRequest 객체는 AJAX 통신 시 전송방식, 경로, 서버로 전송할 data 등 전송 정보를 담는 역할

실제 서버와의 통신은 브라우저의 AJAX 엔진에서 수행

직접 자바스크립트로 AJAX를 프로그래밍할 경우 브라우저 별로 통신방식이 달라 코드가 복잡해진다.

<br>

**readyState**
- 0 : Uninitialized, 객체만 생성(open 메소드 호출 전)
- 1 : Loading, open 메소드 호출
- 2 : Loaded, send 메소드 호출, status의 헤더가 아직 도착하기 전 상태
- 3 : Interactive, 데이터의 일부를 받은 상태
- 4 : Completed, 데이터 전부를 받은 상태

<br>

**status**
- 200 : OK, 요청성공
- 403 : Forbiddeb, 접근 거부
- 404 : Not Found, 페이지 없음
- 500 : Internal Server Error, 서버 오류 발생

<br>

#### fetch() 이용 방식(Browser)

<br>

```javascript
fetch("URL 링크")
    .then((response) => {
        if(!response.ok) {
            throw new Error("400 또는 500 에러 발생!!!");
        }
        return response.json();
    })
    .then((result) => {
        // 작업 수행
        result
    })
    .catch(() => {
        // 에러 처리
    });
```

<br>

브라우저에서 fetch() 함수를 지원하기 이전에는 XMLHttpRequest를 이용하여 직접 HTTP 요청하고 응답을 직접 구현

복잡한 구현때문에 jQuery와 axios 등 라이브러리 사용

브라우저가 fetch() 함수를 지원하면서 라이브러리 없이도 간단히 구현 가능

<br>

fetch() 함수는 첫 번째 인자로 URL, 두 번째 인자로 options 객체를 받음

options에 아무것도 넘기지 않으면 요청은 GET 방식으로 진행되며 URL로부터 contents가 다운로드 된다.

실행 결과 promise 타입의 객체를 반환

반환된 promise 객체는 API 호출이 성공했을 경우 **응답객체(response)**를 resolve

실패했을 경우 **예외(error) 객체** 를 reject

<br>

응답 본문(data)를 받는 방법
- response.text() : 응답을 읽고 text를 반환
- response.json() : 응답을 JSON 형식으로 파싱
- response.formData() : 응답을 FormData 객체 형태로 반환
- response.blob() : 응답을 Blob 형태로 반환

<br>

POST로 사용하는 경우

method option : POST로 설정

headers option : Content-Type에 JSON 사용 여부 설정

body option : 요청 data 값을 JSON 형식으로 직렬화하여 설정

PUT 방식의 경우 method option만 PUT으로 수정하고 나머지는 거의 비슷하다.

<br>

#### 외부라이브러리 이용 방식 - jQuery

<br>

```javascript
$(function() {
    $.ajax({
        type: "GET/POST",
        url: "호출 URL",
        dataType: "xml/json",
        succes: function (result) {
            // TODO Action
        },
    });
});
```

<br>

#### 외부라이브러리 이용 방식 - axios

<br>

```javascript
axios
    .get("호출 URL")
    .then((result) => {
        // TODO Action
        result.data
    })
    .catch(() = > {
        // 에러 처리
    });
```

<br>

### GET 방식 vs POST 방식

<br>

#### GET 방식의 특징

<br>

URL에 변수(데이터)를 포함시켜 요청

데이터를 Header(헤더)에 포함시켜 요청

URL에 데이터가 노출되어 보안에 취약

전송하는 길이에 제한

캐싱(한 번 접근 후, 재 요청시 빠른 접근 위해 레지스터에 데이터 저장) 가능

<br>

#### POST 방식

<br>

URL에 변수(데이터)를 노출하지 않고 요청

데이터를 Body(바디)에 포함

URL에 데이터가 노출되지 않아서 기본 보안

전송하는 길이에 제한 없음

캐싱 불가

<br>

### 데이터 전송 형식

<br>

server와 client는 주고 받을 data의 형식을 맞춰야 함

대표적인 data 형식은 CSV, XML, JSON 등이 있다.

<br>

#### CSV (Comma Separated Values)

<br>

각 항목을 Comma(,)로 구분해 데이터를 표현하는 방법

다른 두 형식에 비해 굉장히 짧다. 많은 양의 데이터 전송 시 유리

각각의 데이터가 어떤 내용인지 파악하기 어렵다.

서버와 클라이언트가 완벽히 데이터 구조를 공유할 경우 사용 가능

data1,data2,...

<br>

#### XML (eXentsible Markup Language)

<br>

XML은 태그로 data를 표현

태그를 보면 각 data가 무엇을 의미하는지 파악 가능

태그에 사용자 정의 속성을 넣을 수 있어 복잡한 data 전달 가능

<br>

#### JSON (JavaScript Object Notation)

<br>

CSV와 XML의 단점을 극복한 형식

JavaScript에서 사용하는 객체의 형식으로 data를 표현

AJAX 사용시 거의 표준으로 사용되는 data 표현 방식

<br>

데이터를 주고 받을 때 쓸 수 있는 가장 간단한 파일 포맷

텍스트 기반으로 매우 가볍고 읽기 편하다.

key-value 쌍으로 구성되어 있다.

서버와 데이터를 주고 받을 때 직렬화(serialize), 역직렬화(deserialize)를 사용

프로그램 언어나 플랫폼에 상관없이 사용 가능

<br>

**직렬화(serialize)**
- 객체를 문자열로 변환하는 작업
- 통신을 할 때는 문자열로 직렬화하여 주고 받는 것이 안전하다.
- `JSON.stringfy(JSON Object)`

**역직렬화(desrialize)**
- 문자열을 객체로 변환하는 작업
- 서버로부터 받은 문자열은 객체로 역직렬화하여 사용
- `JSON.parse(JSON 형식 문자열)`