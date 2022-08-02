## File 

<br>

가장 기본적인 입출력 장치

**파일과 디렉토리**를 다루는 클래스

디렉토리도 파일이다.

<br>

### File 주요 메서드

<br>

- `File()`
  - `public File(String pathname)`

    pathname에 해당하는 파일을 생성

    경로 없이 파일을 생성하면 애플리케이션을 시작한 경로가 된다.

  - `public File(String parent, String child)`

    parent 경로 아래 child 를 생성한다.

  - `public File(File parent, String child)`

    parent 경로 아래 child 를 생성한다.

  - `public File(URI uri)`

    file 로 시작하는 URI 객체를 이용해 파일을 생성한다.

<br>

- `createNewFile()`
  - `public boolean createNewFile() throws IOException`

    새로운 물리적인 파일을 생성한다.

<br>

- `mkdir()`
  - `public boolean mkdir()`

    새로운 디렉토리를 생성한다.

- `mkdirs()`
  - `public boolean mkdirs()`

    경로상에 없는 모든 디렉토리를 생성한다.

<br>

- `delete()`
  - `public boolean delete()`

    파일 또는 디렉토리를 삭제한다.

<br>

- `getName()`
  - `public String getName()`

    파일의 이름을 반환한다.

- `getPath()`
  - `public String getPath()`

    파일의 경로를 반환한다.

- `getAbsolutePath()`
  - `public String getAbsolutePath()`

    파일의 절대 경로를 반환한다.

- `getCanonicalpath()`
  - `public String getCanonicalPath() throws IOException`

    파일의 정식 경로를 반환한다.

    정식 경로는 절대 경로로 경로 내에 . 또는 .. 의 상대 경로 기호가 없는 경로

<br>

- `isDirectory()`
  - `public boolean isDirectory()`

    파일이 디렉토리인지 여부를 반환한다.

- `isFile()`
  - `public boolean isFile()`

    파일이 파일인지 여부를 반환한다.

<br>

- `length()`
  - `public long length()`

    파일의 길이를 반환한다.

- `listFiles()`
  - `public Flie[] listFlies()`

    파일이 디렉토리인 경우 자식 파일들을 File[] 형태로 반환한다.

<br><br>

### FileInputStream 과 FileOutputStream

<br>

- `FileInputStream()`
  - `public FileInputStream(String name) throws FileNotFoundException`

    name 경로의 파일을 읽는 FileInputStream 을 생성한다.

- `FileOutputStream()`
  - `public FileOutputStream(String name) throws FileNotFoundException`

    name 경로의 파일을 출력하는 FileOutputStream 을 생성한다.

  - `public FileOutputStream(String name, boolean append) throws FileNotFoundException`

    name 경로의 파일에 출력하는 FileOutStream 을 생성한다.

    기존에 파일이 있다면 뒤에 이어 쓴다.
