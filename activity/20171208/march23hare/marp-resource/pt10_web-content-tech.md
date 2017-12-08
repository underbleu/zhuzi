Http & Network Basic 제10장
# 웹 콘텐츠에서 사용하는 기술
book study 발표를 위한 slide.

---

작성자: 임기완 march23hare@gmail.com

summary (blog post)
https://march23hare.github.io/2017/12/05/http-network-basic-1204-ch10/

---

## Web content의 기반은 Hyper Text

- hyper text를 전송하기 위한 protocol(HTTP)로...
- hyper text로 만든 문서(.html)를...

---

## 정적(static) content

- HTML로 정보를 구조화
- CSS로 문서 styling

---

## dynamic HTML

- JavaScript로
- DOM을 조작하여
- HTML element를 동적으로 변경

---

### DOM?

HTML문서가 parse 되면...

- HTML element들로 부터 DOM object들이 만들어 짐
	- DOM을 통해서 JavaScript는 HTML element를 조작
- HTML element hierarchy -> DOM tree

---

## web application

### 오늘날의 web application

program에 의해 동적으로 만들어지는 동적 content를 response

---

### CGI

Common Gateway Interface

- server가 resource로써 갖고 있음
- client 요청에 맞는 html을 동적으로 만듦
- 매 request마다 CGI 실행 -> server 부하

---

### servelet

- JavaEE의 일부
- server process의 일부로 작동 -> server 부하 적음

---

## data 송신에 이용되는 format이나 언어

### XML

- 범용 mark-up 언어
- 쉽게 말해 tagname을 customizing 가능한 html

---

### RSS/Atom

- RSS와 Atom 둘 다 XML을 이용
- news나 blog의 기사 등 갱신 정보를 송신하기 위한 문서 format의 총칭

---

### JSON

JavaScript Object Notation

- 경량 data 기술 언어
- JavaScript와 찰떡궁합
