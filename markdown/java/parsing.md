## Parsing

<br>

문서에서 필요한 정보를 얻기 위해 태그를 구별하고 내용을 추출하는 과정

전문적인 parser 활용

<br>

**SAX parser**

Simple API for XML parser

**문서를 읽으면서** 태그의 시작, 종료 등 이벤트 기반으로 처리하는 방식

**빠르고** 한번에 처리하기 때문에 **다양한 탐색이 어렵다.**

**DOM parser**

Document Object Model

문서를 다 읽고 난 후 문서 구조 전체를 자료구조에 저장하여 탐색하는 방식

**다양한 탐색이 가능**하지만 **느리고 무거우며** **큰 문서를 처리하기 어렵다.**

<br>

### SAX(Simple API for XML) parser

<br>

문서를 읽다가 발생하는 **이벤트 기반**으로 문서 처리


![SAX parser](../../img/inner%20ing/sax_parser.png)

**SAX Parser Factory** : SAX Parser 생성

**SAX Parser** : 문서 parsing (DefaultHandler 참조)

**DefaultHandler** : 필요한 메서드 정의

**MyHandler** : DefaultHandler 메서드 중 필요 부분 재정의(Overrinding)

<br>

### DOM(Document Object Model) parser

<br>

문서를 완전히 메모리에 로딩 후 필요한 내용 탐색

![Dom parser](../../img/inner%20ing/dom_parser.png)

**Document Builder Factory** : Document Builder 생성

**Document Builder** : 문서 parsing, DOM Tree 구성

**DOM Tree** : **business logic**, 문서를 구성하는 모든 요소를 **Node(태그, 속성, 값)로 구성**, 
 태그들은 root node를 시작으로 **부모 - 자식 관계** 구성