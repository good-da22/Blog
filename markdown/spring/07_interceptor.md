## Interceptor

<br>

### HandlerInterceptor를 통한 요청 가로채기

<br>

Controller가 요청을 처리하기 전/후 처리

로깅, 모니터링 정보 수집, 접근 제어 처리 등의 실제 Business Logic과는 분리되어 처리해야 하는 기능들을 넣고 싶을 때 유용

interceptor 여러 개 설정 가능, 순서 주의

<br>

#### HandlerInterceptor 제공 default method

- `boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler)`
  - fasle를 반환하면 request를 바로 종료

- `void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView)`
  - Controller 수행 후 호출

- `void afterCompletion(HttpServletRequest request, HttpServlet response, Object Handler, Exception ex)`
  - view를 통해 클라이언트에 응답을 전송한 뒤 실행

<br>

HandlerInterceptor 인터페이스 구현을 통해 사용

servlet-context.xml 파일에서 interceptor 설정을 통해 interceptor를 사용할 주소 mapping