## Coikie & Session

<br>

저장공간, Session은 sever, Cookie는 browser

<br>

### http protocol 특징

<br>

client가 serer에 요청

server는 요청에 대한 처리 후 client에 응답

응답 후 연결 해제 >>> **stateless** : 이전 처리 결과를 기억하지 않고 상태가 없다.

- 지속적인 연결로 인한 자원낭비를 줄이기 위해 연결을 해제
- 그러나 client와 server가 연결 상태를 유지해야 하는 경우 문제 발생(ex. 로그인 정보)
- 즉, client 단위로 **상태 정보를 유지해야 하는 경우** Cookie와 Session이 사용 >> **statefull**


HTTP proticol의 특징(약점)을 보완하기 위해 사용

<br>

## Cookie

javax.servlet.http.Cookie

서버에서 사용자의 컴퓨터에 저장하는 정보파일(클라이언트에서 저장), 만료일자 이전까지 저장

헤더와 페이로드 중 헤더에 저장하여 이후 서버에 전송

사용자가 별도의 요청을 하지 않아도 브라우저는 request시 Request Header를 넣어 자동으로 서버에 전송

key와 value로 구성되며 String 형태

Browser 마다 저장되는 쿠키는 다르다. (서버는 Browser가 다르면 다른 사용자로 인식)

<br>

### Cookie 사용 목적

<br>

세션 관리 : 사용자 아이디, 접속 시간, 장바구니 등의 서버가 알아야 할 정보 저장

개인화 : 사용자마다 다르게 그 사람에 적절한 페이지를 보여줄 수 있다.

트래킹 : 사용자의 행동과 패턴을 분석하고 기록

<br>

### Cookie 사용 예시

<br>

ID 저장(자동 로그인)

일주일간 다시 보지 않음

최근 검색한 상품들을 광고에 추천

쇼핑몰 장바구니 기능...

<br>

### Cookie의 구성요소

이름 : 여러 개의 쿠키가 client의 컴퓨터에 저장되므로 각 쿠키를 구별하는 데 사용되는 이름

값 : 쿠키의 이름과 매핑되는 값

유효기간 : 쿠키의 유효기간

도메인 : 쿠키를 전송할 도메인

경로(path) : 쿠키를 전송할 요청 경로

<br>

### Cookie 동작 순서

<br>

Client가 페이지 요청

WAS는 Cookie 생성

HTTP Header에 Cookie를 넣어 응답

Browser는 넘겨받은 Cookie를 PC에 저장하고, 다시 WAS가 요청할 때 요청과 함께 Cookie를 전송

Browser가 종료되어도 Cookie의 만료기간이 남아 있다면, Clinet는 계속 보관

동일 사이트 재방문시 Client의 PC에 해당 Cookie가 있는 경우, 요청 페이지와 함께 Cookie 전송

<br>

### Cookie 특징

<br>

이름, 값, 만료일(저장 기간 설정), 경로 정보로 구성되어 있다.

클라이언트에 총 300개의 쿠키를 저장할 수 있다.

하나의 도메인 당 20개의 쿠키를 가질 수 있다.

하나의 쿠키는 4KB(4096byte)까지 저장 가능하다.

<br>

### Cookie 주요 기능

<br>

- 생성
    
    `Cookie cookie = new Cookie(String name, String value);`

- 값 변경 / 얻기
    
    `cookie.setValue(String value);` / `String value = cookie.getValue();`

- 사용 도메인 지정 / 얻기

    `cookie setDomain(String Domain);` / `String domain = cookie.getDomain();`

- 값 범위(경로) 지정 / 얻기

    `cookie setPath(String path);` / `String path = cookie.getPath();`

- cookie의 유효기간 지정 / 얻기

    `cookie setMaxAge(int expiry);` / `int expiry = cookie.getMaxAge();`

- cookie 삭제

    `cookie.setMaxAge(0);`

- 생성된 cookie를 client에 전송

    `response.addCookie(cookie);`

- client에 저장된 cookie 얻기

    `Cookie cookies[] = request.getCookies();`

<br>

## HttpSession

<br>

javax.servlet.http.HttpSession

방문자가 웹 서버에 접속해 있는 상태를 하나의 단위로 보고 그것을 세션이라 한다.

WAS의 memory에 Object의 형태로 저장

memory가 허용하는 용량까지 제한 없이 저장 가능

<br>

### session 사용 예시

<br>

site내에서 화면을 이동해도 로그인(사용자 정보)이 풀리지 않고 유지

장바구니

<br>

### session 동작 순서

<br>

클라이언트가 페이지 요청

서버는 접근한 클라이언트의 Request-Header 필드인 Cookie를 확인

클라이언트가 해당 session-id를 보냈는지 확인

session-id가 존재하지 않는다면, 서버는 session-id를 생성해 클라이언트에 돌려준다.

서버에서 클라이언트로 돌려준 session-id를 쿠키를 사용해 서버에 저장

쿠키 이름 : JSESSIONID(톰캣 컨테이너에서 세션을 유지하기 위해 발급하는 키)

클라이언트는 재 접속 시, 해당 쿠키(JSESSION)를 이용하여 session-id 값을 서버에 전달

<br>

### session 특징

<br>

웹 서버에 웹 컨테이너의 상태를 유지하기 위한 정보를 저장

웹 서버에 저장되는 쿠키(= 세션 쿠키)

브라우저를 닫거나, 서버에서 세션을 삭제 했을 때만 삭제된다, 쿠키보다 비교적 보안이 좋다.

저장 데이터에 제한이 없다.

각 클라이언트 고유 Session ID를 부여한다.

Session ID로 클라이언트를 구분하여 각 클라이언트 요구에 맞는 서비스를 제공

<br>

### session 설정

<br>

Browser 당 하나의 JSESSIONID를 할당 받음

아이디 또는 닉네임과 같이 로그인 했을 경우 자주 사용되는 정보를 session에 저장하면 DB에 접근할 필요 없이 효율적

<br>

### HttpSession 주요 기능

<br>

- 생성

    `HttpSession session = request.getSession();`

    `HttpSession session = request.getSession(false);`

- 값 저장

    `session.setAttribute(String name, Object value);`

- 값 얻기
    
    `Object obj = session.getAttribute(String name);`

- 값 제거

    `session.removeAttribute(String name); // 특정 이름의 속성제거`

    `session.invalidate(); // binding되어 있는 모든 속성 제거`

- 생성시간
    
    `long ct = session.getCreationTime();`

- 마지막 접근 시간

    `long lat = session.getLastAccessedTime();`

<br>

### Session & Cookie

<br>

- **Type**

    Session : javax.servlet.http.HttpSession (Interface)

    Cookie : javax.servlet.http.Cookie (Class)

- **저장 위치**

    Session : Server의 memory에 Object로 저장

    Cookie : Client 컴퓨터에 file로 저장 

- **저장 형식**

    Session : Object는 모두 가능(일반적으로 dto, List 등 저장)

    Cookie : file에 저장되기 때문에 String 형태

- **사용 예**

    Session : 로그인 시 사용자 정보, 장바구니 등

    Cookie : 최근 본 상품 목록, 아이디 저장(자동 로그인), 팝업 메뉴에서 '오늘 그만 보기' 등

- **용량 제한**

    Session : 알 수 없음(Client가 로그아웃 or 일정 시간 Session에 접근하지 않을 경우, 만료시간은 web.xml에 설정)

    Cookie : 쿠키 저장 시 설정(설정이 없을 경우 Brower 종료 시 만료)

- **공통**

    전역에서 저장하기 때문에 project내의 모든 JSP에서 사용 가능

    Map 형식으로 관리하기 때문에 key 값의 중복을 허용하지 않는다.

<br>

![Cookie](./../../img/inner%20ing/cookie.png)