page15 이어서

#### MyBatis-Spring 주요 Components

![](/img/inner%20ing/MyBatisSpringComponents.png)

<br>

- MyBatis 설정파일(sqlMapConfig.xml)
  - Dto 객체의 정보를 설정한다. (Alias)

- SqlSessionFactoryBean
  - MyBatis 설정 파일을 바탕으로 SqlSessionFactory를 생성
  - Spring Bean으로 등록해야 한다.

- SqlSessionTemplate
  - 핵심적인 역할을 하는 클래스, SQL 실행이나 Transaction 관리를 실행
  - SqlSession interface를 구현하며, thread-safe 하다.
  - Spring Bean으로 등록해야 한다.

- mapping 파일
  - SQL 문과 ORMapping

- Spring Bean 설정 파일(beans.xml)
  - SqlSessionFactoryBean을 Bean에 등록할 때 DataSource 정보와 MyBatis Config 파일 정보, Mapping 파일의 정보를 함께 설정
  - SqlSessionTemplate을 Bean으로 등록

<br>

### MyBatis Interface

<br>

#### Mapper Interface

<br>

Mapper Interface는 mapping 파일에 기재된 SQL을 호출하기 위한 Interface

Mapper Interface는 SQL을 호출하는 프로그램을 Type Safe하게 기술하기 위해 MyBatis 3.x 부터 등장

Mapping 파일에 있는 SQL을 java interface를 통해 호출할 수 있도록 한다.

<br>

#### Mapper Interface를 사용하지 않았을 경우

SQL을 호출하는 프로그램은 SqlSession의 method의 argumente에 문자열로 **namespace + "." + SQL ID**로 지정

문자열로 지정하기 때문에 오타에 의한 버그가 생기거나, IDE가 제공하는 code assist를 사용할 수 없다.

<br>

#### Mapper Interface를 사용했을 경우

UserMapper Interface는 개발자가 작성

**packagename + "." + InterfaceName + "." + methodName이 namespace + "." + SQL ID** 가 되도록 namespace와 SQL ID를 설정

namespace 속성에는 package를 포함한 Mapper Interface의 이름을 작성

SQL ID에는 mapping하는 method의 이름을 지정

<br>

### MyBatis-Spring 연동

<br>

MyBatis 를 Standalone 형태로 사용하는 경우, SqlSessionFactory 객체를 직접 사용

스프링을 사용하는 경우, 스프링 컨테이너에 MyBatis 관련 빈을 등록하여 MyBatis를 사용

또한 스프링에서 제공하는 트랜잭션 기능을 사용하면 손쉽게 트랜잭션 처리

MyBatis를 스프링과 연동하기 위해서는 MyBatis에서 제공하는 Spring 연동 라이브러리 필요

MyBatis 스프링 연동 라이브러리 의존관계 설정

<br>

#### DataSource 설정

<br>

스프링을 사용하는 경우, 스프링에서 데이터 소스를 관리하므로 MyBatis 설정파일에서는 일부 설정을 생략

스프링 환경 설정파일(application-context.xml)에 데이터소스 설정

데이터소스는 SimpleDriverDataSource 클래스의 빈으로 데이터베이스 연결정보를 가진 객체

MyBatis와 스프링을 연동하면 데이터베이스 설정과 트랜잭션 처리는 스프링에서 관리

<br>

#### TransactionManager 설정

<br>

트랜잭션을 관리하는 객체

MyBatis는 JDBC를 그래도 사용하기 때문에 DataSOurceTransactionManager 타입의 빈을 사용

tx:annotation-driven 요소는 트랜잭션 관리방법을 어노테이션으로 선언하도록 설정

스프링은 메소드나 클래스에 `@Transactional` 이 선언되어 있으면, AOP를 통해 트랜잭션을 처리

<br>

#### SqlSessionFactoryBean

<br>

MyBatis 애플리케이션은 SqlSessionFactory 를 중심으로 수행

스프링에서 SqlSessionFactory 객체를 생성하기 위해서는 SqlSessionFactoryBean을 빈으로 등록해야 한다.

SqlSessionFactoryBean 을 빈으로 등록할 때, 사용할 데이터소스와 mybatis 설정파일 정보 필요

<br>

####  mapper 빈 등록

<br>

Mapper 인터페이스를 사용하기 위해서 스캐너를 사용하여 자동으로 등록하거나, 직접 빈으로 등록

mapperScannerConfigurer을 설정하면, Mapper 인터페이스를 자동으로 검색하여 빈으로 등록

basePaackage로 패키지를 설정하면, 해당 패키지 하위의 모든  Mapper 인터페이스가 자동으로 등록

MapperFactoryBean 클래스는 Mapper 인터페이스를 직접 등록할 때 사용

<br>

#### MyBatis Configuration 파일

<br>

스프링을 사용하면 DB 접속정보 및 Mapper 관련 설정은 스프링 빈으로 등록하여 관리

MyBatis 환경설정 파일에는 스프링에서 관리하지 않는 일부 정보만 설정 ex) typeAlias, typeHandler 등

<br>

#### 데이터 접근 객체 구현

<br>

데이터 접근 객체는 특정한 기술을 사용하여 데이터 저장소에 접근하는 방식을 구현한 객체

`@Repository` 은 데이터 접근 객체를 빈으로 등록하기 위해 사용하는 스프링에서 제공하는 어노테이션

`@Autowired` 어노테이션을 통해, 사용하려는 Mapper 인터페이스를 데이터 접근 객체와 의존 관계를 설정