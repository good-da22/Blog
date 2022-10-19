## AOP (Aspect Oriented Programming)

<br>

OOP(Object Oriented Programming)에서 모듈화의 핵심 단위는 클래스

AOP(Aspect Oriented Programming)에서 모듈화의 단위는 Aspect

Aspect는 여러 타입과 객체에 거쳐서 사용되는 기능(Cross Cutting(공통 관심사항), Core Concern(핵심 관심사항), 트랜잭션 관리 등)의 모듈화

Spring Framework 의 필수 요소는 아니지만, AOP 프레임워크는 Spring IoC를 보완

<br>

### AOP 용어

<br>

- Aspect
  - 여러 클래스에서 공통적으로 구현되는 관심사(Concern)의 모듈화

- JoinPoint
  - 메서드 실행이나 예외처리와 같은 프로그램 실행 중의 특정 지점, Spring에서는 메서드 실행을 의미

- Advice
  - 특정 JoinPoint에서 Aspect에 의해서 취해진 행동, Aroud, Before, After, AfterReturning, AfterThrowing 등 Advice 타입이 존재

- Pointcut
  - JoinPoint에서 Aspect를 적용하기 위한 조건 서술
  - Aspect는 지정한 pointcut에 일치하는 모든 JoinPoint에서 실행된다.

- Target 객체
  - 하나 이상의 Advice가 적용될 객체
  - Spring AOP는 Runtime Proxy를 사용하여 구현되므로 객체는 항상 Proxy 객체가 된다.

- AOP Proxy
  - AOP를 구현하기 위해 AOP 프레임워크에 의해 생성된 객체
  - Spring Framework에서 AOP Proxy는 JDK dynamic proxy 또는 CGLIB proxy이다.

- Weaving
  - Aspect를 다른 객체와 연결하여 Advice 객체를 생성
  - 런타임 또는 로딩 시 수행할 수 있지만 Spring AOP는 런타임에서 Weaving을 수행

<br>

### Spring AOP Proxy

<br>

실제 기능이 구현된 Target 객체를 호출하면, target이 호출이 되는 것이 아니라 advice가 적용된 Proxy 객체가 호출된다.

Spring AOP는 기본값으로 표준 JDK dynamic proxy를 사용

인터페이스를 구현한 클래스가 아닌 경우 CGLIB proxy를 사용

<br>

### Spring AOP

<br>

@AspectJ : 일반 Java 클래스를 Aspect로 선언하는 스타일

Spring AOP에서는 pointcut 구문 분석, 매핑을 위해서 AspectJ 라이브러리를 사용

AOP runtime은 순수 Spring AOP이며 AspectJ에 대한 종속성은 없다.

<br>

### Spring AOP - XML 방식

<br>

Aspect 선언
- @Aspect annotation 또는 XML bean 등록

Pointcut 선언
- pointcut은 어떤 joinpoint를 사용할지 결정, Spring AOP는 메서드 실행만 지원
- joinpoint에 대한 표현식, pointcut의 이름을 pointcut 선언 내용에 포함

<br>

### Spring AOP - Annotation 방식

<br>

@Aspectg 활성화 위해 XML에 `<aop:aspectj-autoproxy>` 선언

bean 등록을 위해 @Component annotation 사용

@Aspect annotation으로 해당 클래스가 Aspect임을 선언

@Pointcut annotation을 이용하여 Pointcut을 설정

이때, pointcut의 이름 설정은 @Pointcut annotation이 설정된 메서드의 이름, 해당 메서드는 void 유형의 body가 비어있는 메서드로 생성

advice type 지정을 위해 @Before, @After 등의 advice type annotation을 설정하고 인자로 pointcut 이름을 넣어준다.

<br>

### Advice Type

<br>

page16