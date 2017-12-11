<!-- $theme: default -->

Http & Network Basic 제11장
# 웹 공격 기술
book study 발표를 위한 slide.

---

작성자: 임기완 march23hare@gmail.com

summary (blog post)
https://march23hare.github.io/2017/12/05/http-network-basic-1203-ch11-attk/

---

## HTTP의 보안상 문제점

- 완전성 증명 기능이 없어 변조 가능
- 평문이라 도청 가능
- 인증 기능이 없어 송신측 위장 가능

---

## web application 공격 type

- 능동적 공격(active attack): server를 노린 공격
  - SQL injection
  - OS command injection
- 수동적 공격(passive attack): user를 노린 공격
  - XSS: cross site scripting
  - CSRF: cross site request forgery

---

## 출력 값의 escape 미비로 인한 취약성

- cross site scripting: browser에 HTML/JavaScript 함정 심음
- SQL injection: 부정 SQL문을 삽입하여 권한 없는 정보에 접근
- OS command injection
- HTTP header injection: 임의의 response header를 추가
	- HTTP response splitting attack: body를 추가
- mail header injection
- directory 접근 공격
- remote file inclusion

---

## web server의 설정이나 설계 미비로 인한 취약성

### 강제 browsing

server의 공개 directory에 있는 file중 공개 의도가 없는 것이 열람 됨

- 고객 정보 등의 중요 정보 누설
- 본래 access 권한이 있는 사용자에게만 표시하는 정보 누설
- 어디에도 link 되지 않는 file 누설

---

### 부적절한 error message 처리

공격자에게 유리한 정보가 error message에 포함

- web application에 의한 error message
- DB 등의 system에 의한 error message
  - PHP, ASP 등의 script error
  - DB, middleware의 error
  - web server error

---

### open redirect

임의의 URL로 redirect하게 함.

---

## session 관리 미비로 인한 취약성  

### session hijack

user session ID를 손에 넣어 user로 위장

- 부적절한 생성 방법에 의한 session ID 추측
- 도청이나 XSS 등에 의한 session ID 도용
- session fixation 공격에 의한 session ID 강제

---

### session fixation

공격자가 지정한 session ID를 user에게 강제/고정.

---

### cross site request forgery

개인 정보, 설정 정보 등을 강제 갱신

* front-end 개발자에게도 중요

- 인증된 user의 권한으로 설정 정보 등을 갱신
- 인증된 user의 권한으로 상품 구입
- 인증된 user의 권한으로 게시판에 글 작성

---

## 기타 공격들

### clickjaking

- 투명 버튼, 투명 링크 함정을 심어두고 click 유도
- 의도치 않은 content에 access
- UI dressing 으로도 불림

---

### Dos 공격

Denial of Service attack. server를 service 불능 상태로 만듬

- 과다한 access를 단시간에 집중시켜 service를 정지 시킴
- server의 취약성을 공격해 service를 정지 시킴

---

### backdoor

절차 없이 server의 제한된 기능을 이용하기 위해 설치해 놓은 뒷문

- 개발 단계에서 설치한 debug용 backdoor
- 개발자가 사익을 위해 설치한 backdoor
- 공격자가 어떠한 방법을 써서 설치한 backdoor

---

## 맺으며

> ...it's worth considering how the Internet got to be such an insecure place in the first place. The answer, in essence, is that the Internet was originally designed to be that way, based on the model of **"a group of mutually trusting users attached to a transparent network"** [Blumenthal 2001]--a model in which (by definition) there is no need for security. Many aspects of the original Internet architecture deeply reflect this notion of mutual trust.