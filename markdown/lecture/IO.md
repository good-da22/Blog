## IO

## #7

하나 씩 읽어오는 것은 비효율적

프로그램 성능 개선시 IO는 주요 문제

close 자원을 반납하지 않으면 부화 가능, 한 번 사용한 스트림은 닫아줘여한다.

언제나 close 해야한다. finally에서 처리

## #13

디렉토리도 파일이다.

## #16
파일 세퍼레이터, 각각의 운영체제에 맞게 구분자 설정

Filrwriter(파일, true) // 계속 이어서 쓰겠다. append true

## #28

implements Serializable { // 직렬화 가능 표시, 추가 구현 메서드 없음

@SuppressWarnings("serial") //최대한 안쓰는게 좋다