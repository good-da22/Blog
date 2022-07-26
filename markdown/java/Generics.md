## Generics

<br>

다양한 타입의 객체를 다루는 메서드, 컬렉션 클래스에서 **컴파일 시에 타입 체크**

    Compile - 컴파일시 타입체크가 안전하다.
    
    Runtime - 동작 중에 오류 발생 가능 ex) instanceof

미리 사용할 타입을 명시해 형 변환을 하지 않아도 된다.

객체 타입에 대한 안전성 향상 및 형 변환의 번거로움 감소

<br>

### 표현

클래스 또는 인터페이스 선언 시 <>에 타입 파라미터 표시
```java
public class 클래스 이름<타입 파라미터> {}
public interface 인터페이스 이름<타입 파라미터> {}
```

<br>

###  타입 파라미터

단순히 **임의의 참조형 타입**

컴파일 시 타입 파라미터들은 대입된 타입으로 대체된다.

- - -

- T : reference **T**ype
- E : **E**lement
- K : **K**ey
- V : **V**alue

<br>

### 객체 생성

변수와 생석 부분 타입은 반드시 같아야 한다.

<br>

```java
클래스 이름<String> generic = new 클래스 이름<String>();
클래스 이름<String> generic = new 클래스 이름<>();
클래스 이름 generic = new 클래스 이름(); // 타입 참조 필요 경고
```

<br>


