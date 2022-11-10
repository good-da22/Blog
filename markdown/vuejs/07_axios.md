## axios

<br>

### HTTP 통신 : axios

<br>

Vue에서 권고하는 HTTP 통신 라이브러리는 axios

**promise** 기반의 HTTP 통신 라이브러리이며 상대적으로 다른 HTTP 통신 라이브러리들에 비해 문서화가 잘되어 있고 API가 다양하다.

`axios.get(URL) // promise 객체를 return`, `then`, `catch` 사용 가능

[axios](https://github.com/axios/axios)

<br>

#### promise

promise란 서버에 데이터를 요청하여 받아오는 동작과 같은 비동기 로직 처리에 유용한 자바스크립트 라이브러리

자바스크립트는 단일 스레드로 코드를 처리하기 때문에 특정 로직의 처리가 끝날 때까지 기다려 주지 않는다.

따라서 데이터를 요청하고 받아올 때까지 기다렸다가 화면에 나타내는 로직을 실행해야 할 때 주로 promise를 활용한다.

그리고 데이터를 받아왔을 때 promise로 데이터를 화면에 표시하거나 연산을 수행하는 등 특정 로직을 수행한다.

page7
