## java.util.function 패키지

<br>

대부분의 메서드는 매개변수가 없거나 한 개 또는 두 개, 반환 값이 없거나 한 개

**제네릭 메서드**로 정의하면 **매개변수**나 **반환 타입**이 달라도 문제가 되지 않는다.

**java.util.function 패키지**에 일반적으로 쓰이는 형식의 메서드를 **함수형 인터페이스**로 미리 정의

패키지 활용을 통해 함수형 인터페이스에 정의된 메서드 이름 통일

**재사용성**이나 **유지보수** 측면에서 효율적

**매개변수의 개수**, **반환 여부**에 따라 함수형 인터페이스 사용 가능

<br>

- 매개변수 없음, 반환값 없음
  
```java
java.lang.Runable
@FunctionalInterface
public interface Runnable {
    public abstract void run();
}
```

- 매개변수 없음, 반환값 있음
```java
@FunctionalInterface
public interface Supplier<T> {
    public abstract T get();
}
```

- 매개변수 한 개, 반환값 없음

```java
@FunctionalInterface
public interface Consumer<T> {
    public abstract void accept(T t);
}
```

- 매개변수 한 개, 반환값 있음
  
```java
@FunctionalInterface
public interface Function<T, R> {
    public abstract R apply(T t);
}
```

- 매개변수 한 개, 반환 타입 boolean
    
    조건식을 함수(람다식)로 표현하는데 사용
```java
@FunctionalInterface
public interface Predicate<T> {
    public abstract boolean test(T t);
}
```

<br>

#### 매개변수 2개

<br>

- 매개변수 두 개, 반환값 없음

```java
@FunctionalInterface
public interface BiConsumer<T, U> {
    public abstract void accept(T t, U u);
}
```

- 매개변수 두 개, 반환 타입 boolean

    조건식을 함수(람다식)로 표현하는데 사용
```java
@FunctionalInterface
public interface BiPredicate<T, U> {
    public abstract boolean test(T t, U u);
}
```

- 매개변수 두 개, 반환값 있음
  
```java
@FunctionalInterface
public interface BiFunction<T, R> {
    public abstract R apply(T t);
}
```

<br>

#### Function 변형

<br>

- Function의 자손, 매개변수와 결과의 타입이 같다.

```java
@FunctionalInterface
public interface UnaryOperator<T> {
    public abstract T apply(T t);
}
```

- BiFunction의 자손, 매개변수와 결과의 타입이 같다.

```java
@FunctionalInterface
public interface BinaryOperator<T> {
    public abstract T apply(T t, T t);
}
```

<br><br>

### 컬렉션 프레임워크

<br>

컬렉션 프레임워크 인터페이스에서 함수형 인터페이스를 사용하는 **디폴트 메서드**

<br>

#### Collection

<br>

- `boolean removeIf(Predicate<E> filter)`
  
    조건에 맞는 요소를 삭제

<br>

#### List

<br>

- `void replaceAll(UnaryOperator<E> operator)`
  
    모든 요소를 변환하여 대체

<br>

#### Iterable

<br>

- `void forEach(Consumer<T> action)`
    
    모든 요소에 작업 action 을 수행

<br>

#### Map

<br>

- `V compute(K key, BiFunction<K, V, V> f)`

    지정된 키의 값에 잡업 f 를 수행

- `V computeifAbsent(K key, Function<K, V> f)`

    키가 없으면, 작업 f 수행 후 추가

- `V computeIfPresent(K key, BiFunction<K, V, V> f)`

    지정된 키가 있을 때, 작업 f 수행

- `V merge(k key, V value, BiFunction<V, V, V> f)`

    모든 요소에 병합작업 f 를 수행

- `void forEach(BiConsumer<K, V> action)`

    모든 요소에 작업 action 을 수행

- `void replaceAll(BiFunction<K, V, V> f)`

    모든 요소에 치환작업 f 를 수행

<br><br>

### 기본형을 사용하는 함수형 인터페이스

<br>

**기본형**을 사용하는 함수형 인터페이스 제공

<br>

- A To B Function, 입력은 타입 A, 출력은 타입 B

```java
@FunctionalInterface
public interface DoubleToIntFunction {
    public abstract int applyAsInt(double d);
}
```

<br>

- To A Function, 입력은 제네릭 타입, 출력은 타입 A

```java
@FunctionalInterface
public interface ToIntFunction<T> {
    public abstract int applyAsInt(T value);
}
```

<br>

- A Function, 입력은 타입 A, 출력은 제네릭타입

```java
@FunctionalInterface
public interface IntFunction<R> {
    public abstract R apply(T t, U u);
}
```

<br>

- Obj A Consumer, 입력은 T, 타입 A, 출력은 없음

```java
@FunctionalInterface
public interface ObjIntConsumer<T> {
    public abstract void apply(T t, U u);
}
```

<br><br>

### 메서드 참조(method reference)

<br>

람다식이 **하나의 메서드만 호출**하는 경우 메서드 참조를 통해 간략히 표현 가능

참조변수 타입이 받는 매개변수를 메서드에서 사용하는 경우

이미 생성된 객체의 메서드를 람다식에서 사용하는 경우 객체의 참조변수를 적어야 한다

`함수형인터페이스 f = 클래스이름::메서드이름`

`함수형인터페이스 f = 참조변수::메서드이름`

<br>

**생성자를 호출하는 람다식**도 메서드 참조로 변환 가능

매개변수가 있는 생성자인 경우, 매개변수에 개수에 따라 알맞은 함수형 인터페이스를 사용

필요하다면 함수형 인터페이스를 새로 정의

`함수형인터페이스 f = 클래스이름::new`

<br>

메서드 참조는 람다식을 마치 static 변수처럼 다룰 수 있게 해준다.