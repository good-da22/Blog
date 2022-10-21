## Spring Web MVC

<br>

## Controller

<br>

`@Controller` 와 `@RequestMapping` 선언

스프링 4.2버전까지는 아래와 같은 방식으로 작성

`@RequestMapping(value = "URL", method = RequestMethod.GET or RequestMethod.POST)`

이후 버전에서는 `@GetMapping("URL")` 또는 `@PostMapping("URL")` 사용

Method 단위의 mapping이 가능

DefaultAnnotationHandlerMapping과 AnnotationHandlerAdapter를 사용함
- Spring 3.0부터는 기본 설정이므로 별도의 추가 없이 사용 가능

Controller Class는 Client의 요청을 처리

`@Controller` 선언
- Class 타입에 적용
- SPring 3.0부터는 `@Controller` 사용을 권장

Controller Class를 servlet-context.xml에 `<bean>` 등록

또는, Controller Class 자동 스캔

`<context:component-scan>` 선언

base-package내의 class 중 `@Controller` annotation이 적용된 클래스는 자동 스캔 대상이 된다.

`@GetMapping("URL")` 또는 `@PostMapping("URL")` 선언
- 요청 URL mapping 정보를 설정

Controller method의 HTTP method에 한정
- 같은 URL 요청에 대하여 HTTP method(GET, POST)에 따라 서로 다른 메소드를 mapping 할 수 있다.

mapping하지 않는 경우 HTTP ERROR 404 발생 가능

<br>

### Controller method의 parameter type

Controller method의 parameter로 다양한 Object를 받을 수 있음

- HttpServletRequest
- HttpServletResponse
- HttpSession
  - 필요시 Servlet API를 사용할 수 있음

- Java.util.Locale
  - 현재 요청에 대한 Locale

- InputStream, Reader
  - 요청 컨텐츠에 직접 접근할 때 사용

- OutputStream, Writer
  - 응답 컨텐츠를 생성할 때 사용

- @PathVariable annotation 적용 파라미터
  - URL 템플릿 변수에 접근할 때 사용

- @RequestParam annotation 적용 파라미터
  - HTTP 요청 파라미터를 매핑

- @RequestHeader annotation 적용 파라미터
  - HTTP 요청 헤더를 매핑

- @CookieValue annotation 적용 파라미터
  - HTTP 쿠키 매핑

- @RequestBody annotation 적용 파라미터
  - HTTP 요청의 body 내용에 접근할 때 사용

- Map, Model, ModelMap
  - view에 전달할 model data를 설정할 때 사용

- 커맨드 객체(DTO)
  - HTTP 요청 parameter를 저장한 객체
  - 기본적으로 클래스 이름을 모델명으로 사용
  - @ModelAttribute annotation 설정으로 모델명을 설정할 수 있음

- Errors, BindingResult
  - HTTP 요철 파라미터를 커맨드 객체에 저장한 결과
  - 커맨드 객체를 위한 파라미터 바로 다음에 위치

- SessionStatus
  - 폼 처리를 완료 했음을 처리하기 위해 사용
  - @SessionAttributes annotation을 명시한 session속성을 제거하도록 이벤트를 발생시킨다.

<br>

HTML form과 Command Object(DTO, VO ..)
- Spring MVC는 form에 입력한 data를 JavaBean 객체를 이용해서 전송할 수 있다.

View에서 Command 객체에 접근
- Command 객체는 자동으로 반환되는 Model에 추가된다.

@RequestBody parameter type
- HTTP 요청 body가 그대로 객체에 전달됨
- AnnotationMethodHandlerAdapter에는 HttpMessageConverter 타입의 메시지 변환기가 기본으로 여러 개 등록되어 있다.
- @RequestBody가 붙은 parameter가 있으면 해당 미디어 타입을 확인 후 처리 가능한 변환기(Converter)가 자동으로 객체로 변환시킨다.
- 주로 `@ResponseBody`와 함께 사용 -> **비동기 처리**

Servlet API 사용
- HttpSession의 생성을 직접 제어해야 하는 경우
- Controller가 Cookie를 생성해야 하는 경우
- Servlet API를 선호하는 경우
  - javax.servlet.ServletRequest / javax.servlet.http.HttpServletRequest
  - javax.servlet.ServletResponse / javax.servlet.http.HttpServletResponse
  - javax.servlet.http.HttpSession

<br>

### Controller Class에서 method의 return type 종류

<br>

- ModelAndView
  - model 정보 및 view 정보를 담고 있는 ModelAndView 객체

- Model
  - view에 전달할 객체 정보를 담고 있는 Model을 반환한다.
  - 이 때 view 이름은 요청 URL로부터 결정
  - RequestToViewNameTranslator

- Map
  - view에 전달 할 객체 정보를 담고 있는 Map을 반환한다.
  - 이 때 view 이름은 요청 URL로부터 결정
  - RequestToViewNameTranslator

- String
  - view의 이름을 반환한다.

- View
  - view 객체를 직접 리턴, 해당 view 객체를 이용해서 view를 생성한다.

- void
  - method가 ServletResponse나 HttpServletResponse 타입의 parameter를 갖는 경우 method가 직접 응답을 처리한다고 가정한다.
  - 그렇지 않을 경우 요청 URL로부터 결정된 View를 보여준다.
  - RequestToViewNameTranslator

- @ResponseBody Annotation 적용
  - method에서 @ResponseBody annotation이 적용된 경우, 리턴 객체를 HTTP 응답으로 전송한다.
  - HttpMessageConverter를 이용해서 객체를 HTTP 응답 스트림으로 변환한다.

<br>

## View

<br>

Controller에서는 처리 결과를 보여줄 View 이름이나 객체를 리턴하고, DispatcherServlet은 View 이름이나 View 객체를 이용하여 view 생성
- 명시적 지정
- 자동 지정

**ViewResolver** : 논리적 view와 실제 JSP 파일 mapping

servlet-context.xml 에서 InternalResourceViewResolver 설정

prefix + 논리 뷰 + suffix로 설정

**View 이름 명시적 지정**

ModelAndView와 String 리턴 타입

**View 자동 지정**

RequestToViewNameTranslator를 이용하여 URL로부터 view 이름을 결정

자동 지정 유형
- return type이 Model이나 Map인 경우
- return type이 void이면서 ServletResponse나 HttpServlerResponse 타입의 parameter가 없는 경우

**redirect view**

View 이름에 `redirect:` 접두어를 붙이면, 지정한 페이지로 redirect

<br>

## Model

<br>

### Model 생성

<br>

View에 전달하는 데이터
- @RequestMapping annotation이 적용된 method의 Map, Model, ModelMap
- @RequestMapping method가 return하는 ModelAndView
- @ModelAttribute annotation이 적용된 method가 return한 객체

Map, Model, ModelMap을 통한 설정
- method의 argument로 받는 방식

Model Interface의 주요 method
- `Model addAttribute(String name, Object value);`
- `Model addAttribute(Object value);`
- `Model addAllAttributes(Collection<?> values);`
- `Model addAllAttributes(Map<String, ?> attributes);`
- `Model mergeAttributes(Map<String, ?> arrtibutes);`
- `boolean containsAttribute(String name);`

ModelAndView를 통한 Model 설정
- Controller에서 처리결과를 보여줄 view와 view에 전달할 값(model)을 저장하는 용도로 사용
- `setViewName(String viewname);`
- `addObject(String name, Object value);`

@ModelAttribute annotation을 이용한 model data 처리
- @RequestMapping annotation이 적용되지 않은 별도 method로 모델이 추가될 객체를 생성

<br>

### 요청 URL 매칭

<br>

전체 경로와 Servlet 기반 경로 매칭
- DispatcherServlet은 DefaultAnnotationHandlerMapping Class를 기본으로 HandlerMapping 구현체로 사용
- Default로 Context 내의 경로가 아닌 Servlet 경로를 제외한 나머지 경로에 대해 mapping

Servlet 기반 경로 매칭
- Servlet 경로를 포함한 전체 경로를 이용해서 매칭하려는 경우
- @RequestMapping("/full path")
- `<property name="alwaysUseFullPath vlaue="true" />`

@PathVariable annotation을 이용한 URI 템플릿
- RESTfull 방식
- @RequestMapping annotation 값으로 **`{템플릿 변수}`** 를 사용
- @PathVariable annotation을 이용해서 **`{템플릿 변수}`** 와 동일한 이름을 갖는 parameter 추가

@ReqestMapping annotation 추가 설정
 - Ant 스타일의 URI 패턴 지원
 - `?` : 하나의 문자열과 대치
 - `*` : 하나 이상의 문자열과 대치
 - `**` : 하나 이상의 디렉토리와 대치