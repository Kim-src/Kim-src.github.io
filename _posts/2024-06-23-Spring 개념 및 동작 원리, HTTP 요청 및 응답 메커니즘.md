---
title: Spring 개념 및 동작 원리, HTTP 요청 및 응답 메커니즘
date: 2024-06-23 18:00:00 +09:00
categories: [1. Fundamental, Spring]
tags: [Spring, Fundamental]
---

<!-- 2024-06-22 글 작성 시작; 2099-01-01 페이지 호출 완료 -->
<h2>강의 내용 복습 : 코리아IT 신촌점 강의 (2024-06-10,12,21 강의)</h2>
> - Tool :  
<img alt="Spring" src="https://img.shields.io/badge/-Spring-6DB33F?style=flat-square&logo=spring&logoColor=white" />
<img alt="Spring Tool Suite 4" src="https://img.shields.io/badge/-Spring%20Tool%20Suite%204-6DB33F?style=flat-square&logo=eclipse&logoColor=white" />

<br>

### 🔔 Spring
### 📌 Spring 주요 개념
> - Spring의 동작을 설명하는 주요 개념에는 IOC와 DI가 있습니다.
> - IOC와 DI를 이용하여 객체의 생성과 관리의 복잡성을 최소화 할 수 있습니다.

#### 🚩 IOC (Inversion of Control)
> - IOC는 프로그램의 실행 흐름을 개발자가 아닌 Spring Framework가 제어한다는 의미입니다.
> - 애플리케이션의 흐름이란 객체의 생성, 사용, 소멸과 같은 생명 주기 등을 의미합니다.
> - Spring은 어노테이션을 통해 객체를 관리하고 프레임워크가 생명 주기를 제어합니다.
> - 아래는 주요 어노테이션에 대한 설명입니다.
>    - @Controller, @RestController : 요청과 응답을 처리하는 컨트롤러 객체를 정의함
>    - @Service : 비즈니스 로직을 처리하는 서비스 계층의 객체를 정의함
>    - @Mapper, @Repository : 데이터베이스와의 상호작용을 처리하는 <a href="https://kim-src.github.io/posts/%EC%A0%91%EA%B7%BC%EC%A0%9C%ED%95%9C%EC%9E%90,-%EC%BA%A1%EC%8A%90%ED%99%94,-%EC%98%A4%EB%B2%84%EB%A1%9C%EB%94%A9,-Getter,-Setter-%EC%9D%98%EB%AF%B8/#-dto-vo-dao-utility-%EA%B0%9D%EC%B2%B4">DAO 계층</a>의 객체를 정의함
>    - @Component : 일반적인 컴포넌트로 자주 사용되는 객체를 정의함
>    - @Bean : 메서드에서 반환되는 객체를 Spring 컨테이너에 Bean으로 등록함
>    - @Configuration : 클래스가 Bean 정의를 포함하고 있음을 나타냄

#### 🚩 DI (Dependency Injection)
> - DI는 객체가 필요로 하는 의존성 객체를 외부에서 제공하는 패턴입니다.
> - DI의 장점은 애플리케이션 테스트가 용이해진다는 것입니다.
> - DI의 주요 의존성 주입 방식은 아래와 같습니다.
>    - 생성자 주입 : 객체가 생성될 때 생성자를 통해 의존성을 주입함
>    - 세터 주입 : 객체가 생성된 후 메서드를 통해 의존성을 주입함

<br>

### 🔔 제목
### 📌 XML vs JSON
#### 🚩 XML
#### 🚩 JSON

<br>

### 🔔 응용 학습
### 📌 부제목
> - 글 내용

<br>
<br>
<br>

### 📌 Prefix & Surfix
> - Prefix + viewName + surfix = 경로 + 이름 = full 경로

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