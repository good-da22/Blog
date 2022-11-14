## vuex

<br>

[vuex](https://vuex.vuejs.org/)

Vue.js apllication에 대한 **상태관리패턴 + 라이브러리**

application 모든 component들의 중앙 저장소 역할(데이터 관리)

상위(부모) 하위(자식)의 단계가 많이 복잡해 진다면 데이터의 전달하는 부분이 매우 복잡해 짐

application이 여러 구성 요소로 구성되고 더 커지는 경우 데이터를 공유하는 문제가 발생

<br>

#### 부모-자식 컴포넌트간의 data 전달

자식 -> `$emit` -> 부모 -> `props` -> 자식

#### 동위 컴포넌트간의 data 전달

자식 -> `$emit` -> Event Bus -> `$on` -> 자식

#### vuex

공통의 저장소 사용

<br>

### 상태 관리 패턴

<br>

```javascript
new Vue({
  // 상태
  data() {
    return {
      count: 0,
    }
  },
  // 뷰
  template: `
    <div>{{ count }}</div>
  `,
  // 액션
  methids: {
    increment() {
      this.count++,
    }
  }
});
```

page 10