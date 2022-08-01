## 표준 입출력

<br>

- System.in
- System.out
- System.err

<br>

대상 변경

- System.setOut()
- System.setErr()
- System.setIn()

<br>

### java.util.Scanner

<br>

파일, 입력 스트림등에서 데이터를 읽어 구분자로 토큰화

다양한 타입으로 형변환하여 리턴하는 클래스

- Scanner(File source)
- Scanner(InputStream source)
- Scanner(String source)

입력 스트림을 다루는 방법을 몰라도 쉽게 입력처리 가능

데이터 형변환으로 인한 편리함

대량의 데이터 처리 시 수행시간 비효율적

<br>

### Scanner 주요 메서드

<br>

- `nextInt()`

    int 타입 반환

    유효 문자열 후 White space 문자를 만나면 처리

    유효 데이터가 식별이되면 구분자를 만날 때 까지 읽는다.

    구분자는 남긴다.

- `nextDouble()`

    double 타입 반환

    유효 문자열 후 White space 문자를 만나면 처리

- `next()`

    문자열 반환

    유효 문자열 후 White space 문자를 만나면 처리

- `nextLine()`

    문자열 반환

    개행(Enter) 문자를 만나면 처리

    개행 문자까지 읽어와 개행 문자는 버리고 준다.

    `next()`와 달리 문자열 안에 띄어쓰기 가능(space, tab 포함 가능)

<br>

### java.io.BufferedReader

<br>

char 타입 기반

필터 스트림 유형, 입출력 처리할 노드 스트림 필요

줄(line) 단위로 문자열 처리 기능 제공

대량의 데이터 처리 시 수행시간이 효율적

<br>

### java.lang.StringBuilder

<br>

문자열의 조작을 지원하는 클래스

자바에서 상수로 취급되는 문자열을 조작 시마다 새로운 문자열이 생성되는 것을 방지

`append()`

`toString()`

