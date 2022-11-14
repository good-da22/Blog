## axios

<br>

### HTTP 통신 : axios

<br>

[axios](https://github.com/axios/axios#axios-api)

`npm install axios`

Vue에서 권고하는 HTTP 통신 라이브러리는 axios

**promise** 기반의 HTTP 통신 라이브러리이며 상대적으로 다른 HTTP 통신 라이브러리들에 비해 문서화가 잘되어 있고 API가 다양하다.

`axios.get(URL) // promise 객체를 return`, `then`, `catch` 사용 가능

[axios](https://github.com/axios/axios)

<br>

#### promise

promise란 서버에 데이터를 요청하여 받아오는 동작과 같은 비동기 로직 처리에 유용한 자바스크립트 라이브러리

자바스크립트는 단일 스레드로 코드를 처리하기 때문에 특정 로직의 처리가 끝날 때까지 기다려 주지 않는다.

따라서 데이터를 요청하고 받아올 때까지 기다렸다가 화면에 나타내는 로직을 실행해야 할 때 주로 promise를 활용한다.

그리고 데이터를 받아왔을 때 promise로 데이터를 화면에 표시하거나 연산을 수행하는 등 특정 로직을 수행한다.

<br>

### axios API

<br>

- `axios.get('URL 주소').then().catch()`
  
  해당 URL 주소에 대해 HTTP GET 요청을 보냄

  서버에서 보낸 데이터를 정상적으로 받아오면 `then()`안에 정의된 로직 실행

  데이터를 받아올 때 오류가 발생하면 `catch()`에 정의한 로직이 실행

- `axios.post('URL 주소').then().catch()`

  해당 URL 주소에 대해 HTTP POST 요청을 보냄

  `then()`과 `catch()`는 get 방식과 동일

- `axios({ 옵션 속성 })`

  HTTP 요청에 대한 자세한 속성을 직접 정의하여 보냄

  데이터 요청을 보낼 URL, HTTP 요청 방식, 보내는 데이터 유형 등

<br>

## vue-router

<br>

[vue-router](https://v3.router.vuejs.org.kr)

라우팅 : 웹 페이지 간의 이동 방법

Vue.js의 공식 라우터

라우터는 컴포넌트와 매핑

Vue를 이용한 SPA를 제작할 때 유용

URL에 따라 컴포넌트를 연결하고 설정된 컴포넌트를 보여준다.

`npm install vue-router`

<br>

### vue-router 연결

<br>

`routes` 옵션과 함께 router instance 생성

```javascript
// 라우트 컴포넌트
const Main = { 
  template: '<div>메인 페이지</div>'
};
const Board = {
  template: '<div>자유게시판</div>'
};

const router = new VueRouter({
  routes: [
    {
      path: '/',
      component: Main, // 라우트 컴포넌트 정의
    },
    {
      path: '/board',
      component: Board,
    },
  ],
});
```

<br>

### vue-router 이동 및 렌더링

<br>

네비게이션을 위해 `router-link` 컴포넌트를 사용

속성은 `to` prop을 사용

기본적으로 `<router-link>`는 `<a>` 태그로 렌더링

```html
<router-link to="/">HOME</router-link>
<router-link to="/board">게시판</router-link>
```

현재 라우트에 맞는 컴포넌트가 렌더링 된다.

```html
<!-- 현재 라우트에 맞는 컴포넌트가 렌더링 -->
<router-view></router-view>
```

<br>

### $router, $route

<br>

라우트 설정

```javascript
const router = new VueRouter({
  routes: [
    ...,
    {
      path: '/board/:no',
      component: BoardView,
    },
  ],
});
```

라우터 링크

```html
<router-link to="/board/20">20번 게시글</router-link>
```

전체 라우터 정보

`this.$router`

현재 호출된 해당 라우터 정보

`this.$route`

`this.$route.params.no`

`this.$route.path`

<br>

### 이름을 가지는 route

<br>

route는 연결하거나 탐색을 수행할 때 이름이 있는 route를 사용

Router Instance를 생성하는 동안 routes 옵션에 지정

```javascript
routes: [
  ...,
  {
    path: '/board',
    name: 'board',
    component: Board,
    redirect: '/board/list', // or redirect: { name: 'list' } 리다이렉트
  },
  ...,
],
```

<br>

### 프로그래밍 방식 router

<br>

`<router-link>`를 사용하여 선언적 네비게이션용 achor 태그를 만드는 것 외에도 라우터의 instance method를 사용하여 프로그래밍으로 수행

```javascript
$router.push('home');
$router.push({ path: 'home' });
$router.push({ name: 'boardview', params: { no: 3 } });
$router.push({ path: '/board', query: { pg: 1} });
```

<br>

### 중첩된 route

<br>

앱 UI는 일반적으로 여러 단계로 중첩된 컴포넌트 구조임

URL의 세그먼트가 중첩된 컴포넌트의 특정 구조와 일치하는 것을 활용

