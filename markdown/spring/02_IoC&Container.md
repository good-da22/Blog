## Ioc & Container

<br>

## IoC (Inversion of Control, 제어의 역행)

<br>

객체지향 언어에서 Object간의 연결 관계를 런타임에 결정

객체 간의 관계가 느슨하게 연결됨(loose coupling)

IoC의 구현 방법 중 하나가 DI(Dependency Injection)

<br>

### IoC 유형

<br>

#### Dependency Lookup

컨테이너가 lookup context를 통해서 필요한 Resource나 Object를 얻는 방식

JNDI Lookup

JNDI 이외의 방법을 사용한다면 JNDI 관련 코드를 오브젝트 내에서 일일이 변경해주어야 한다.

Lookup 한 Object를 필요한 타입으로 Casting 필요

Naming Exception을 처리하기 위한 로직 필요

<br>

#### Dependency Injection

Object에 lookup 코드를 사용하지 않고 컨테이너가 직접 의존 구조를 Object에 설정할 수 있도록 지정해 주는 방식

Object가 컨테이너의 존재 여부를 알 필요가 없다.

Lookup 관련된 코드들이 Object 내에서 사라짐

Setter Injection, Contructor Injection, Method Injection

<br>

### IoC 개념

<br>

**객체 제어 방식**
- 기존 : 필요한 위치에서 개발자가 필요한 객체 생성 로직 구현
- IoC : 객체 생성을 Container에게 위임하여 처리

**IoC 사용에 따른 장점**
- 객체 간의 결합도를 떨어뜨린다.(loose coupling)
- 객체간 결합도가 높으면 해당 클래스가 유지보수 될 때 그 클래스와 결합된 다른 클래스도 같이 유지보수 되어야 할 가능성이 높다.

<br>

**객체 간 강한 결합**
- 클래스 호출 방식
- 클래스내에 선언과 구현이 모두 되어 있기 때문에 다양한 형태로 변화가 불가능
- 클래스가 다른 클래스를 생성, 사용, 호출

**객체간의 강한 결합을 다형성을 통해 결합도를 낮춤**
- 인터페이스 호출 방식
- 구현 클래스 교체가 용이하여 다양한 형태로 변화 가능
- 인터페시읏 교체 시 호출 클래스도 수정해야 한다.
- 클래스가 인터페이스를 통해 해당 인터페이스를 구현한 클래스를 생성, 호출

**객체 간의 강한 결합을 Factory를 통해 결합도를 낮춤**
- 팩토리 호출 발식
- 팩토리 방식은 팩토리가 구현 클래스를 생성하므로 클래스는 팩토리를 호출
- 인터페이스 변경 시 팩토리만 수정, 호출 클래스에는 영향을 미치지 않는다.
- 하지만 클래스에 팩토리 호출하는 소스 필요, 이 자체가 팩토리에 의존함을 의미한다.
- 클래스는 팩토리 호출을 통해 팩토리 내에서 인터페이스를 구현한 클래스를 사용
- 인터페이스만 알고 있으면 어떤 구현체가 어떻게 생성되는지에 대해서는 알 필요 없다.
- Factory 패턴이 적용된 것이 Container의 기능이며 이 Container의 기능을 제공해 주고자 하는 것이 IoC 모듈

**객체 간의 강한 결합을 Assembler를 통해 결합도를 낮춤**
- IoC 호출 방식
- 팩토리 패턴의 장점을 더하여 어떠한 것에도 의존하지 않는 형태가 된다.
- 실행시점(Runtime)에 클래스 간의 관계가 형성
- Assembler(조립기)에 의존성을 주입, 인터페이스를 구현한 클래스를 생성,
- Spring Container가 외부 조립기(Assembler) 역할 수행

<br>

## Container

<br>

객체의 생성, 사용, 소멸에 해당하는 라이프사이클을 담당

라이프사이클을 기본으로 애플리케이션 사용에 필요한 주요 기능을 제공

<br>

#### Container 기능

라이프 사이클 관리

Dependency 객체 제공

Thread 관리

기타 애플리케이션 실행에 필요한 환경

#### Container 필요성

비지니스 로직외에 부가적인 기능들에 대해서는 독립적으로 관리되도록 하기 위함

서비스 look up이나 Configuration에 대한 일관성을 갖기 위함

서비스 객체를 사용하기 위해 각각 Factory 또는 Singleton 패턴을 직접 구현하지 않아도 됨

<br>

### IoC Container

<br>

오브젝트의 생성과 관계설정, 사용, 제거 등의 작업을 애플리케이션 코드 대신 독립된 컨테이너가 담당

컨테이너가 코드 대신 오브젝트에 대한 제어권을 갖고 있어 IoC라고 부른다.

위와 같은 이유로 스프링 컨테이너를 IoC 컨테이너라고 부르기도 한다.

스프링에서 IoC를 담당하는 컨테이너에는 BeanFactory, ApplicationContext가 있다.

<br>

### Spring DI Container

<br>

Spring DI Container가 관리하는 객체를 빈(Bean)이라 하고, 이 빈들의 생명주기(Life-Cycle)를 관리하는 의미로 빈팩토리(BeanFactory)라 한다.

Bean Factory에 여러 가지 컨테이너 기능을 추가하여 Application Context라 한다.

`<<interface>> BeanFactory`

- Bean을 등록, 생성, 조회, 반환 관리
- 일반적으로 BeanFactory보다는 이를 확장한 ApplicationContext를 사용
- `getBean()` method가 정의되어 있다.
- 단일 유형의 객체를 생성하는 것이 아니라, 여러 유형의 Bean을 생성, 제공
- 객체간의 연관 관계를 설정, 클라이언트의 요청 시 Bean을 생성
- Bean의 LifeCycle 관리 

`<<interface>> ApplicationContext`

- Bean을 등록, 생성, 조회, 반환 관리 기능은 BeanFactory와 같다.
- BeanFactory가 제공하는 모든 기능 제공
- Spring의 각종 부가 서비스를 추가로 제공
- Spring이 제공하는 ApplicationContext 구현 클래스는 여러가지 종류가 있다.
- 엔터프라이즈에 애플리케이션을 개발하는데 필요한 여러 기능을 추가
- I18N. 리소스 로딩, 이벤트 발생 및 통지
- 컨테이너 생성시 모든 Bean 정보를 메모리에 로딩

`<<interface>> WebApplicationContext`

- 웹 환경에서 사용할 때 필요한 기능이 추가된 ApplicationContext
- 가장 많이 사용, 특히 XmlWebApplicationContext를 가장 많이 사용

<br>

## Spring DI(Dependency Injection) 용어

<br>

**빈(Bean)**
- 스프링이 IoC 방식으로 관리하는 오브젝트
- 스프링이 직접 그 생성과 제어를 담당하는 오브젝트만을 bean이라 부른다.

**빈 팩토리(BeanFactory)**
- 스프링이 IoC를 담당하는 핵심 컨테이너
- Bean을 등록, 생성, 조회, 반환하는 기능을 담당
- 일반적으로 BeanFactory를 바로 사용하지 않고 이를 확장한 ApplicationContext를 이용

**애플리케이션 컨텍스트(ApplicationContext)**
- BeanFactory를 확장한 IoC 컨테이너
- Bean을 등록하고 관리하는 기본적인 기능은 BeanFactory와 동일
- 스프링이 제공하는 각종 부가 서비스를 추가로 제공
- BeanFactory라고 부를 때는 주로 빈의 생성과 제어의 관점
- ApplicationContext라고 할 때는 스프링이 제공하는 애플리케이션 지원 기능을 모두 포함해서 이야기하는 것

**설정정보 / 설정 메타정보(configuration metedata)**
- 스프링의 설정정보란 ApplicationContext 또는 BeanFactory가 IoC를 적용하기 위해 사용하는 메타 정보
- 구성 정보 또는 형상 정보를 의미
- 설정정보는 IoC 컨테이너에 의해 관리되는 Bean 객체를 생성하고 구성할 때 사용된다.

**스프링 프레임워크(Spring Framework)**
- 스프링 프레임워크는 IoC 컨테이너, ApplicationContext를 포함해서 스프링이 제공하는 모든 기능을 통틀어 말할 때 주로 사용