## SSE(Server-Sent Events)

클라이언트가 HTTP 연결을 통해 서버에서 자동 업데이트를 수신할 수 있도록 하는 server push 기술

클라이언트는 event-strem을 받기 위해 특정 URL을 요청하고 최초 요청 이후 서버는 일정시간 동안 변경 이벤트를 연결된 클라이언트에게 자동으로 보내준다.

브라우저 기반 애플리케이션 기술로 브라우저 클라이언트에 message update 또는 연속 data stream을 보내는데 사용된다.

JavaScript의 EventSource API의 경우 `HTTP persistent connections` 기반 HTML5 표준 기술이다.

