Http & Network Basic 제9장
# HTTP에 기능을 추가한 프로토콜
book study 발표를 위한 slide.

---

작성자: 임기완 march23hare@gmail.com

summary (blog post)
https://march23hare.github.io/2017/12/04/http-network-basic-ch09-new-protocol/

---

## protocol과 각각의 keyword

- SPDY[스피디]: 병목현상 해결
- WebSocket: 양방향 통신
- HTTP/2.0: 차세대
- WebDAV: server상의 file 관리

---

## SPDY

HTTP 병목현상 해결

---

### HTTP 병목현상의 원인

- 1 connection : 1 request
- no request no response
- 너무 장황한 header, 압축은 option

---

### 병목현상 해결을 위한 기존의 기술들
- Ajax: 비동기 통신, HTML 문서 일부분만 동적 변경
- Comet: server 갱신 전까지 response 보류하여 server 변경사항을 실시간 push해 주는 효과.

그러나 HTTP 자체의 단점은 여전히 존재

---

### SPDY는 어디에?

![SPDY-Stack.png](img/SPDY-Stack.png)

---

### SPDY는 뭘 해주지?

- **다중화 stream**
- server push & server hint
- HTTP request 압축
- request 우선순위 부여

---

![shadow_clone.jpg](img/shadow_clone.jpg)

---

### SPDY의 한계

- 하나의 web site에서 여러 domain의 resource 사용시 다중화 stream으로 부터의 이점이 미미.

---

## WebSocket

양방향 통신

---

### WebSocket은 뭘 해주지?

- server push
- 통신량 삭감
	- handshake로 한 번 접속이 발생하면 이를 유지함
	- header의 크기 자체가 작음

---

### handshake?

- client의 request
	- upgrade: WebSocket
- server의 response 101 switching protocol
	- protocol이 HTTP에서 WebSocket으로 전환 됨.
	- 독자적인 data frame을 사용하게 됨.

---

## HTTP/2.0

차세대 HTTP로 논의 중.

---

### HTTP2.0의 base

- SPDY
- HTTP Speed+Mobility
- Network-Friendly HTTP Upgrade

---

### HTTP/2.0에서 논의 되는 7가지 기술

- 다중화
- TLS 의무화
- negotiation
- client pull / server push
- 흐름 제어
- WebSocket

---

## WebDAV

server file 관리

- Web-based
- Distributed
- Authoring and
- Versioning

---

### WebDAV 추가 된 개념

- collection: resource들의 묶음 입니다. method를 통한 처리의 단위가 됩니다.
- resource: 쉽게 말하면, server 상의 file 입니다만 collection도 resource의 일종입니다. cliet가 요청 하는 대상이 됩니다.
- property: resource의 속성을 나타냅니다. '이름=값' 쌍의 list 입니다.
- lock: resource의 상태를 lock으로 하면 편집 불가능해 집니다. 동시 편집을 배제 하기 위해 사용 됩니다.

---

### WebDAV 추가 된 method

- PROPFIND: property 취득
- PROPPATCH: property 변경
- MKCOL: collection 생성
- COPY: resource 및 property 복사
- MOVE: resource 이동
- LOCK: resource 잠금
- UNLOCK: resource 잠금 해제

---

### WebDAV 추가 된 method 상태 code

- 102 Processing: request 처리중
- 207 Multi-Status: 복수의 status를 갖고 있음을 나타냄
- 422 Unprocessable Entity: 서식은 올바르나 내용이 그름
- 423 Locked: resource가 잠겨 있음
- 424 Failed Dependency: 관련된 request의 실패로 의존성을 유지 할 수 없음
- 507 Insufficient Storage: 저장 공간이 부족함

---

## HTTP가 이렇게 까지 많이 사용 되는 이유?

web access를 공공/사 기관에서 가장 많이 허용하고 있기 때문.