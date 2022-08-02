## I / O

<br>

Input 과 Output, 데이터의 **입력과 출력**

<br><br>

## Stream

<br>

데이터는 한 쪽에서 주고 한 쪽에서 받는 구조로 되어있다.

이때, 입력과 출력의 끝단 : **노드(Node)**

두 노드를 연결하고 데이터를 전송할 수 있는 개념 : **스트입(Stream)**

스트림이란 데이터를 운반하는데 사용되는 연결 통로

스트림은 **단방향 통신만 가능**하기 때문에 하나의 스트림으로 입력과 출력을 동시에 처리할 수 없다.

입력과 출력을 동시에 수행하려면 입력을 위한 **입력스트림(input stream)**과 출력을 위한 **출력스트림(output stream)**, 모두 2개의 스트림이 필요하다.

스트림은 먼저 보낸 데이터를 먼저 받게 되어 있어 중간에 건너뜀 없이 **연속적으로 데이터를 주고받는다.**

<br><br>

### Node Stream 종류

<br>

**데이터 타입에 따라**

<br>

**byte** 타입
- - -
- **InputStream**
  - **KeyBoard** - InputStream
  - **File** - FileInputStream
  - **Byte** - ByteArrayInputStream
  - **Pipe** - PipedInputStream
  - **Audio** - AudioInputStream

<br>

- **OutputStream**
  - **Monitor** - OutputStream
  - **File**-  FileOutputStream
  - **Byte** - ByteArrayOutputStream
  - **Pipe** - PipedOutputStream
  - **Audio** - AudioOutputStream
  
<br>

**char** 타입
- - -
- **Reader**
  - **KeyBoard** - Reader
  - **File** - FileReader
  - **Char** - CharArrayReader
  - **String** - StringReader
  - **Pipe** - PipedReader

<br>

- **Writer**
  - **Monitor** - Writer
  - **File** - FileWriter
  - **Char** - CharArrayWriter
  - **String** - StringWriter
  - **Pipe** - PipedWriter

<br>

하나씩 읽어오는 것은 비효율적

**프로그램 성능 개선시 IO는 주요 문제**

close 자원을 반납하지 않으면 부화 가능, **한 번 사용한 스트림은 닫아줘여한다.**

언제나 close 해야한다. **finally에서 처리**

<br><br>

### InputStream 주요 메서드

<br>

- `read()`
  - `public abstract int read() throws IOException`

    byte 하나를 읽어서 int로 변환한다. 더 이상 읽을 값이 없으면 -1을 반환한다.

  - `public int read(byte b[]) throws IOException`

    데이터를 읽어서 b 를 채우고 읽은 byte 개수를 반환한다.
    
    0이 반환되면 더 이상 읽을 값이 없는 상태이다.

  - `public int read(byte b[], int offset, int len) throws IOException`

    최대 len 만큼 데이터를 읽어서 b 의 offset 부터 b 에 저장하고 읽은 byte 개수를 반환한다.

    len + offset 은 b 의 크기 이하여야 한다.

<br>

- `close()`
  - `public void close() throws IOException`
  
    스트림을 종료해서 자원을 반납한다.

<br><br>

### OutputStream 주요 메서드

<br>

- `write()`
  - `public abstract void write(int b) throws IOException`
    
    b 의 내용을 byte로 출력한다.

  - `public void write(byte b[]) throws IOException`
    
    b 를 문자열로 변환해서 출력한다.

  - `public void write(byte b[], int off, int len) throws IOException`
  
    b 의 off 부터 off + len - 1 만큼을 문자열로 변환해서 출력한다.

<br>

- `close()`
  - `public void close() throws IOException`

    스트림을 종료해서 자원을 반납한다.

    `close()`는 내부적으로 `flush()`를 호출한다.

<br>

- `flush()`
  - `public void flush() throws IOException`
  
    버퍼가 있는 스트림에서 버퍼의 내요을 출력하고 버퍼를 비운다.

<br><br>

### Reader 주요 메서드

<br>

- `read()`
  - `public int read() throws IOException`
    
    char 하나를 읽어서 int 로 변환한다.

    더 이상 읽을 값이 없으면 -1 을 반환한다.

  - `public int read(char cbuf[]) throws IOException`

    데이터를 읽어서 cbuf 를 채우고 읽은 문자의 개수를 반환한다.

    0 이 반환되면 더 이상 읽은 값이 없는 상황이다.

  - `public abstract int read(char cbuf[], int offm int len) throws IOException`

    최대 len 만큼 데이터를 읽어서 cbuf 의 offset 부터 cbuf 에 저장하고 읽은 char 개수를 반환한다.

    따라서 len + off 는 cbuf 의 크기 이하여야 한다.

  - `public int read(java.nio.CharBuffer target) throws IOException`

    데이터를 읽어서 target 에 저장한다.

    target 은 cbuf 를 대체한다.

<br>

- `close()`
  - `public void close() throws IOException`

    스트림을 종료해서 자원을 반납한다.

<br>

### Writer 주요 메서드

<br>

- `write()`
  - `public void write(int c) throws IOException`

    b 의 내용을 char로 출력한다.

  - `public void write(char cbuf[]) throws IOException`

    cbuf를 문자열로 변환해서 출력한다.

  - `public abstract void write(char cbuf[], int off, int len) throws IOException`

    cbuf 의 off 부터 off + len - 1 만큼 문자열로 변환해서 출력한다.

  - `public void write(String str) throws IOException`

    str 을 출력한다.

  - `public void write(String str, int off, int len) throws IOException`

    str 의 off 부터 off + len - 1 만큼 출력한다.

<br>

- `append()`
  - `public Writer append(CharSequence csq) throws IOException`

    csq 를 출력하고 Writer 를 반환한다.

  - `public Writer append(CharSequence csq, int start, int end) throws IOException`

    csq 의 start 부터 end 까지 출력하고 Writer 를 반환한다.

<br>

- `close()`
  - `public void close() throws IOException`

    스트림을 종려해서 자원을 반납한다.

    `close()` 는 내부적으로 `flush()` 를 호출한다.

<br>

- `flush()`
  - `public abstract void flush() throws IOException`
  
    버퍼가 있는 스트림에서 버퍼의 내용을 출력하고 버퍼를 비운다.