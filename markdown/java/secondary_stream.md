## 보조 스트림

<br>

Filter Stream, Processing Stram

다른 스트림에 **부가적인 기능**을 제공하는 스트림

보조 스트림 자체적으로는 입출력을 수행할 수 없어 **노드 스트림이 필요**하다.

<br>

### 스트림 체이닝 Stream Chaining

<br>

필요에 따라 여러 **보조 스트림을 연결**해서 사용 가능

<br>

### 보조 스트림 종류

<br>

**byte 스트림을 char 스트림으로 변환**
- - -
- **byte 기반**
  - InputStreamReader
  - OutputStreamReader

<br>

**버퍼링을 통한 속도 향상**
- - -
- **byte 기반**
  - BufferedInputStream
  - BufferedOutputStream

- **char 기반**
  - BufferedReader
  - BufferedWriter
  
<br>

**객체 전송**
- - -
- **byte 기반**
  - ObjectInputStream
  - ObjectOutputStream

<br>

이전 스트림을 생성자의 파리미터에 연결하여 생성한다.

노드 스트림은 언제나 필요하다.

종료 시 보조 스트림의 `close()`를 호출하면 노드 스트림의 `close()` 까지 호출 됨

<br>

### 스트림 결정 과정

<br>

노드 스트림 구성
- 노드가 무엇인가?
- 타입은 문자열 혹은 바이트 인가?
- 방향은 무엇인가?

보조 스트림 구성
- 추가 기능이 필요한가?

<br><br>

### InputStreamReader & OutputStreamWriter

<br>

byte 기반 스트림을 char 기반으로 변경해주는 스트림

문자열을 관리하기 위해서는 byte 단위보다 char 단위가 유리하다.

byte 기반 스트림의 데이터를 지정된 **인코딩의 문자데이터로 변환하는 작업 수행**

Reader/Writer 의 자손

<br>

- `InputStreamReader()`
  - `public InputStreamReader(InputStram in)`

    기본 캐릭터 셋을 이용해, OS에서 사용하는 기본 인코딩의 문자로 변환하는 InputStreamReader를 생성

  - `public InputStreamReader(InputStream in, String charsetName) throws UnsupportedEncodingException`

    charsetName을 이용해 지정된 인코딩을 사용하는 InputStreamReader를 생성

  - `public InputStreamReader(InputStream in, Charset cs)`

    cs를 이용해 InputStreamReader를 생성

- `String getEncoding()`

    InputStreamReader의 인코딩을 알려준다

<br>

- `OutputStreamWriter()`
  - `public OutputStreamWriter(OutputStream out)`

    기본 캐릭터 셋을 이용해, OS에서 사용하는 기본 인코딩의 문자로 변환하는 OutputStreamWriter 생성

  - `public OutputStreamWriter(OutputStream out, String charsetName) throws UnsupportedEncodingException`

    charsetName을 이용해 지정된 인코딩을 사용하는 OutputStreamWriter 생성

  - `public OutputStreamWriter(OutputStream out, Charset cs)`

    cs를 이용해 OutputStreamWriter 생성

- `String getEncoding()`

    OutputStreamWriter의 인코딩을 알려준다

<br><br>

### BufferedInputStream & BufferedOutputStream

<br>

스트림의 **입출력 효율을 높이기 위해** 버퍼를 사용하는 스트림

한 바이트씩 입출력하는 것 보다 버퍼(바이트 배열)를 이용해 한 번에 여러 바이트를 입출력하는 것이 빠르다.

<br>

- `BufferedInputStream()`
  - `public BufferedInputStream(InputStram in)`

    주어진 InputStream 인스턴스를 input source로 크기가 8192인 버퍼를 가지는 BufferedInputStream를 생성

  - `public BufferedInputStream(InputStram in, int size)`

    주어진 InputStream 인스턴스를 input source로 지정된 size 크기의 버퍼를 가지는 BufferedInputStream를 생성

<br>

- `BufferedOutputStream()`
  - `public BufferedOutputStream(OutputStram out)`

    주어진 OutputStram 인스턴스를 output source로 크기가 8192인 버퍼를 가지는 BufferedInputStream 생성

  - `public BufferedOutputStream(OutputStram out, int size)`

    주어진 OutputStram 인스턴스를 output source로 지정된 size 크기의 버퍼를 가지는 BufferedOutputStream 생성

- `flush()`

    버퍼의 모든 내용을 출력소스에 출력한 다음, 버퍼를 비운다.

- `close()`

    `flush()`를 호출해서 버퍼의 모든 내요을 출력소스에 출력하고

    BufferedOutputStream 인스턴스가 사용하던 모든 자원을 반환한다.

<br><br>

### BufferedReader & BufferedWriter

<br>

char 형태의 데이터를 읽기 위한 클래스

**Scanner** - 자동 형변환을 지원하는 등 사용이 간편하지만 속도가 느리다.

**BufferedReader** - 직접 스트림을 구성해야 하지만 속도가 빠르다.

- `BufferedReader()`
  - `public BufferedReader(Reader in)`

    주어진 Reader 인스턴스를 input source로 크기가 8192인 버퍼를 가지는 BufferedReader 생성

  - `public BufferedReader(Reader in, int size)`

    주어진 Reader 인스턴스를 input source로 지정된 size 크기의 버퍼를 가지는 BufferedReader 생성
    
- `readLine()`

    줄 단위로 데이터를 읽어들인다.

<br>

- `BufferedWriter()`
  - `public BufferedWriter(Writer out)`

    주어진 Writer 인스턴스를 output source로 크기가 8192인 버퍼를 가지는 BufferedWriter 생성

  - `public BufferedWriter(Writer out, int size)`

    주어진 Writer 인스턴스를 output source로 지정된 size 크기의 버퍼를 가지는 BufferedWriter 생성

- `newLine()`

    줄바꿈을 출력