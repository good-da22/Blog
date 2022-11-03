## REST API

<br>

### OPEN API (Application Programming Interface)

<br>

OPEN API는 프로그래밍에서 사용할 수 있는 개방되어 있는 상태의 Interface

많은 사이트들이 가지고 있는 데이터를 외부 응용 프로그램에서 사용할 수 있도록 OPEN API를 제공

OPEN API와 함께 거론되는 기술이 REST, 대부분의 OPEN API는 REST 방식으로 지원

<br>

### REST (Representational State Transfer)

<br>

2000년도 로이 필딩(Roy Fielding)의 박사학위 논문에 최초로 소개

REST 는 'Representational State Transfer'의 약어로 하나의 URI는 하나의 고유한 리소스(Resource)를 대표하도록 설계된다는 개념에 전송방식을 결합해서 원하는 작업을 지정

URI + GET / POST / PUT/ DELETE

웹의 장점을 최대한 활용할 수 있는 아키텍처(설계구조)로써 REST를 발표

HTTP URI를 통해 제어할 자원(Resource)를 명시하고, HTTP Method(GET, POST, PUT, DELETE)을 통해 해당 자원(Resource)를 제어하는 명령을 내리는 방식의 아키텍처

<br>

#### REST 구성

<br>

자원 (Resource) : URI

행위 (Verb) - HTTP Method

표현 (Representations)

잘 표현된 HTTP URI로 Resource를 정의하고 HTTP method로 리소스에 대한 행위를 정의한다.

Resource는 JSON, XML과 같은 여러 가지 언어로 표현할 수 있다.

<br>

#### 기존 Service VS REST Service

<br>

기존 Service : 요청에 대한 처리를 한 후 가공된 data를 이용하여 특정 플랫폼에 적합한 형태의 View로 만들어서 반환

REST Service

data 처리만 한다거나, 처리 후 반환될 data가 있다면 JSON이나 XML 형식으로 전달

View에 대해서는 신경 쓸 필요가 없다. 이러한 이유로 Open API에서 많이 사용

<br>

### REST

<br>

기존의 전송방식과는 달리 서버는 요청을 받은 리소스에 대해 순수한 데이터를 전송

기존의 GET/POST 외에 PUT. DELETE 방식을 사용하여 리소스에 대한 CRUD 처리

HTTP URI를 통해 제어한 자원(Resource)를 명시하고 HTTP Method(GET / POST / PUT / DELETE)를 통해 해당 자원(Resource)를 제어하는 명령을 내리는 방식의 Architecture

자원을 표현할 때 Collection(문서, 객체의 집합)과 Documente(하나의 문서, 객체) 사용

정해진 표준은 없고 암묵적인 표준 존재
- 하이픈(-)은 사용 가능하지만 언더바(_)는 사용하지 않는다.(가독성)
- 특별한 경우를 제외, 대문자는 사용하지 않는다. (대소문자 구분, RFC3986)
- URI 마지막에 슬래시(/)를 사용하지 않는다.
- 확장자가 포함된 파일 이름을 직접 포함시키지 않는다.
- URI는 명사를 사용한다.

<br>

| 작업 | 기존방식 | REST 방식 | 비고 |
| :--: | :--: | :--: | :--: |
| Create(Insert) | POST | POST | 쓰기 |
| Read(Select) | GET | GET | 읽기 |
| Update(Update) | POSP | PUT | 수정 |
| Delete(Delete) | GET | DELETE | 삭제 |

<br>

jackson library 사용

jackson-databind 라이브러리는 객체를 JSON 포맷의 문자열로 변환시켜 브라우저로 전송

jackson-dataformat-xml 라이브러리는 객체를 xml로 브라우저로 전송

pom.xml에 dependency 추가

<br>

#### REST 관련 Annotation

<br>

`@RestController` : Controller가 REST 방식을 처리하기 위한 것임을 명시

`@ResponseBody` : JSP 같은 뷰로 전달되는 것이 아니라 데이터 자체를 전달

`@PathVariable` : URL 경로에 있는 값을 파라미터로 추출

`@CrossOrigin` : Ajax의 크로스 도메인 문제를 해결

`@RequestBody` : JSON 데이터를 원하는 타입으로 바인딩