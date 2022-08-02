## 정렬 Sort

<br>

요소를 특정 기준에 대한 내림차순 또는 오름차순으로 배치 하는 것

**순서를 가지는 Collection**들만 정렬 가능하다.

<br>

### sort 인터페이스를 상속 받은 자식들
- - -
- List 계열
- Set에서 SortedSet의 자식 객체 (TreeSet)
- Map에서 SortedMap의 자식 객체(key 기준) (TreeMap)

<br>

### Collections의 `sort()`를 이용한 정렬

<br>

`sort(List<T> list)`

객체가 Comparable을 구현하고 있는 경우 내장 알고리즘을 통해 정렬

<br>

### Comparator 와 Comparable

<br>

**Comparator** 와 **Comparable**은 모두 인터페이스로 컬렉션을 정렬하는데 필요한 메서드를 정의

**Comparable**을 구현하고 있는 클래스들은 같은 타입의 인스턴스끼리 **서로 비교가 가능한 클래스**

기본적으로 **오름차순**, Comparable을 구현한 클래스는 정렬이 가능하다는 것을 의미

<br>

#### Comparable

<br>

기본 정렬을 구현하는데 사용

**java.lang 패키지**

<br>

```java
public interface Comparable {
    public int compareTo(Object o);
    // 양수 : 자리 바꿈
    // 음수 : 자리 유지
    // 0 : 동일 위치
}
```

<br>

#### Comparator

<br>

 기본 정렬기준 외 **다른 기준으로 정렬**하고자할 때 사용

 객체가 Comparable을 구현하고 있지 않거나 **사용자 정의 알고리즘**으로 정렬하고자 할 때 사용

 **java.util 패키지**

 <br>

 ```java
public interface Comparator {
    int compare(Object o1, Object o2);
    // 양수 : 자리 바꿈
    // 음수 : 자리 유지
    // 0 : 동일 위치
    
    boolean equals(Object obj);
}
 ```

 <br>

 1회성 객체 사용 시 **익명 클래스 (anonymous inner class)** 사용

 클래스 정의, 객체 생성을 한번에 처리

 new 연산자 다음 바로 인터페이스 comparator

 클래스 이름과 implements 키워드 생략, **이름없는 클래스로 객체 생성**

 <br>

 ```java
Collections.sort(정렬할 객체, new Comparator<T> {
    @Override
    public int compare(Object o1, Object o2) {
        return o1 - o2;
    }
});
 ```

 <br>

**익명 클래스** - 1회성 기능 사용을 위해, 사용하기위해선 클래스를 객체화 할 필요가 있다.

객체지향 프로그래밍 -> 클래스가 필요 -> 클래스를 객체화 -> 실행

<br>

**람다 표현식** 사용 가능

 <br>

 ```java
Collections.sort(정렬할 객체, (o1, o2) -> {
    return o1 - o2;
});
 ```