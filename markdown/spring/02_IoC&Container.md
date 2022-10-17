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

Lookup 한 Objecet를 필요한 타입으로 Casting 필요

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

page 39








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

`<<interface>> ApplicationCOntext`

- Bean을 등록, 생성, 조회, 반환 관리 기능은 BeanFactory와 같다.
- Spring의 각종 부가 서비스를 추가로 제공
- Spring이 제공하는 ApplicationContext 구현 클래스는 여러가지 종류가 있다.