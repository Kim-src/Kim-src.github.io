---
title: HTTP 관련 객체와 메서드 Request, Response, GET, POST
date: 2024-06-18 18:00:00 +09:00
categories: [1. Fundamental, Spring]
tags: [Spring, Fundamental, Server, Server Side, Request, Response, GET, POST]
---

<!-- 2024-06-18 글 작성 시작; 2024-06-18 페이지 호출 완료 -->
<h2>강의 내용 복습 : 코리아IT 신촌점 강의 (2024-06-12 강의)</h2>
> - Tool :  
<img alt="Spring" src="https://img.shields.io/badge/-Spring-6DB33F?style=flat-square&logo=spring&logoColor=white" />
<img alt="Spring Tool Suite 4" src="https://img.shields.io/badge/-Spring%20Tool%20Suite%204-6DB33F?style=flat-square&logo=eclipse&logoColor=white" />

<br>

### 📌 URL

### 📌 URI

### 📌 Request 객체(요청)
> - 클라이언트가 서버와 상호작용하는 방법은 크게 요청과 응답으로 분류됩니다.
> - 그 중 요청은 클라이언트가 서버에 특정 데이터나 동작을 요구하는 객체입니다.
> - Request에는 URL, 헤더, 데이터 등이 포함됩니다.
> - Request는 데이터를 저장하는 setter 기능은 없고 getter 기능은 제공합니다.
> - 즉, 일반적으로 Request 객체는 데이터를 전송하는 역할을 합니다.
> - 데이터 전송을 위해 Request 객체의 GET 및 POST 메서드를 사용합니다.

#### 🚩 GET 메서드
> - Response 객체의 GET 메서드는 주로 정보를 조회하기 위해 이용되는 메서드입니다.
> - GET 요청은 데이터를 URL에 포함시켜 전송한다는 것이 특징입니다.
> - GET 요청의 예시는 사용자가 브라우저 주소창에 URL을 입력하는 행위입니다.

#### 🚩 POST 메서드
> - Response 객체의 POST 메서드는 주로 정보를 저장하기 위해 이용되는 메서드입니다.
> - POST 요청은 데이터를 HTTP 메시지의 본문(body 태그 내용)에 포함시켜 전송합니다.
> - POST 요청은 서버의 데이터를 생성하거나 업데이트하기 위해서도 사용됩니다.

### 📌 Response 객체(응답)
> - 서버가 클라이언트의 요청에 반응하여 전달하는 데이터를 포함하는 객체입니다.
> - Response 객체가 전달하는 데이터에는 아래 내용이 포함됩니다.
> - 응답하는 정보의 예시는 아래와 같습니다.
>    - 서비스의 결과물 : HTML, CSS, JS 등
>    - 상태 코드 : 요청에 대한 처리 결과를 나타내는 200(성공), 404(찾을 수 없음) 등
>    - 세션 및 쿠키 관리 : 후속 요청에 필요한 정보를 서버에 저장

### 📌 Apache Tomcat

### 📌 JPA

### 📌 MyBatis

### 📌 Parameter 객체

### 📌 Attribute 객체
> - 클라이언트가 서버로부터 데이터를 받으려면 무조건?

<br>
<br>
<br>
