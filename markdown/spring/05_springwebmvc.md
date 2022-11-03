## Spring Web MVC

<br>

### MVC(Model-View-Controller) Pattern

<br>

어플케이션의 확장을 위해 Model, View, Controller 세 가지 영역으로 분리

컴포넌트의 변경이 다른 영역 컴포넌트에 영향을 미치지 않음(유지보수 용이)

컴포넌트 간의 결합성이 낮아 프로그램 수정이 용이(확장성이 뛰어남)

장점
- 화면과 비즈니스 로직을 분리해서 작업 가능
- 영역별 개발로 인하여 확장성이 뛰어남
- 표준화된 커드를 사용하므로 공동작업이 용이하고 유지보수성이 좋음

단점
- 개발과정이 복잡해 초기 개발속도가 늦음
- 초보자가 이해하고 개발하기 다소 어려움

**Model**
- 어플리케이션 상태의 캡슐화
- 상태 쿼리에 대한 응답
- 어플리케이션의 기능표현
- 변경을 view에 통지

**View**
- 모델을 화면에 시각적으로 표현
- 모델에게 업데이트 요청
- 사용자의 입력을 컨트롤러에 전달
- 컨트롤러가 view를 선택하도록 허용

**Controller**
- 어플리케이션의 행위 정의
- 사용자 액션을 모델 업데이트와 mapping
- 응답에 대한 view 선택

<br>

### Spring Web MVC 요청 흐름

<br>

![](../../img/inner%20ing/mvc.png)

<br>

### Spring Web MVC 특징

<br>

Spring은 DI나 AOP 같은 기능 뿐만 아니라. Servlet 기반 WEB 개발을 위한 MVC Farmework를 제공

Spring MVC는 Model2 Achotecture와 Front Controller Patttern을 Framework 차원에서 제공

Spring MVC Framwork는 Spring을 기반으로 하고 있기 때문에 Spring이 제공하는 Transaction 처리나 DI 및 AOP 등을 손쉽게 사용

<br>

### Spring Web MVC 구성요소

<br>

**DispatcherServlet (Front Controller)**
- 모든 클라이언트의 요청을 전달 받음
- Controller에게 클라이언트의 요청을 전달하고, Controller가 리턴 한 결과값을 View에게 전달하여 알맞은 응답을 생성

**HandlerMapping**
- 클라이언트의 요청 URL을 어떤 Controller가 처리할지를 결정
- URL과 요청 정보를 기준으로 어떤 핸들러 객체를 사용할지 결정하는 객체, DispatcherServlet은 하나 이상의 핸들러 매핑을 가질 수 있음

**Controller**
- 클라이언트의 요청을 처리한 뒤, Model을 호출하고 그 결과를 DispatcherServlet에게 알려준다.

**ModelAndView**
- Controller가 처리한 데이터 및 화면에 대한 정보를 보유한 객체

**ViewResolver**
- Controller가 리턴한 뷰 이름을 기반으로 Controller의 처리 결과를 보여줄 View를 결정

**View**
- Controller의 처리결과를 보여줄 응답화면을 생성

<br>

### Spring Web MVC 실행 순서

<br>

1. DispatcherServlet이 요청을 수신
   - 단일 Front Controller Servlet
   - 요청을 수신하여 처리를 다른 컴포넌트에 위임
   - 어느 Controller에 요청을 전송할지 결정

2. DispatcherServlet은 Handler Mapping에 어는 Controller를 사용할 것인지 문의
   - URL과 Mapping

3. DispatcherServlet은 요청을 Controller에게 전송하고 Controller는 요청을 처리한 후 결과 리턴
   - Business Logic 수행 후 결과 정보(Model)가 생성되어 JSP와 같은 view에서 사용됨

4. ModelAndView Object에 수행결과가 포함되어 DispatcherServlet에 리턴

5. ModelAndView는 실제 JSP 정보를 갖고 있지 않으며, View Resolver가 논리적 이름을 실제 JSP이름으로 변환

6. View는 결과정보를 사용하여 화면을 표현

<br>

### Spring Web MVC 사용

<br>

web.xml에 DispatcherServlet 등록 및 Spring 설정파일 등록

설정 파일에 HandlerMapping 설정

Controller 구현 및 Context 설정 파일(servlet-context.xml)에 등록

Controller와 JSP의 연결을 위해 View Resolver 설정

JSP 코드 작성

좋은 디자인은 Controller가 많은 일을 하지 않고 Service에 처리를 위임

<br>

#### web.xml - DispatcherServlet 설정

`<init-param>`을 설정하지 않으면 `<servlet-name>-servlet.xml` file에서 applicationContext의 정보를 load

Spring Container는 설정파일의 내용을 읽고 ApplicationContext 객체를 생성

`<url-pattern>`은 DispatcherServlet이 처리하는 URL Mapping pattern을 정의

Servlet이므로 1개 이상의 DispatcherServlet 설정 가능

`<load-on-startup>1</load-on-startup>` 설정 시 WAS startup시 초기화 작업 진행

DispatcherServlet을 여러 개 설정가능

각 DispatcherServlet마다 각각의 ApplicationContext 생성

<br>

web.xml - 최상위 Root ContextLoader 설정

Context 설정 파일들을 로드하기 위해 web.xml 파일에 리스너 설정(ContextLoaderListener)

리스너 설정이 되면 /WEB-INF/spring/root-context.xml 파일을 읽어서 공통적으로 사용되는 최상위 Context를 생성

<br>

Application Context 분리

어플리케이션 레이어에 따라 어플리케이션 컨텍스트 분리

Security Layer - board-security.xml

Web Layer - board-servlet.xml

Service Layer - board-service.xml

Persistence Layer - board-dao.xml

<br>

### Spring Web Application 동작원리

<br>

1. 웹 어플리케이션이 실행되면 Tomcat(WAS)에 의해 web.xml이 loading
2. web.xml에 등록되어 있는 ContextLoaderListener (Java Class) 가 생성
   
   ContextLoaderListener class는 ServletContextListener interface를 구현하고 있으며, ApplicationContext를 생성하는 역할 수행

3. 생성된 ContextLoaderListener는 root-context.xml를 loading
4. root-context.xml에 등록되어 있는 Spring Container(ROOT)가 구동

   이 때 개발자가 작성한 Business Logic(Service)에 대한 부분과 Database Logic(DAO), VO 객체들이 생성

5. Client로 부터 요청(request)가 들어옴
6. DispatcherServlet(Servlet)이 생성
   
   DispatcherServlet은 FrontController의 역할을 수행

   Client로부터 요청 온 메시지를 분석하여 알맞은 PageController에게 전달하고 응답을 받아 요청에 따른 응답을 어떻게 할 지 결정

   실질적인 작업은 PageController에서 이루어 진다.

   이러한 클래스들을 HandlerMapping, ViewResolver Class라고 한다.

7. DispatcherServlet은 servlet-context.xml을 loading
8. 두 번째 Spring Container가 구동되며 응답에 맞는 PageController들이 동작

   이 때 첫 번째 Spring Container가 구동되면서 생성된 DAO, VO, Service 클래스들과 협업하여 알맞은 작업 처리