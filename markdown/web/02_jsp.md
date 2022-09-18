## JSP (Java Server Page)

<br>

**자바 서버 페이지(Java Server Page, JSP)** 는 HTML 내 Java 코드를 삽입하여 웹 서버에서 동적으로 웹 페이지를 생성하여 웹 브라우저에 돌려주는 언어

JavaEE 스펙 중 일부로 웹 애플리케이션 서버(WAS)에서 동작

JSP는 실행 시 Java Servlet으로 변환된 후 실행, 서블릿과 거의 유사

서블릿과 달리 HTML 표준에 따라 작성되므로 웹 디자인에 편리

1999년 썬 마이크로시스템즈에 의해 배포, 이와 비슷한 구조로 PHP, ASP, ASP.NET 등이 있다.

아파치 스트럿츠, 자카르타 프로젝트의 JSTL 등 JSP 태그 라이브러리르 사용하는 경우 Java 코딩 없이 태그만으로 간략히 기술이 가능, 생산성 향상 가능

<br>

### JSP 동작 흐름

<br>

data를 얻고 Business logic 수행(JDBC를 사용하여 DB에 접근) 후 reponse page를 작성하여 응답(reponse)

최소 jsp 요청 시, jsp 파일 변경 시 -> jsp가 servlet으로 변경

1. Servlet java file로 변환
2. Servlet class compile
3. Servlet class를 메모리에 적재

servlet 변환 파일 위치

%workspace%\.metadata\.plugins\org.eclipse.wst.server.core\tmp0\work\Catalina\localhost\[project]\org\apache\jsp

<br>

### JSP 스크립팅 요소(JSP Scripting Element)

<br>

#### 선언(Declaration)

<br>

멤버변수 선언이나 메소드를 선언하는 영역

```jsp
<%! 멤버변수와 method 작성 %>
```

<br>

#### 스크립트릿(Scriptlet)

<br>

Client 요청 시 매번 호출 영역으로, Servlet으로 변환 시 service() method에 해당되는 영역

requeest, response에 관련된 코드 구현

```jsp
<% java code %>
```

<br>

#### 표현식(Expression)

<br>

데이터를 브라우저 출력할 때 사용

```jsp
<%= 문자열 %>
```

문자열 뒤에 세미콜론(;)은 작성하지 않는다.

```jsp
<%= 문자열 %> == <% out.print(문자열); %>
```

<br>

#### 주석(Comment)

<br>

코드 상에서 부가 설명을 작성

HTML 주석은 개발자 도구(f12)를 통해 확인 가능

JSP 주석은 외부에서 확인 불가

```jsp
<%-- 주석 --%>
```

<br>

### JSP 지시자(JSP Directive)

<br>

#### page Directive

<br>

컨테이너에게 현재 JSP 페이지를 어떻게 처리할 것인가에 대한 정보를 제공

```jsp
<%! page attr1="val1" attr2="val2" ... %>
```

**속성**
- language
    
    default : java
    
    스크립트에서 사용할 언어 지정

- info
    
    현재 JSP 페이지에 대한 설명

- contentType
  
    default : text/html;charset=ISO-8859-1
    
    브라우저로 내보내는 내용의 MIME 형식 지정 및 문자 집합 지정

- pageEncoding

    default : ISO-8859-1
    
    현재 JSP 페이지 문자집합 지정

- import

    현재 JSP 페이지에서 사용할 Java 패키지나 클래스를 지정

- session
    
    default : true
    
    세션의 사용 유무 설정

- errorPage
    
    에러가 발생할 때 대신 처리될 JSP 페이지 지정

- isErrorPage

    default : false
    
    현재 JSP 페이지가 에러 핸들링 하는 페이지인지 지정하는 요소

- buffer
    
    default : 8KB
    
    버퍼의 크기

- autoflush
    
    default : true
    
    버퍼의 내용을 자동으로 브라우저로 보낼 지에 대한 설정

- isThreadsafe 

    default : true
    
    현재 JSP 페이지가 멀티 쓰레드로 동작해도 안전한지 여부를 설정, false인 경우 JSP 페이지는 SingleThread로 서비스

- extends
    
    default : javax.servlet.jsp.HttpJspPage
    
    현재 JSP 페이지를 기본적인 클래스가 아닌 다른 클래스로부터 상속하도록 변경


<br>

#### include Directive

<br>

특정 jsp file을 페이지에 포함

여러 jsp페이지에서 반복적으로 사용되는 부분을 jsp file로 만든 후 반복 영역에 include 시켜 반복되는 코드를 줄일 수 있다.

```jsp
<%@ include file="/template/*.jsp" %>
```

<br>

#### taglib Directive

<br>

JSTL 또는 사용자에 의해서 만든 커스텀 태그(custom tag)를 이용할 때 사용

JSP 페이지 내에서 불필요한 자바 코드를 줄일 수 있다.

```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```

<br>

### JSP 기본 객체

<br>

- requset

    Type : javax.servlet.http.HttpServletRequest

    HTML 폼 요소의 선택 값 등 사용자 입력 정보를 읽어올 때 사용

- response

    Type : javx.servlet.http.HttpServletResponse

    사용자 요청에 대한 응답을 처리하기 위해 사용

- pageContext

    Type : javax.servlet.jsp.PageCotext

    각종 기본 객체를 얻거나 forward 및 include 기능을 활용할 때 사용

- session

    Type : javax.servlet.http.HttpSession

    클라이언트에 대한 세션 정보를 처리하기 위해 사용

    page directive의 session 속성을 false로 하면 내장 객체는 생성 불가

- application

    Type : javax.servlet.ServletConText

    웹 서버의 애플리케이션 처리와 관련된 정보를 레퍼런스하기 위해 사용

- out
  
    Type : javax.servlet.jsp.JspWriter

    사용자에게 전달하기 위한 output 스트림을 처리할 때 사용

- config

    Type : javax.servlet.ServletConfig

    현재 JSP에 대한 초기화 환경을 처리하기 위해 사용

- page

    Type : java.lang.Object

    현재 JSP 페이지에 대한 참조 변수에 해당됨

- exception

    Type : java.lang.Exception

    Error를 처리하는 JSP에서 isErrorPage 속성을 true로 설정하면 exception 내장 객체 사용 가능

    기본은 false로 설정

    전달되 오류 정보를 담고 있는 내장 객체

<br>

#### JSP 기본 객체의 영역(scope)

<br>

- pageContext

    하나의 JSP 페이지를 처리할 때 사용되는 영역

    한번의 클라이언트 요청에 대하여 하나의 JSP 페이지가 호출

    이때 단 한 개의 page 객체만 대응

    페이지 영역에서 저장한 값은 페이지를 벗어나면 사라진다.

    커스텀 태그에서 새로운 변수를 추가할 때 사용

- request

    하나의 HTTP 요청을 처리할 때 사용되는 영역

    웹 브라우저가 요청을 할 때마다 새로운 request 객체가 생성

    request 영역에 저장한 속성은 그 요청에 대한 응답이 완료되면 사라진다.

- session

    하나의 웹 브라우저와 관련된 영역

    같은 웹 브라우저 내에서 요청되는 페이지들은 같은 session들을 공유하게 된다.

    로그인 정보 등을 저장

- application

    하나의 웹 어플리케이션과 관련된 영역

    웹 어플리케이션당 1개의 application 객체가 생성

    같은 웹 어플리케이션에서 요청되는 페이지들은 같은 application 객체를 공유

<br>

#### JSP 기본 객체의 영역(scope) - 공통 method

<br>

servlet과 jsp페이지 간에 특정 정보를 주고 받거나 공유하기 위한 메소드 지원

- void setAttribute(String name, Object value)

    문자열 name 이름으로 Object형 데이터를 저장

    Object형으로 어떠한 Java 객체도 저장 가능

- Object getAttribute(String name)

    문자열 name에 해당하는 속성 값이 있다면 Object형태로 가져온다.

    없다면 null을 리턴

    리턴 값에 대한 적절한 형 변환이 필요

- Enumeration getAttributeNames()

    현재 객체에 저장된 속성들의 이름들을 Enumeration 형태로 가져온다.

- void removeAttribute(String name)

    문자열 name에 해당하는 속성들을 삭제

<br>

### Web Page 이동

<br>

#### forard(request, response)

<br>

사용 방법

```java
RequestDispatcher dispatcher = request.getRequestDispatcher(path);
dispatcher.forward(request, response);
```

이동 범위 : 동일 서버(project)내 경로

location bar : 기존 URL 유지(실제 이동되는 주소 확인 불가)

객체 : 기존 requset와 response가 그대로 전달

속도 : 비교적 빠름

데이터 유지 : request의 setAttribute(name, value)를 통해 전달

<br>

#### sendRedirect(location)

<br>

사용 방법

```java
response.sendRedirect(location);
```

이동 범위 : 동일 서버 포함 타 URL 가능

location bar : 이동하는 page로 변경

객체 : 기존의 requeset와 response는 소멸, 개로운 request와 response 생성

속도 : forward()에 비해 느림

데이터 유지 : request로는 data 저장 불가능, session이나 cookie를 이용