## JSTL (JSP Standard Tag Library)

<br>

자바 서버 페이지 표준 태그 라이브러리(Java Server Pages Standard Tag Library, 이하 JSTL)은 Java EE 기반 웹 애플리케이션 개발 플랫폼을 위한 컨포넌트 모음

JSTL은 XML 데이터 처리와 조건문, 반복문, 국제화와 지역화 같은 일을 처리하기 위한 JSP 태그 라이브러리를 추가하여 JSP 사양을 확장

JSTL은 JSP 페이지 내에서 자바 코드를 바로 사용하지 않고 로직을 내장하는 효율적인 방법을 제공

표중화된 태그 셋을 사용하여 자바 코드가 들락거리는 것보다 더 코드의 유지보수와 응용 소프트웨어 코드와 사용자 인터페이스 간의 관심사의 분리로 이어지게 한다.

<br>

custom tag : 개발자가 직접 태그를 작성할 수 있는 기능을 제공

custom tag 중에서 많이 사용되는 것들을 모아서 JSTL이라는 규약을 만듦

논리적 판단, 반복문의 처리, 데이터베이스 등의 처리를 할 수 있다.

JSP 2.1 ~ JSP 2.2와 호환되는 JSTL 버전은 1.2

JSTL은 JSP 페이지에서 스크립트릿을 사용하지 않고 액션을 통해 간단하게 처리할 수 있는 방법을 제공

JSTL에는 다양한 액션이 있으며, EL과 함께 사용하여 코드를 간결하게 작성할 수 있다.

<br>

### JSTL Tag

<br>

Directive 선언 형식 : `<%@ taglib prefix="prefix" uri="uri" %>`

**library**

- **core**
  - prefix : c
  - function : 변수 지원, 흐름 제어, URL 처리
  - uri : http://java.sun.com/jsp/jstl/core

- XML
  - prefix : x
  - function : XML 코어, 흐름 제어, XMl 변환
  - uri : http://java.sun.com/jsp/jstl/xml

- 국제화
  - prefix : fmt
  - function : 지역, 메시지 형식, 숫자 및 날짜 형식
  - uri : http://java.sun.com/jsp/jstl/fmt

- database
  - prefix : sql
  - function : SQL
  - uri : http://java.sun.com/jsp/jstl/sql

- 함수
  - function : Collection, String 처리
  - uri : http://java.sun.com/jsp/jstl/functions

<br>

### JSTL - core tag

<br>

선언 : `<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>`

**function**

- 변수 지원
  - **set** : jsp page에서 사용할 변수 설정
  - remove : 설정한 변수를 제거

- 흐름 제어
  - **if** : 조건에 따른 코드 실행
  - **choose, when, otherwise** : 다중 조건을 처리할 때 사용(if ~ else if ~ else)
  - **forEach** : array나 collection의 각 항목을 처리할 때 사용
  - forTokens : 구분자로 분리된 각각의 토큰을 처리할 때 사용(StringTokenizer)

- URL 처리
  - import : URL을 사용하여 다른 자원의 결과를 삽입
  - redirect : 지정한 경로로 redirect
  - url : URL 작성

- 기타 태그
  - catch : Exception 처리에 사용
  - out : JspWriter에 내용을 처리한 후 출력

<br>

#### 변수 선언 : `<c:set>`

<br>

`<c:set>` 액션은 변수나 특정 객체의 프로퍼티에 값을 할당할 때 사용

value 속성의 값이나 액션의 Body content로 값을 설정

var 속성은 변수를 나타내며, 변수의 생존범위는 scope속성으로 설정 (page(default) | request | session | application)

특정 객체의 프로퍼티에 값을 할당할 때는 target 속성에 객체를 설정하고 property에 프로퍼티명을 설정

<br>

value 속성을 이용하여 생존범위 변수 값 할당

```jsp
<c:set value="value" var="varName" [scope="{page | request | session | application}"]/>
```

액션의 Body 컨텐츠를 사용하여 생존범위 변수 값 할당

```jsp
<c:set var="varName" [scope="{page | request | session | application}"]>
    body contents
</c:set>
```

value 속성을 이용하여 대상 객체의 프로퍼티 값 할당

```jsp
<c:set value="value" target="target" property="propertyName"/>
```

value 속성을 이용하여 생존범위 변수 값 할당

```jsp
<c:set target="target" property="propertyName">
    body contents
</c:set>
```

<br>

#### 예외 : `<c:catch>`

<br>

기본적으로 JSP 페이지는 예외가 발생하면 지정된 오류페이지를 통해 처리

`<c:catch>` 액션은 JSP 페이지에서 예외가 발생할 만한 코드를 오류페이지로 넘기지 않고 직접 처리할 때 사용

var 속성에는 발생한 예외를 담을 page 생존범위 변수를 지정

`<c:catch>`와 `<c:if>` 액션을 함께 사용하여 Java 코드의 try ~ catch 와 같은 기능 구현 가능

```jsp
<c:catch vat="exception"> 예외 발생 코드 </c:catch>

<c:if test="${exception != null}">
    예외 발생 ${exception.message}
</c:if>
```

<br>

#### 조건문 : `<c:if>` , `<c:choose>`, `<c:when>`, `<c:otherwise>`

<br>

`<c:if>` 액션은 test 속성에 지정된 표현식을 평가하여 결과가 true인 경우 액션의 body 컨텐츠를 수행

`<c:if>` 액션의 var 속성은 표현식의 평가 결과인 boolean 값을 담을 변수를 나타내며, 변수의 생존범위는 scope 속성으로 설정 

`<c:choose>`, `<c:when>`, `<c:otherwise>` 액션을 사용하면 if, else if, else 와 같이 처리 가능

`<c:if>` 액션 사용

```jsp
<c:if test="${expr}">
    표현식 결과가 true인 경우 수행
</c:if>

<c:if test="${expr}" var="varName">
    표현식 결과가 true인 경우 수행
</c:if>
```

`<c:choose>`, `<c:when>`, `<c:otherwise>` 액션 사용

```jsp
<c:choose>
    <c:when test="${expr}">
        if
    </c:when>

    <c:when test="${expr}">
        else if
    </c:when>

    <c:otherwise>
        else
    </c:otherwise>

</c:choose>
```

<br>

#### 반복문 : `<c:forEach>`

<br>

`<c:forEach>` 액션은 컬렉션에 있는 항목들에 대하여 액션의 body 컨텐츠를 반복하여 수행

컬렉션에는 Array, Collection, Map 또는 콤마로 분리된 문자열이 올 수 있다.

var 속성에는 반복에 대한 현재 항목을 담는 변수를 지정하고 items 속성은 반복할 항목들을 갖는 컬렉션을 지정

varStatus 속성에는 지정한 변수를 통해 현재의 반복 상태를 알 수 있다.

```jsp
<c:forEach var="var" items="${varIter}" varStatus="varSatus" begin="beginNumber" end="endNumber">
    ${varStatus.count}
    ${var.propertyName}
</c:forEach>
```