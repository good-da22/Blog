## 객체 직렬화 Serialization

<br>

### 직렬화(serialization)

<br>

객체를 데이터 스트림으로 만드는 것

객체를 파일등에 저장하거나 네트워크로 전송하기 위해 연속적인 데이터로 변환하는 것

<br>

### 역 직렬화(deserialization)

<br>

직렬화의 반대로 스트림으로부터 데이터를 읽어서 객체를 만드는 것

<br>

### 직렬화 조건

<br>

**java.io.Serializable 인터페이스**를 구현해야 한다.

추가 구현 메서드는 없다

@SuppressWarnings("serial") 경고를 무시할 수 있지만 사용하지 말 것

**Serializable를 구현하는 클래스를 상속**받는다면, 자식 클래스에서는 Serializable을 구현하지 않아도 된다.

부모 클래스가 Serializable을 구현하지 않은 상태에서 **자식 클래스가 Serializable을 구현**하여 직렬화할 경우 **부모 클래스의 인스턴스 변수는 직렬화 대상에서 제외**된다.

Serializable을 구현하였지만 **직렬화할 수 없는 클래스의 객체를 인스턴스 변수로 참조**하는 경우 **NoSerializableException**이 발생한다.

Object 클래스는 Serializable를 구현하지 않아 직렬화 할 수 없다.

인스턴스 변수의 타입이 아닌 **실제로 연결된 객체의 종류**에 의해서 직렬화 여부가 결정된다.

<br>

직렬화하고자 하는 객체의 클래스에 직렬화가 안 되는 객체에 대한 참조를 포함하는 경우

`transient` 키워드를 통해 직렬화 대상에서 제외 가능

<br>

### serialVersionUID

<br>

클래스의 변경 여부를 파악하기 위한 유일 키

객체가 직렬화 할 때 클레스에 정의된 멤버들의 정보를 이용해 **serialVersionUID라는 클래스의 버전**을 자동생성해서 **직렬화 내용에 포함**

직렬화 할 떄의 UID와 역 직렬화 할 떄의 **UID가 다를 경우 예외 발생**

직렬화되는 객체에 UID가 설정되지 않았을 경우 **컴파일러가 자동 생성**

**멤버 변경**으로 인한 컴파일 시마다 변경 -> InvalidClassException 발생

직렬화되는 객체에 대해서 serialVersionUID 설정 권장

<br><br>

### ObjectInputStream & ObjectOutputStream

<br>

InputStream 과 OutputStram을 직접 상속받지만 노드 스트림을 필요로 하는 보조 스트림

객체를 생성할 때 입출력(직렬화/역직렬화)할 스트림을 지정 필요

<br>

- `ObjectInputStream()`
  - `public ObjectInputStream(InputStram in) throws IOException`

    주어진 InputStream 인스턴스를 input source로 ObjectInputStream  생성

- `readObject()`
  - `public final Object readObject() throws IOException, ClassNotFoundException`

    직렬화된 데이터를 역직렬화해서 Object로 반환

<br>

- `ObjectOutputStream()`
  - `public BufferedOutputStream(OutputStram out) throws IOException`

    주어진 OutputStram 인스턴스를 output source로 ObjectOutputStream 생성

- `writeObject()`
  - `public final Object writeObject(Object obj) throws IOException, ClassNotFoundException`

    obj를 직렬화해서 출력