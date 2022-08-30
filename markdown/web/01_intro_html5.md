## HTML

<br>

HTML은 Hypertext Markup Language의 약자

1990년도 이후 웹(Web, World Wide Web)에서 사용하는 문서 양식

문서에 하이퍼텍스트, 표, 목록, 비디오 등을 포함할 수 있는 tag(Tag)를 사용

문서를 **Web Brower** 에 표현할 때 **tag** 를 사용(Markup 적용)

<br>

### HTML 개발 배경

<br>

다양한 플러그인들로 인한 Browser간의 부작용을 막기위해 개발

W3C에서 Web Application1.0을 HTML5로 수용

<br>

### 웹 표준

<br>

모든 브라우저에서 웹서비스가 정상적으로 보여질 수 있도록 하는 것

W3C(World Wide Web Consortium)에서 HTML5를 웹 표준으로 권고하고 웹 브라우저는 이를 따른다.

<br>

### HTML5 특징

<br>

별도의 플러그인 없이 멀티미디어 재생 가능

서버와 클라이언트 사이 소켓 통신 가능

Semantic tag 추가
- 검색엔진이 좀 더 빠르게 검색할 수 있도록 특정 tag에 의미를 부여\
  
<br>

### HTML 문서 구조

<br>

`<html>` 루트 태그

크게 head와 body로 구성

**시작 tag`<tagname>`** 와 **종료 tag`</tagname>`** 로 구성, tag 사이에는 내용을 정의

각 tag는 고유의 의미를 가지고 있으며 웹 브라우저는 태그가 가지는 의미에 따라 문서를 화면에 표시

<br>

### Web & HTML 작동원리

<br>

서버는 클라이언트의 요청 내용을 분석하여 결과값을 HTML로 전송

서버는 결과값을 전송한 후 클라이언트와 연결 종료

stateless 하다. 클라이언트의 상태를 계속 가지고 있을 수 없다.

클라이언트는 서버로부터 전달받은 HTML을 웹 브라우저에 표시

각 웹 브라우저는 브라우저 엔진이 내장 되어 있다. 해당 엔진이 tag를 해석하여 화면에 표현