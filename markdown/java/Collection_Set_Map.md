## Set

<br>

**순서를 유지하지 않고** 데이터 **중복을 허용하지 않는다.**

<br>

순서가 없어 데이터를 구별한 **Index**가 없어 **중복이 허용되지 않는다.**

동일한 데이터(객체)의 `equals()`는 `true`를 리턴하고 `hashCode()`값이 **같다.**

Set은 **Index가 없어** `remove()`를 통해 살제할 때 동일한 객체르 매개변수로 넘겨줘야 한다.

<br><br>

## Map

<br>

데이터를 **키(key)** 와 **값(value)** 를 하나의 **Entry**로 묶어서 하나의 쌍(pair)으로 관리한다.

<br>

### Key

<br>

Object 형태로 데이터 **중복을 허락하지 않는다.**

<br>

### Valur

<br>

Object 형태로 데이터 **중복을 허락한다.**

<br>

### Map 주요 메서드

<br>

#### 추가
- - -
- `put(K k, V vlaue)`
    
    key와 value는 Generic 타입, 어떤 타입이든 사용 가능
- `put(Map <? extends K, ? extends V> m)`

    설명

<br>

#### 조회
- - -
- `boolean containKey(Object key)`
  
    설명
- `boolean containValue(Object value)`
  
    설명
- `entrySet()`
  
    설명
- `keySet()`

    key에 해당하는 객체들만  Set에 담아서 반환
- `get(Object key)`

    매개변수로 주어진 key에 해당하는 value를 가져온다.
- `values()`

    설명
- `size()`
  
    Map의 행(Entry)의 개수
- `isEmpty()`
  
    설명

<br>

#### 삭제
- - -
- `clear()`

    설명
- `remove(Object key)`
  
    설명

<br>

#### 수정
- - -
- `put(K key, V value)`

    해당하는 key에 새로운 value
- `putAll(Map<? extends K, ? extends V> m)`
  
    설명
