## 람다 표현식 Lambda Exression

<br>

**자바8 (JDK1.8)** 부터 지원

기존의 자바 변경없이 **함수형 프로그래밍 형태 지원**

코드 간결화 가능

다른 함수에 전달되는 함수인 **일급객체**를 쓸 수 있다. -> 함수형 프로그래밍 언어이다.

<br>

### 람다식

<br>

메서드를 **하나의 식(expression)** 으로 표현한 것

메서드를 람다식으로 표현하면 메서드의 이름과 반환값이 없어져 **익명 함수(anonymous function)** 이라고도 한다.

<br>

```java
// 변수명 = 람다식 매개변수 -> { 구현/리턴 내용 };
FunctionalInterface 참조변수 = (int x1, int x2) -> { return x1 + x2; };
```

<br>

익명 클래스의 객체와 동등하다.

**구현부가 한 줄**인 경우 **중괄호 {} 생략 가능**

<br>

```java
// 구현 내용이 한 줄일 경우 return 키워드 생략 가능
FunctionalInterface 참조변수 = (int x1, int x2) -> x1 + x2;
```

<br>

그 한줄이 리턴되는 값으로 판단, **return 키워드 생략 가능**

return 문 대식 **식(expression)**으로 작성


<br>

```java
// 구현 내용이 한 줄일 경우 return 키워드 생략 가능
FunctionalInterface 참조변수 = (int x1, int x2) -> x1 + x2;

// 구현 내용이 여러 줄일 경우
FunctionalInterface 참조변수 = (int x1, int x2) -> {
	System.out.println(x1 + x2);
	return x1 + x2;
};

// 데이터 추론 가능 매개변수 데이터타입 생략 가능, 인터페이스 선언부를 보고 파라미터 타입을 판단
FunctionalInterface 참조변수 = (x1, x2) -> x1 + x2;
```

<br>

문장이 아닌 식으로 끝에 **; 을 붙이지 않는다.**

<br><br>

### 함수형 인터페이스 FunctionalInterface

<br>

람다식을 다루기 위한 **인터페이스**

오직 **하나의 추상 메서드만 정의**되어 있어야 한다.

그래야 람다식과 인터페이스의 메서드가 **1 대 1 연결**이 가능하다.

static 메서드와 default 메서드 개수에는 제약이 없다.

`@FunctionalInterface` 함수형 인터페이스인지 검사

<br>

```java
@FunctionalInterface
public interface 함수형인터페이스 {
	반환타입 메소드이름(매개변수...);
}

```

<br>

### 함수형 인터페이스 타입

<br>

메서드의 **매개변수**가 **함수형 인터페이스 타입**일 때 메서드를 호출할 때 **람다식을 참조하는 참조변수**를 매개 변수로 지정해야 한다.

또는 **참조변수 없이 직접 람다식**을 매개변수로 지정하는 것도 가능하다.

<br>

```java
// 함수에 다른 함수를 파라미터로 전달
FunctionalInterface 참조변수 = () -> System.out.println("test");
abstractMethod(참조변수);

abstractMethod(() -> System.out.println("test"));
```

<br>

메서드의 **반환타입**이 **함수형 인터페이스타입**이라면, 해당하는 함수형 인터페이스의 추상메서드와 동등한 **람다식을 가리키는 참조변수**를 반환하거나 **람다식을 직접 반환**할 수 있다.

<br>

```java
FunctionalInterface 메서드이름() {
    FunctionalInterface 참조변수 = () ->{};
    return 참조변수; // return ()->{};
}
```

<br>

**함수형 인터페이스로 람다식을 참조**할 수 있다.

람다식의 타입이 함수형 인터페이스 타입과 일치하는 것은 아니다.

**람다식**은 익명 객체, **익명 객체는 타입이 없다.**

참조를 위해 **형변환** 필요 발생

람다식은 **함수형 인터페이스로만 형변환**이 가능

**Object 타입으로 형변환 불가**

<br>

**람다식 내부에서 참조하는 지역변수**는 final이 붙지 않아도 상수로 간주

람다식 내부 또는 외부에서 해당 변수의 값 **변경을 허용하지 않는다.**

Inner 클래스와 Outer 클래스의 인스턴스 변수 사용 시 `this` 또는 `Outer` 키워드 사용

외부 변수와 **같은 이름으로 람다식의 매개변수는 허용되지 않는다.**