## JAVA NFC

java의 javax.smartcardio 라이브러리를 이용한 nfc writer 구현

<br>

### NFC란?

무선태그(RFID) 기술 중 하나로 **비접촉식 통신 기술**

근거리 무선 통신 (**N**ear **F**ield **C**ommunication, **NFC**)으로 13.56MHz의 대역을 가지며

아주 가까운 거리(접촉 및 근접 비접촉(약 10cm) 포함)의 무선 통신을 하기 위한 기술

<br>

모드에 따라 쓰기(write)와 읽기(read)가 가능하며 대부분의 스마트폰에서 NFC 기능을 제공한다.

양방향 통신으로 상대 기기로 정보를 주기도 하며 상대 기기에서 정보를 가져오기도 한다.

<br>

### Java smartcard I/O API



```java
// java smartcardio NFC Write example code

public class NfcWrite {

    public static void nfcWriter(String value) {
        try {
            // Get the default terminal
            TerminalFactory factory = TerminalFactory.getDefault();
            List<CardTerminal> terminals = factory.terminals().list();
            CardTerminal terminal = terminals.get(0);

            // Connect to the card
            Card card = terminal.connect("");
            CardChannel channel = card.getBasicChannel();

            // Write data to the NFC device
            byte[] data = value.getBytes();
            byte[] header = new byte[] {
                    (byte) 0xFF, // Class
                    (byte) 0xD6, // INS, 0x00
                    (byte) 0x00, // P1
                    (byte) 0x00, // P2
                    (byte) data.length, // Length
            };

            // Send the command to the device
            byte[] apdu = new byte[header.length + data.length];

            // header copy to apdu
            System.arraycopy(header, 0, apdu, 0, header.length);
            // data copy to apdu
            System.arraycopy(data, 0, apdu, header.length, data.length);

            ResponseAPDU response = channel.transmit(new CommandAPDU(apdu));

            // check response status
            if(response.getSW() == 0x9000) {
                log.info("Data write Success");
            }
            else {
                log.info("Data write Fail");
            }

            // Disconnect from the card
            card.disconnect(true);

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

- `TerminalFactory`

    `getDefault()` 또는 `getInstance()` 메소드를 통해 `TerminalFactory` 객체를 얻을 수 있다.

    `terminals()` 메소드를 통해 `CardTerminals`에 접근 가능

- `CardTerminal`

    Smart Card terminal 또는 Smart Card Reader 라고 한다.

    `CardTerminals.list()` 또는 `CardTerminals.getTerminal()`을 통해 객체를 얻을 수 있다.

    `connect(String protocol)` 메소드를 통해 `Card`에 대한 연결을 설정

    이전에 설정된 protocol이 있다면 이를 통해 연결된다.

    `("T=0", "T=1", or "T=CL")` 또는 `("*")` 사용한다.

- `Card`

    연결이 설정된 Smart Card

    `CardTerminal.connect(String protocol)`을 통해 객체를 얻는다.

    `getBasicChannel()` 메소드를 통해 basci logical channel에 대한 `CardChannel`을 얻을 수 있다.

    `disconnect(boolean reset)` 메소드를 통해 현재 카드와 연결을 종료한다.

    연결 해제 이후 해당 객체와 연결된 `CardChannels`에서 메소드를 호출하면 `IllegalStateException` 발생

    `boolean reset`을 통해 연결 해제 후 카드 재설정 여부를 설정

- `CardChannel`
  
    Smart Card에 대한 logical clannel connection

    Smart Card와 APDU(Application Protocol Data Unit)를 교환하는데 사용

    `Card.getBasicChannel()` 또는 `Card.openLogicalChannel()`을 통해 객체를 얻는다.

    `transmint(CommandAPDU command)` 메소드를 통해 특정 command APUD를 전송하고 response APDU를 반환한다.

    command APDU의 CLA byte는 해당 `CardChannel`의 채널 번호와 일치하도록 자동 조정된다.

    전송 프로토콜에 따라 투명하게 처리해야 한다.

    retrun 되는 `ResponseAPUD`는 해당 처리가 수행된 후의 결과


- `CommandAPDU`

    ISO/IEC 7816-4에 정의된 구조를 따른다.

    4byte header와 가변 길이의 조건부 body로 구성된다.

    해당 클래스는 APDU가 의미론적으로 유효한 명령을 인코딩하는지는 확인하지 않는다.

    데이터 규격과 NFC 태그에 쓰고자하는 주소에 맞춰서 header를 구성해야 한다. 현 예제는 ACR122U, mifare ultralight C를 사용한다.

    header byte CLA, INS, P1, P2의 경우 8bit unsigned value를 사용한다.

    해당 클래스의 인스턴스는 변경할 수 없으며 바이트 배열을 통해 데이터가 들어오거나 나가는 경우 defensive cloning(방어 복제)가 수행된다.

- `ResponseAPDU`

    ISO/IEC 7816-4에 정의된 구조를 따른다.

    조건부 body와 2 byte trailer로 구성된다.

    해당 클래스가 APDU가 의미론적으로 유효한 응답을 인코딩하는지 확인하지 않는다.

    `getSW()` 메소드

    status byte(상태 바이트) SW1과 SW2를 하나의 SW(status word)로 반환한다.





<br>

#### Reference

[Java Smart Card I/O docs](https://docs.oracle.com/javase/8/docs/jre/api/security/smartcardio/spec/javax/smartcardio/package-summary.html)

[ORACLE, An Introduction to Java Card Technology - Part 1](https://www.oracle.com/java/technologies/java-card/javacard1.html)