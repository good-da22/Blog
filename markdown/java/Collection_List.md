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

배열에 저장할 공간이 없으면 보다 큰 새로운 배열을 생성에 기존의 배열에 저장된 내용을 새로운 배열로 복사한 다음 저장