## Servlet

<br>

**자바 서블릿(Java Servlet)**은 자바를 사용하여 웹 피이지를 동적으로 생성하는 서버측 프로그램 혹은 그 사양을 말하며 **서블릿**으로 불린다.

웹 서버의 성능을 향상하기 위해 사용되는 자바 클래스의 일종

JSP와 비슷한 점이 있지만 JSP는 HTML 문서 안에 Java 코드를 포함

서블릿은 자바 코드 안에 HTML을 포함하는 차이점 존재

Web Brower(Client)에서 요청(request)를 받아 Web Application Server 안에서 작동

data를 얻고 Business logic 수행(JDBC를 사용하여 DB에 접근) 후 reponse page를 작성하여 응답(reponse)

<br>

### Servlet API

<br>

사용자 정의 서블릿의 상속 구조

![servlet](./../../img/inner%20ing/serveltAPI.png)

<br>

### Servlet Life-cycle

<br>

Servlet class는 javaSE에서의 class와 다르게 main method가 없다.

객체의 생성부터 사용(method call)의 주체가 사용자가 아닌 Servlet Container에게 있다.

Client가 요청(request)를 하게 되면 Servlet Container는 Servlet 객체를 생성(최초 한번만)하고, 초기화(최초한 번만)하여 요청에 대한 처리(요청시마다 반복)

Servlet 객체가 필요 없게 되면 제거하는 일까지 Container가 담당

<br>

#### Servlet Life-cycle 주요 method

<br>

request ->

(최초 요청 시 한번만 실행) Constructor ->

(최초 요청 시 한번만 실행) init() ->

(요청 시 마다 반복) service() / doGet() / doPost() -

(최초 요청 시 한번만 실행) destroy()

<br>

- init() : 서블릿이 메모리에 로드 될 때 한번 호출, 코드 수정으로 인해 다시 로드되면 다시 호출
- doGet() : GET 방식으로 data 전송 시 호출
- doPost() : POST 방식으로 data 전송 시 호출
- service() : 모든 요청은 service()를 통해서 do~() 메소드로 이동
- destroy() : 서블릿이 메모리에서 해제되면 호출, 코드가 수정되면 호출

<br>

### Servlet Parameter 처리

<br>

#### Parameter 전송 방식

- GET
    
    - 특징
  
        전송되는 데이터가 URL 뒤에 Quert String으로 전달

        입력 값이 적은 경우나 데이터가 노출되도 문제 없을 경우 사용

    - 장점

        간단한 데이터를 빠르게 전송

        form tag 뿐만 아니라 직접 URL에 입력하여 전송 가능

    - 단점

        데이터 양에 제한 존재

        location bar(URL + parameters)를 통해 전송할 수 있는 데이터 사이즈는 2KB(2048 byte)로 제한

- POST

    - 특징

        URL과 별도로 전송

        HTTP header 뒤 body에 입력 스트림 데이터로 전달

    - 장점

        데이터의 제한이 없다

        최소한의 보안 유지 효과

    - 단점

        전달 데이터의 양이 같을 경우 GET방식보다 느리다.

        전송 패킷을 body에 데이터로 구성해야하기 때문

<br>

#### URL / QuerySrting / Parameters

<br>

![QueryString](./../../img/inner%20ing/querystring.png)