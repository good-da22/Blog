## Spring Framwork

<br>

### Spring Framwork 등장 배경

<br>

기존 EJB(Enterprise JavaBean) 을 사용하여 애플리케이션 작성을 쉽게 할 수 있다.

Low Level의 트랜잭션이나 상태관리, 멀티 쓰레딩, 리소스 풀링과 같은 복잡한 Low Level의 API를 이해하지 못해도 애플리케이션 개발 가능

하지만 현실에서 반영이 어려움

코드 수정 후 반영하는 과정 자체가 번거롭다.

기능은 좋지만 복잡한 스펙으로 인한 개발 효율성 감소

애플리케이션 테스트를 위해선 반드시 EJB 서버가 필요

<br>

웹 사이트가 점점 커지면서 엔터프라이즈급의 서비스가 필요
- 세션빈에서 Transaction 관리 용이
- 로긴, 분산처리, 보안 등

자바 진영에서는 EJB가 엔터프라이즈급 서비스로 각광
- EJB 스펙에 정의된 인터페이스에 따라 코드를 작성, 기존에 작성된 POJO(Plain Old Java Object) 변경 필요
- 컨테이너에 배포해야 테스트 가능, 개발속도 저하
- 높은 난이도, 많은 설정
- EJB는 RMI를 기반으로 하는 서버, 무거운 Container

점차 POJO + 경량 프레임워크 사용 시작

POJO(Plain Old Java Object)
- 특정 프레임워크나 기술에 의존적이지 않은 자바 객체
- 특정 기술에 종속적이지 않기 때문에 생산성, 이식성 향상
- Plain : component interface를 상속받지 않는 특징(특정 framwork에 종속되지 않는다.)
- Old : EJB 이전의 Java class 의미

경량 프레임워크
- EJB가 제공하는 서비스를 지원할 수 있는 프레임워크 등장
- Hibernate, JDO, iBatis(MyBatis), Spring

POJO + Framework
- EJB서버와 같은 거창한 컨테이너 필요 없다.
- 오픈소스 프레임워크로 무료 사용
- 각종 기업용 어플리케이션 개발에 필요한 많은 라이브러리 지원
- 스프링 프레임워크는 모든 플랫폼에서 사용 가능
- 웹 분야 뿐만 아니라 어플리케이션 등 모든 분야에 적용 가능한 다양한 라이브러리

<br>

### Spring Framework

<br>

엔터프라이즈 급 애플리케이션을 만들기 위한 모든 기능을 종합적으로 제공하는 경량화 된 솔루션

JEE(Java Enterprise Edition)가 제공하는 다수의 기능을 지원, JEE를 대체하는 Framwork로 자리잡고 있다.

Spring Framework는 JEE가 제공하는 다양한 기능을 제공

DI(Dependency Injection)나 AOP(Aspect Oriented Programming)와 같은 기능도 제공

자바로 Enterprise Application을 만들 때 포괄적으로 사용하는 Programming 및 Configuration Model을 제공하는 Framework로 Application 수준의 인프라 스트럭쳐 제공

개발자가 복잡하고 실수하기 쉬운 Low Level에 신경 쓰지 않고 Business Logic 개발에 전념할 수 있도록 해준다.

<br>

### Spring Framework 구조

<br>

#### Spring 삼각형

<br>

Enterprise Application 개발 시 복잡함을 해결하는 Spring 핵심

- **POJO(Plain Old Java Object)**
  - 특정 환경이나 기술에 종속적이지 않은 객체지향 원리에 충실한 자바객체
  - 테스트하기 용이하며, 객체지향 설계를 자유롭게 적용 가능

- **PSA(Portable Service Abstraction)**
  - 환경과 세부기술의 변경과 관계없이 일관된 방식으로 기술에 접근할 수 있게 해주는 설계 원칙
  - 트랜잭션 추상화, OXM 추상화, 데이터 액세스의 Exception 변환기능 등 기술적인 복잡함은 추상화를 통해 Low Level의 기술 구현 부분과 기술을 사용하는 인터페이스로 분리
  - ex) 데이터베이스에 관계없이 동일하게 적용할 수 있는 트랜잭션 처리 방식

- **IoC / DI(Dependency Injection)**
  - DI는 유연하게 확장 가능한 객체를 만들어 두고 객체 간의 의존관계는 외부에서 다이나믹하게 설정

- **AOP(Aspect Oriented Programming)**
  - 관심사의 분리를 통해서 소프트웨어의 모듈성을 향상
  - 공동 모듈을 여러 코드에 쉽게 적용 가능

<br>

### Spring Framework 특징

<br>

**경량 컨테이너**

- 스프링은 자바 객체를 담고 있는 컨테이너
- 스프링 컨테이너는 이들 자바 객체의 생성과 소멸 같은 라이프사이클을 관리
- 언제든지 스프링 컨테이너로부터 필요한 객체를 가져와 사용 가능

**DI(Dependency Injection - 의존성 지원) 패턴 지원**

- 스프링은 설정 파일이나, 어노테이션을 통해서 객체 간의 의존 관계를 설정할 수 있다.
- 객체는 의존하고 있는 객체를 직접 생성하거나 검색할 필요가 없다.

**AOP(Aspect Oriented Programming - 관점 지향 프로그래밍) 지원**
- AOP는 문제를 바라보는 관점을 기준으로 프로그래밍하는 기법
- 문제를 해결하기 위한 핵심관심 사항과 전체에 적용되는 공통관심 사항을 기준으로 프로그래밍 하여 공통 모듈을 여러 코드에 쉽게 적용할 수 있도록 한다.
- 스프링은 자체적으로 프록시 기반의 AOP를 지원하므로 트랜잭션이나, 로깅, 보안과 같이 여러 모듈에서 공통으로 필요로 하지만 실제 모듈의 핵심이 아닌 기능들을 분리하여 각 모듈에 적용 가능

**POJO(Plain Old Java Object) 지원**
- 특정 인터페이스를 구현하거나 또는 클래스를 상속하지 않는 일반 자바 객체 지원
- 스프링 컨테이너에 저장되는 자바 객체는 특정한 인터페이스를 구현하거나, 클래스 상속 없이도 사용이 가능
- 일반적인 자바 객체를 칭하기 위한 별칭 개념

**IoC(Inversion of Control - 제어의 반전)**
- IoC는 스프링이 갖는 핵심 기능
- 자바의 객체 생성 및 의존관계에 있어 모든 제어권은 개발자에게 있었다.
- Servlet과 EJB가 등장하며 기존 제어권이 Servlet Container 및 EJB Container에게 넘어갔다.
- 모든 객체의 제어권이 넘어간 것이 아닌 Servlet, EJB에 대한 제어권을 제외한 나머지 객체 제어권은 개발자가 담당
- 스프링에서도 객체에 대한 생성과 생명주기릴 관리할 수 있는 기능을 제공, 이런 이유로 Spring Container 또는 IoC Container라고 부리기도 한다.

**트랜잭션 처리를 위한 일관된 방법을 제공**
- JDBC, JTA 또는 컨테이너가 제공하는 트랜잭션을 사용하든, 설정파일을 통해 트랜잭션 관련정보를 입력하기 때문에 트랜잭션 구현에 상관 없이 동일한 코드를 여러 환경에서 사용 가능

**영속성과 관련된 다양한 API 지원**
- 스프링은 JDBC를 비롯하여 iBatis, MyBatis, Hibernate, JPA 등 DB처리를 위한 널리 사용되는 라이브러리와 연동을 지원

**다양한 API에 대한 연동 지원**
- 스프링은 JMS, 메일, 스케쥴링 등 엔터프라이즈 어플리케이션 개발에 필요한 다양한 API를 설정 파일과 어노테이션을 통해서 손쉽게 사용할 수 있도록 지원

<br>

### Spring Framework Module

<br>

**Spring Core**
- Spring Framework의 핵심 기능을 제공, Core 컨터이너의 주요 컴포넌트는 Bean Factory이다.

**Spring Context**
- Spring을 컨테이너로 만든 것이 Spring Core의 Bean Factory라면, Spring을 Framework로 만든것이 Context module
- 국제화된 메시지, Application 생명주기 이벤트, 유효성 검증 등을 지원함으로써 Bean Factory의 개념을 확장

**Spring AOP**
- 설정 관리 기능을 통해 AOP 기능을 SPring Framework와 직접 통합 시킨다.

**Spring DAO**
- Spring JDBC DAO 추상 레이어는 다른 데이터베이스 벤더들의 예외 핸들링과 오류 메시지를 관리하는 중요한 예외계층을 제공

**Spring ORM**
- Spring Framework는 여러 ORM(Objecet Relational Mapping) Framework에 플러그인되어 Object Relational 툴(JDO, Hibernate, iBatis)을 제공

**Spring Web**
- Web Context module은 Application Context module 상위에 구현되어, Web 기반 Application에 context를 제공

**Spring Web MVC**
- Spring Framework는 자체적으로 MVC 프레임워크를 제공하고 있으며, 스프링만 사용해도 MVC 기반의 웹 어플리케이션을 어렵지 않게 개발 가능