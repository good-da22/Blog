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

