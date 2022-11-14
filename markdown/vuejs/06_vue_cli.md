## @vue/cli

<br>

### @vue/cli 실행 환경 구축

<br>

NodeJS 설치 - LTS 버전(NPM 같이 설치)

NPM을 이용한 @vue/cli 설치

<br>

#### NodeJs 설치

[NodeJS 설치](https://nodejs.org/ko/)

각 운영체제에 맞는 LTS버전 다운로드

<br>

#### NodeJS 설치 확인

`node -v`

`node --version`

`npm -v`

<br>

#### NPM

Node Package Manager

command에서 써드파티 모듈을 설치하고 관리하는 툴

[모듈(패키지) 검색](https://www.npmjs.com/)

<br>

#### NPM 명령어

`npm init` : 새로운 프로젝트나 패키지를 만들 때 사용 (package.json 생성)

`npm install package` : 생성되는 위치에서만 사용 가능한 패키지로 설치

`npm install -g package` : 글로벌 패키지에 추가, 모든 프로젝트에서 사용 가능한 패키지로 설치

<br>

### @vue/cli

<br>

CLI : Command Line Interface

Vue.js 개발을 위한 시스템으로 Vue.js에서 공식으로 제공하는 CLI

개발의 필수는 아니지만 개발의 편리성을 위해 필수처럼 사용

Vue 프로젝트를 빠르게 구성할 수 있는 스캐폴딩을 제공

Vue과 관련된 오픈 소스들의 대부분이 CLI를 통해 구성이 가능하도록 구현되어 있다.

[Vue CLI](https://cli.vuejs.org/)

<br>

#### @vue/cli 설치

`npm install -g @vue/cli`

`vue -V` or `vue --version`

<br>

### @vue/cli 프로젝트 생성

<br>

생성 : `vue create project-name`

생성 중 중지 : ctrl + c

실행 : `npm run serve`

<br>

#### @vue/cli 프로젝트 생성 후 별도 플러그인 설치

`vue add plugin-name`

<br>

#### axios 추가

`npm install axios`

package.json 파일의 dependencies 확인

<br>

### @vue/cli 프로젝트 구조

<br>

#### @vue/cli 3.x 이상 버전

플러그인 방식으로 기능 추가

Webpack 설정 파일 내부 처리

UI를 통한 프로젝트 관리

프로젝트 생성시 모듈을 같이 다운로드

<br>

#### UI를 통한 프로젝트 관리

project-path>`vue ui`

<br>

### SFC (Single File Component)

<br>

확장자가 ".vue"인 파일

.vue = template(html) + script + style

구문 강조 가능

컴포넌트에만 CSS의 범위를 제한할 수 있다.( `<style scoped>`)

전처리기를 사용해 기능의 확장이 가능

<br>

#### template

기본 언어 : html

각 \*.vue 파일은 한 번에 최대 하나의 `<template>`블록을 포함 할 수 있다.

내용은 문자열로 추출되어 컴파일 된 Vue Component의 template 옵션으로 사용

<br>

#### script

기본언어 : js

각 \*.vue 파일은 한 번에 최대 하나의 `<script>` 블록을 포함할 수 있다.

ES2015(ES6)를 지원하여 `import`와 `export`를 사용 할 수 있다.

<br>

#### style

각 \*.vue 파일은 여러 개의 `<style>` 태그를 지원

`scoped` 속성을 이용하여 현재 컴포넌트에서만 사용 가능한 css를 지정 가능
