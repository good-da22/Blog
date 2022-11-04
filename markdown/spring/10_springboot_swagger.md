## SpringBoot

<br>

Spring의 경우 Application을 개발하려면 사전에 많은 작업(library 추가, dependency 설정, 그 외 SpringFramework가 처리해야 할 여러 가지 구성 및 설정 파일 등)이 필요

SpringBoot의 장점
- project에 따라 자주 사용되는 library들이 미리 조합되어 있다.
- 복잡한 설정을 자동으로 처리
- 내장 서버를 포함하여 tomcat과 같은 WAS를 추가로 설치하지 않아도 개발 가능
- WAS에 배포하지 않고도 실행할 수 있는 JAR파일로 Web Application 개발 가능
- Spring Starter Project를 이용하여 쉽게 SpringBoot 기반 프로젝트 생성 가능

<br>

### project 생성 구조 및 주요 구성 폴더 / 파일

<br>

src/main/java
- java source directory

HelloSpringBootApplication
- application 을 시작할 수 있는 main method가 존재하는 스프링 구성 메인 클래스

static
- img, css, js 등 정적 resource directory

templates
- SpringBoot에서 사용 가능한 여러 View Template(Tymleaf, Velocity, FreeMarker ...)

application.properties
- application 및 스프링의 설정 등에서 사용할 여러 property를 정의한 file

src/main
- jsp 등의 resource directory

<br>

## Swagger

<br>

간단한 설정으로 프로젝트의 API 목록을 웹에서 확인 및 테스트 할 수 있게 해주는 Library

Swagger를 사용하면 Controller에 정의되어 있는 모든 URI를 바로 확인할 수 있다.

API 목록 뿐 아니라 API의 명세 및 설명도 볼 수 있으며, 또한 API를 직접 테스트해 볼 수도 있다.

<br>

### Swagger를 이용한 REST API 문서화

<br>

프로젝트 개발 시 일반적으로 FrontEnd 개발자와 BackEnd 개발자 분리

FrontEnd 개발자의 경우 화면과 로직에 집중, BackEnd 개발자가 만든 문서 API를 보며 데이터 처리

이 때 개발 상황의 변화에 따른 API의 추가 또는 변경할 때 마다 문서에 적용하는 불편함 발생

이 문제를 해결하기 위해 Swagger 사용
