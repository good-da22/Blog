## List

<br>

**중복을 허용** 하면서 **저장순서 유지**

<br>

### **List Inferface** 주요 메서드

<br>

#### 추가
- - -
- `void add(int index, Object element)`
    
    지정된 위치(index)에 **객체(element) 추가**
- `boolean addAll(int index, Collection<? extends E> c)`

    지정된 위치(index)에Collection **객체를 추가**

    작업을 성공하면 true, 그렇지 않으면 false

<br>

#### 조회
- - -
- `Object get(int index)`
  
    지정된 위치(index)에 있는 **객체를 반환**
- `int indexOf(Objec o)`
    
    지정된 객체의 위치(index)를 List의 **첫 번째 요소**부터 찾아 반환
- `int lastIndexOf(Object o)`
    
    지정된 객체의 위치(index)를 List의 **마지막 요소**부터 찾아 반환
- `ListIterator listIterator()`
    
    List 객체에 접근할 수 있는 **ListIterator**를 반환
  
<br>

#### 삭제
- - -
- `Object remove(int index)`
  
    지정된 위치(index)에 있는 객체를 삭제하고 **삭제된 객체를 반환**

<br>

#### 수정
- - -
- `Object set(int index, Object element)`
  
    지정된 위치(index)에 **객체(element)를 저장**

<br>

#### 기타
- - -
- `List subList(int fromIndex, int toIndex)`
  
    지정된 범위(fromaIndex ~ toIndex)에 있는 **객체를 List**로 반환

- `void sort(Comparator c)`
    
    지정된 비교자(comparator)로 List를 **정렬**

<br><br>

### ArrayList

<br>

**배열의 장점**
- 가장 기본적인 형태의 자료구조, 간단하며 사용이 쉽다.
- 인덱스를 통해 접근 속도가 빠르다.

<br>

**배열의 단점**
- 크기를 변경할 수 없다.
- 추가 데이터를 위해 새로운 배열을 만들고 복사해야한다.
- 비 순차적 데이터 추가, 삭제에 많은 시간이 걸림

<br>

배열을 사용하는 **ArrayList** 역시 배열의 장단점을 가져간다.

Object 배열을 사용해 데이터를 순차적으로 저장

배열에 저장할 공간이 없으면 보다 **큰 새로운 배열**을 생성에 기존의 배열에 저장된 내용을 **새로운 배열로 복사한 다음 저장**

<br>

#### 자료 삭제 시 주의 사항

<br>

```java
for (int i = 0; i < 리스트 길이; i++) {
    if (삭제 조건) {
        리스트.remove(i);
        i--;
    }
}
```

<br>

요소가 삭제될 때마다 **빈 공간을 채우기 위해 나머지 요소들이 자리 이동**

**제어변수를 감소(index 차감)** 하며 삭제해야 자리이동이 발생해도 영향을 받지 않고 작업이 가능

<br>

마지막 요소부터 접근해 자연스럽게 해결 가능

```java
for (int i = 리스트 길이; i >= 0; i--) {
    if (삭제 조건) {
        리스트.remove(i);
    }
}
```

<br>

### forEach 문 사용 주의사항

<br>

forEach 문은 Collection **크기가 변하면 안된다.**

잘못된 인덱스에 접근하여 예외 발생 가능

추가, 삭제 없이 조회 시에만 사용 (읽기 전용)

```java
for (객체 타입 : 리스트) {
    // 리스트.add() 금지
    // 리스트.remove() 금지
}
```

<br><br>

### LinkedList

<br>

각 요소를 **Node**로 정의하고 Node는 **다음 요소의 참조 값** 과 **데이터**로 구성된다.

각 요소가 다음 요소의 **링크 정보**를 가지며 **연속적으로 구성될 필요가 없다.**

**데이터가 많아질수록** 데이터를 읽어오는 **접근시간(access time)이 길어진다.**

<br><br>

### ArrayList vs LinkedList

<br>

- **순차적**으로 추가 / 수정 / 삭제하는 경우
  
    **ArrayList 가** LinkedList 보다 **빠르다.**

- **비 순차적(중간 데이터)** 으로 추가 / 수정/ 삭제하는 경우

    **ArrayList 가** LinkedList 보다 **느리다.**

- **조회**하는 경우

    **ArrayList 가** LinkedList 보다 **빠르다.**

<br>

사용 목적에 따라 선택

소량의 데이터를 사용할 경우 유의미한 차이는 없다.

<br>

**정적**인 데이터 활용, 단순히 데이터 **조회** : **ArrayList**

**동적**인 데이터 추가, 삭제가 많은 작업 : **LinkedList**

<br><br>

## 정렬 sort

<br>

Collection 정렬을 위해선 데이터의 순서를 가지고 있어야 한다.