## Ajax

<br>

Ajax(Asynchronous Javascript And XML)은 언어나 프레임 워크가 아닌 구현하는 방식을 의미

AJax는 웹(Web)에서 화면을 갱신하지 한고 데이터를 서버로부터 가져와 처리하는 방법을 의미

JavaScript의 XMLHttpRequest(XHR) 객체로 데이터를 전달하고 **비동기 방식**으로 결과를 조회

화면 갱신이 없으므로 사용자 입장에서는 편리하지만, 동적으로 DOM을 구성해야 하므로 구현이 복잡

<br>

**일반 요청에 대한 응답**

data를 입력 후 event 발생

Ajax를 적용하지 않은 요청은 서버에서 data를 이용하여 logic 처리

logic 처리에 대한 결과에 따라 응답 page를 생성하고  client에 전송(화면 전환 발생)

**Ajax 요청에 대한 응답**

data를 입력 후 event 발생

Ajax를 적용하면 event 발생시 서버에서 요청을 처리한 후 text, XML 또는 JSON으로 응답

client(browser)에서는 이 응답 data를 이용하여 화면 전환없이 현재 페이지에서 동적으로 화면을 재구성

<br>

### 서버와 클라이언트의 상호작용

ssr - 모든 작업을 서버가 처리, html(응답 페이지)를 만들어서 전송

csr - 화면을 만들기 위한 데이터만 만들어서 전송

page9

new XMLHttpRequesst() -> 서버 통신을 위한 객체
