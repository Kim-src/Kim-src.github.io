---
title: 서버 사이드 기술의 종류, Request, Response, GET, POST
date: 2024-06-18 18:00:00 +09:00
categories: [1. Fundamental, Spring]
tags: [Spring, Server, Server Side, Request, Response, GET, POST]
---

<!-- 2024-06-18 글 작성 시작; 2024-06-18 페이지 호출 완료 -->
<h2>강의 내용 복습 : 코리아IT 신촌점 강의 (2024-06-12 강의)</h2>
> - Tool :  
<img alt="Java" src="https://img.shields.io/badge/-Java-007396?style=flat-square&logo=java&logoColor=white" />
<img alt="Eclipse" src="https://img.shields.io/badge/-Eclipse-2C2255?style=flat-square&logo=eclipse&logoColor=white" />

<br>

### 📌 서버(Server) 개념
> - 서버란 네트워크를 통해 클라이언트의 요청에 응답하는 컴퓨터입니다.
> - 정확히는 서버 관리 전용 프로그램이 구비된 물리적인 컴퓨터이거나 가상 환경의 것입니다.
> - 서버는 단어 그대로 서비스를 제공하는 역할을 합니다.
> - 서비스에는 웹 페이지 접근, DB 접근, 파일 또는 이메일 전송 등이 포함됩니다.
> - 서버는 일반 사용자(user)가 접근하기 어렵기 때문에 백엔드 파트로 분류됩니다.

### 📌 서버 사이드 기술
> - 서버 사이드(서버단)는 서버 단계의 백엔드(백단) 기술에 해당됩니다.
> - 서버 사이드 기술에는 클라이언트와의 상호작용을 위한 다양한 기술이 포함됩니다.
> - 서버 사이드 기술은 웹 개발의 일환이며 상세 예시는 아래와 같습니다.
> - 참고로 React는 클라이언트 사이드의 UI 구축이 목적인 JS 라이브러리입니다.

#### 🚩 프로그래밍 언어 및 유관 기술
> - Java : Spring Framework, Spring Boot, Java EE
> - Python : Django 및 Flask 프레임워크
> - Node.js : Express 프레임워크
> - Ruby : Ruby on Rails
> - PHP : WordPress

#### 🚩 웹 서버 및 DBMS
> - Apache HTTP Server : HTML, CSS, JS 등 정적 콘텐츠 제공
> - Apache Tomcat : Java 기반 웹 애플리케이션 개발을 위한 JSP, Servlet 파일 처리
> - 데이터베이스 유관 프레임워크 : JPA, MyBatis
> - 각종 DBMS : MySQL, Oracle, MaiaDB, MongoDB 등

### 📌 Request 객체(요청)
> - 클라이언트가 서버와 상호작용하는 방법은 크게 요청과 응답으로 분류됩니다.
> - 그 중 요청은 클라이언트가 서버에 특정 데이터나 동작을 요구하는 객체입니다.
> - Request에는 URL, 헤더, 데이터 등이 포함됩니다.
> - Request는 데이터를 저장하는 setter 기능은 없고 getter 기능은 제공합니다.
> - 즉, 일반적으로 Request 객체는 데이터를 전송하는 역할을 합니다.
> - 데이터 전송을 위해 Request 객체의 GET 및 POST 메서드를 사용합니다.

#### 🚩 GET 메서드
> - 서버의 정보를 조회하기 위해 이용하는 Response 객체의 메서드입니다.
> - GET 요청은 데이터를 URL에 포함시켜서 전송합니다.
> - 사용자가 브라우저의 주소창에 URL을 입력하는 행위가 GET 요청을 보내는 것입니다.

#### 🚩 POST 메서드
> - 서버에 데이터 처리를 요청하는 Response 객체의 메서드입니다.
> - POST 요청은 데이터를 HTTP 메시지의 본문(body 태그)에 포함시켜 전송합니다.
> - 주로 서버의 데이터를 생성하거나 업데이트하기 위해 사용합니다.

### 📌 Response 객체(응답)
> - 서버가 클라이언트의 요청에 반응하여 전달하는 데이터를 포함하는 객체입니다.
> - Response 객체가 전달하는 데이터에는 아래 내용이 포함됩니다.
> - 응답하는 정보의 예시는 아래와 같습니다.
>    - 서비스의 결과물 : HTML, CSS, JS 등
>    - 상태 코드 : 요청에 대한 처리 결과를 나타내는 200(성공), 404(찾을 수 없음) 등
>    - 세션 및 쿠키 관리 : 후속 요청에 필요한 정보를 서버에 저장

<br>
<br>
<br>
