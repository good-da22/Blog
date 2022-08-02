## Collection Framework

<br>

### 자료구조 (data structure)

<br>

컴퓨터 과학에서 효율적인 접근 및 수정을 가능하게 하는 자료의 조직, 관리, 저장을 의미

**데이터 값의 모임, 데이터 간의 관계, 데이터에 적용 가능한 함수나 명령**을 의미

<br><br>

### 배열

<br>

**homogeneous collection** : 동일한 데이터 타입만 관리

타입이 다른 객체를 관리하기 위해서는 매번 다른 배열이 필요

<br><br>

### 컬렉션

<br>

데이터 군(**Collection**)을 저장하는 클래스들을 표준화한 설계(**Framework**)

<br>

**다형성 (Polymorphism)**

Object을 이용하면 모든 객체 참조 가능 -> **Collection Framework**

담을 때는 편리, 빼낼 때는 Object로만 가져올 수 있다.

**런타임에 실제 객체 타입을 확인** 후 사용해야하는 번거러움 존재

**Generic**을 이용해 타입 한정

컴파일 타임에 저장하려는 타입 제한 -> **형변환 번거로움 제거**

<br><br>

### 핵심 인터페이스

<br>

**컬렉션 프레임워크**에서는 컬렉션데이터 그룹을 크게 **3가지 타입**이 존재한다고 인식

각 컬렉션을 다루는데 필요한 기능을 가진 **3개의 인터페이스**를 정의

그 중 **List**와 **Set**의 공통 부분을 뽑아 새로운 인터페이스 **Collection** 정의

<br>

#### List
---
- **순서**가 있는 데이터 집합
- 데이터 **중복을 허용**
- ex) 일렬로 줄 선 대기자
- 구현 클래스 : ArrayList, LinkedList, Stack, Vector

<br>

#### Set
---
- **순서를 유지하지 않는** 데이터 집합
- 데이터 **중복을 허용하지 않는다.**
- ex) 양의 정수 집합, 소수의 집합
- 구현 클래스 : HashSet, TreeSet

<br>

#### Map
---
- **키(key)** 와 **값(value)** 의 쌍(pair)로 이루어진 데이터 집합
- **순서를 유지하지 않는** 데이터 집합
- **키(key)** 는 중복을 허용하지 않는다.
- **값(value)** 은 중복을 허용한다.
- ex) 우편번호, 지역번호
- 구현 클래스 : HashMap, TreeMap, Hashtable, Properties

<br><br>

### Collection Inferface 주요 메서드

<br>

**List** 와 **Set** 의 조상 인터페이스

#### 추가
---
- `boolean add(E e)` 
  
    지정된 객체를 **Collection에 추가**
  
    작업을 성공하면 true, 그렇지 않으면 false
- `boolean addAll(Collection<? extends E> c)`
    
    Collection 객체를 **Collection에 추가**
    
    작업을 성공하면 true, 그렇지 않으면 false

<br>

#### 조회
- - -
- `boolean contains(Object o)` 

    지정된 객체가 **Collection에 포함 되어 있는지 확인**

    작업을 성공하면 true, 그렇지 않으면 false
- `boolean containsAll(Collection<?> c)`

    Collection 객체가 **Collection에 포함 되어 있는지 확인**
  
    작업을 성공하면 true, 그렇지 않으면 false
- `boolean equals(Object o)`

    **동일한 Collection** 인지 비교

    작업을 성공하면 true, 그렇지 않으면 false
- `boolean isEmpty()`

    **Collection이 비어있는지** 확인

    비어있으면 true, 그렇지 않으면 false
- `iterator iteratir()`

    Collection의 **iterator**를 얻어서 반환
- `int size()`

    Collection에 **저장된 객체의 개수**를 반환

<br>

#### 삭제
- - -
- `void clear()`
  
    Collection의 **모든 객체를 삭제**
- `boolean remove(Object o)`

    **지정된 객체를 삭제**

    작업을 성공하면 true, 그렇지 않으면 false
- `boolean removeAll(Collection<?> c)`
    
    지정된 Collection의 **모든 객체를 삭제**

    작업을 성공하면 true, 그렇지 않으면 false
- `boolean retainAll(Collection<?> c)`
    
    지정된 Collection에 포함된 객체를 남기고 **다른 객체들은 Collection에서 삭제**
    
    작업을 통해 Collection에 변화가 있으면 true, 없으면 false 반환

<br>

#### 기타
- - -
- `Object[] toArray()`
  
    Collection에 저장된 객체를 **객체배열로 반환**
- `Object[] toArray(Object[] a)`
    
    지정된 **배열에 Collection 객체를 저장**해서 반환