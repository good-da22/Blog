## Exception handling

<br>

### try - catch - finally

<br>

`finally` 블록은 예외 발생 여부와 상관 없이 실행되어야 하는 코드를 포함

`try - catch` 블록에 선택적으로 추가하여 사용

중간에 `return`을 만나는 경우에도 `finally` 블록을 **수행 후 리턴**

<br>

```java
try {
    // exception이 발생할 만한 코드 - System 자원 사용
} catch (Exception e) {
    // 예외 발생 시 처리 코드
} finally {
    // try block에서 접근했던 System자원의 안전한 원상 복구

    // try 블록 또는 catch 블록에 return이 존재해도 finally 블록 수행 후 종료
}
```

<br>

`finally` 블록을 통해 예외 발생 여부와 상관 없이 자원 정리 가능

`try` 블록에서 사용한 리소스 반납

생성한 시스템 자원을 반납하지 않는 경우 추후 **resource leak 발생 가능 -> close 처리**

<br>

`finally` 블록에서 `close()` 메서드 사용하는 경우, IOException 발생 가능

`finally` 블록 안에서도 `try - catch` 블록으로 예외를 처리해야 한다.

코드 가독성이 떨어지며 `try` 블록과 `finally` 블록 모두 예외가 발생하면 `try` 블록의 예외는 무시된다.

<br><br>

### try - with - resource

<br>

JDK 1.7 이상에서 리소스의 자동 `close()` 처리

<br>

```java
try (리소스타입 res1 = 초기화; 리소스타입 res2 = 초기화; ...) {
    // 예외 발생 코드
} catch (Exception e) {
    // 예외 처리 코드
}
```
<br>

괄호 () 안에서 객체를 생성하는 문장을 넣으면 해당 객체는 `close()` 를 호출하지 않아도 `try` 블록을 벗어나는 순간 **자동 `close()` 호출**

그 다음 `catch` 블록 또는 `finally` 블록 실행

<br>

해당 객체들은 **AutoCloseable interface를 구현한 것**이여만 한다.

해당 객체는 `try` 블록에서 다시 할당될 수 없다.

<br><br>

## throws exception

<br>

메서드에서 처리해야할 하나 이상의 예외를 **호출한 곳**으로 전달 (처리 위임)

예외가 여러 개일 경우 쉼표(,)로 구분

메서드 재정의 시 조상 클래스 메서드가 던지는 예외보다 부모타입의 예외를 던질 수 없다.

<br>

```java
리턴타입 method() throws 예외, 예외, ... {
    // 예외 발생 코드
    // 직접 해결하지 않고 처리 위임
}

// 예외가 발생하는 method() 호출
리턴타입 callMathod() {
    try {
        method();
    } catch (예외 e) {
        ...
    }
}
```

<br>

메인 메서드에서 `throws` 사용 시 **JVM에게 예외를 던진다.**

예외가 없어지는 것이 아닌 단순히 전달, 전달 받은 메서드는 다시 예외를 처리하거나 다시 던지거나

처리하려는 예외의 **조상 타입**으로 `throws` 가능

<br>

**uncheckedException**  (RuntimeException) **따로 `throws` 없어도 전달**이 된다.

전달되고 나서 결국은 `try - catch로` 해결해야 한다.

코드 작성은 간편해지나 눈으로 예외를 즉각적으로 파악하기 어렵다. 

실행을 해야 알 수 있다.

<br>

**checkedException** 은 `throws` 하거나 `try-catch`로 해결

<br><br>

### 메서드 호출 스택 (method call stack)

<br>

Throwable 의 `printStackTrace()` 로 예외 발생 시 메서드 호출 스택 정보 조회 가능

최초 호출 메서드부터 예외 발생 메서드까지 **스택 정보 출력**

예외 종류, 예외 원인 파악을 통해 **디버깅 출발점 설정**

**직접 작성한 코드를 디버깅 대상으로**

<br>

참조하는 라이브러리는 건너뛰기

API가 제공하는 메서드는 사전에 예외가 발생할 수 있음을 선언부에 명시

프로그래머가 예외에 대처하도록 강요

개발자가 예외가 발생했음을 인지하고 적절하게 처리를 유도하기 위해

<br><br>

### 사용자 정의 예외

<br>

API에 정의된 기존 예외 클래스 외에 필요에 따라 새로운 사용자 정의 예외 클래스 작성 가능

대부분 Exception 또는 RuntimeException 클래스를 상속받아 작성

<br>

- **checked exception** 활용
  - **명시적 예외 처리** 또는 **throws** 필요
  - 코드는 복잡해지지만 처리 누락 등 오류 발생 가능성 감소

<br>

- **unchecked exception** 활용
  - 묵시적 예외 처리 가능
  - 코드는 간결해지나 예외 처리 누락 가능
  - 문제 발생 가능성을 **조건문**을 통해 처리하는 것이 좋다
  - **디버깅의 대상**으로 예외의 처리 대상으로 생각하지 말것

<br>

**장점**
---
- **객체 활용** : 필요한 추가정보, 기능 활용 가능
- **코드 재사용** : 동일 상황에서 예외 객체 재사용 가능
-  **throws 메커니즘 이용** : 중간 호출 단계에서 return 불필요

<br>

Exception 클래스를 상속받을 때 생성시 String 값을 받아 메시지로 저장 가능

String을 매개변수로 받는 생성자 추가

<br>

```java
class 사용자 정의 예외 extends Exception {
    사용자 정의 예외(String message) {// String을 매개변수로 받는 생성자
        super(message); // 조상 Exception 클래스의 생성자 호출
    }
}
```