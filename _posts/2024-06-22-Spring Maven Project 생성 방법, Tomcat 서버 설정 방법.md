---
title: Spring Maven Project 생성 방법, Tomcat 서버 설정 방법
date: 2024-06-22 18:00:00 +09:00
categories: [1. Fundamental, Spring]
tags: [Spring, Fundamental, Java EE, STS, STS4, Spring Tool Suite 4, JSP, Servlet, UTF-8, Tomcat, JPA, MyBatis, Server, Server Side, Request, Response, GET, POST, WEB-INF]
---

<!-- 2024-06-18 글 작성 시작; 2024-06-22 페이지 호출 완료 -->
<h2>강의 내용 복습 : 코리아IT 신촌점 강의 (2024-06-11,12,20,21 강의)</h2>
> - Tool : 
<img alt="Spring" src="https://img.shields.io/badge/-Spring-6DB33F?style=flat-square&logo=spring&logoColor=white" />
<img alt="Spring Tool Suite 4" src="https://img.shields.io/badge/-Spring%20Tool%20Suite%204-6DB33F?style=flat-square&logo=eclipse&logoColor=white" />

<br>

### 🔔 Spring Maven Project 초기 세팅
### 📌 Spring Tool Suite 4 다운로드
> - Spring 개발을 할 수 있는 IDE는 다양하며 주로 IntelliJ 또는 Eclipse가 사용됩니다.
> - 필자는 <a href="https://spring.io/tools">Eclipse에서 Spring 개발에 초점을 맞춘 IDE인 STS4</a>를 사용하였습니다.
> - STS4 개발 환경은 Eclipse와 매우 흡사하고 링크된 글에서 다운로드 받으실 수 있습니다.
> - 이번 문단에서는 Spring의 Maven Project를 이용하여 브라우저 뷰포트에 호출해보겠습니다.

### 📌 메모리 할당량 설정
> - 다운로드 받았던 STS 루트 폴더를 열고 'SpringToolSuite4.ini'를 클릭합니다.
> - ini 파일의 본문 내용 하단부에 위치한 Xms 값을 Xmx (최댓값)와 동일하게 2048m로 변경합니다.
> - 이는 메모리 할당량을 증가시키는 설정이며 메모리를 요구하는 프로젝트를 개발할 수 있습니다.
> - 예를들면 Dispatcher Servlet에 의해 메모리 사용량이 많은 Spring 웹 개발을 할 수 있습니다.

### 📌 Perspective 설정
> - 필자는 Perspective를 Java EE로 설정하였습니다.
> - Perspective는 프로젝트의 성격에 맞게 설정하시면 됩니다.
> - Perspective는 STS4 화면의 우측 상단에 위치하였으며 여러가지 중 선택할 수 있습니다.

### 📌 UTF-8 설정
> - UTF-8은 국제적으로 널리 사용되는 문자 인코딩 방식이며 한국어가 포함됩니다.
> - 전역 인코딩 설정은 Preferences로 가능하며 UTF-8로 설정하는 방법은 아래와 같습니다.

```
- Windows 탭 → Preferences → General → Content Types → Text → Spring Properties File → Default encoding 입력창 → ISO-8859-1 내용을 UTF-8로 수정 → Update → Apply and Close
- Windows 탭 → Preferences → General → Content Types → Text → JSP → ISO-8859-1 내용을 UTF-8로 수정 → Update → Apply and Close
- Windows 탭 → Preferences → General → Content Types → Text → JSP → JSP Fragment → ISO-8859-1 내용을 UTF-8로 수정 → Update → Apply and Close
- Windows 탭 → Preferences → General → Content Types → Text → JSP → JSP Tag Definition → ISO-8859-1 내용을 UTF-8로 수정 → Update → Apply and Close
- Windows 탭 → Preferences → General → Content Types → Text → CSS → 공란에 UTF-8 입력 → Update → Apply and Close
- Windows 탭 → Preferences → General → Content Types → Text → HTML → 공란에 UTF-8 입력 → Update → Apply and Close
- Windows 탭 → Preferences → General → Content Types → Text → Java Source File → 공란에 UTF-8 입력 → Update → Apply and Close
- Windows 탭 → Preferences → General → Content Types → Text → Java Properties File → ISO-8859-1 내용을 UTF-8로 수정 → Update → Apply and Close
```

### 📌 JDK 경로 설정
> - JDK는 Java Devlopment Kit의 축약어이며 컴파일러 등이 포함된 개발 환경입니다.
> - 필자의 경우 좋은 호환성을 위해 JDK 17을 사용 중입니다.

```
- Windows 탭 → Preferences → Java → Installed JREs → Edit → C드라이브 등에 위치된 JDK 17 선택 → 'jre'를 'jdk-17'로 수정 → Finish
```

<br>

### 🔔 서버(Server)
### 📌 서버 개념
> - 웹 서버는 클라이언트로부터 받은 HTTP 요청을 토대로 콘텐츠를 제공하는 것입니다.
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

<br>

### 🔔 Apache Tomcat
### 📌 Tomcat 소개
> - Tomcat은 웹 개발에 이용되는 서버이자 웹 컨테이너이고 다양한 디렉토리와 요소로 구성됩니다.
> - bin : Tomcat을 실행/중지하는 데 사용되는 실행 파일 및 스크립트가 포함됩니다.
> - conf : Tomcat 서버의 동작 방식을 결정하는 주요 xml 파일 등이 포함됩니다.
> - lib : Tomcat과 함께 사용되는 Java의 라이브러리 jar 파일 등이 포함됩니다.
> - Tomcat 서버 하나 당 1,000명 정도의 사용자는 감당 가능하기에 개발 초기에 사용하기 좋습니다.
> - Tomcat 서버는 프로젝트 당 하나씩 설정하는 것이 관리에 용이합니다.

### 📌 Apache vs Tomcat
> - 웹은 서버와 컨테이너로 구분되고 서버는 정적, 컨테이너는 동적 콘텐츠 처리에 적합합니다.
> - Apache는 웹 서버, Tomcat은 웹 컨테이너로 분류됩니다.
> - 따라서 함께 사용되는 Apache Tomcat은 담당하는 정적/동적 콘텐츠가 상이합니다.

### 📌 Apache Tomcat 다운로드
> - <a href="https://tomcat.apache.org">Tomcat은 링크된 글</a>에서 다운로드 받으실 수 있습니다.
> - 사이트 접속 → Tomcat 9 → Core → zip이 일반적인 Tomcat을 다운로드 받는 방법입니다.

### 📌 Tomcat 서버 포트 및 인코딩 방식 변경 방법
> - 8080 서버 포트는 다양한 곳에서 이미 사용 중이기 때문에 다른 포트로 변경하는 것이 좋습니다.
> - 참고로 8005 서버 포트는 서버 종료 시 사용되기 때문에 변경할 필요 없습니다.
> - 서버 포트를 변경하기 위해서는 conf 디렉토리의 server.xml 파일에 접근해야 됩니다.
> - server.xml 파일 하단부의 'Connector port="8080"'에서 번호를 '9090'으로 변경합니다.
> - 그리고 'maxParameterCount="1000"' 뒤에 'URIEncoding="UTF-8"'을 입력합니다.
> - server.xml 파일의 주석과 실사용 코드를 구분하기 위해서 VS Code를 이용하면 좋습니다.

### 📌 Tomcat 가상 서버 설정 방법
> - STS, Eclipse와 같은 IDE에서는 Tomcat 가상 서버를 설정할 수 있습니다.
> - 즉, 실제 서버 전용 환경을 구비하지 않더라도 프로그램을 테스트할 수 있습니다.
> - 프로젝트 Properties의 Targeted Runtimes에서는 서버 설정이 잘 됐는지 확인할 수 있습니다.
> - STS, Eclipse에서 가상 서버 설정하는 방법은 아래와 같습니다.

```
- Windows 탭 → Preferences → Server → Runtime Environment → Add → Apache → Apache Tomcat v9.0 → Next → Browse → Tomcat 경로 선택 → JRE → jdk-17 → Finish → Apply and Close
```

### 📌 Tomcat 가상 서버 생성 방법
> - 이제 개별 프로젝트와 연결되는 실질적인 가상의 Tomcat 서버를 생성해보겠습니다.
> - 서버 생성을 위해 Server 탭에 접근해야 되며 STS에서는 Console 탭 근처에 있습니다.
> - 서버 생성을 완료하고 서버를 더블 클릭하면 Overview 탭과 Modules 탭을 확인할 수 있습니다.
> - Moudles 탭을 확인했을 때 생성된 서버가 표시되고 Enable 상태라면 정상입니다.
> - 아래는 서버 생성 방법입니다.

```
- Server 탭 마우스 우클릭 → New → Server → Apache → Tomcat v9.0 Server → Next → 해당 프로젝트 클릭 → Add → Finish
```

### 📌 웹 페이지 호출 URL 변경
> - 브라우저에 웹 페이지를 호출하려면 로컬 호스트 주소를 입력해야 됩니다.
> - 이때 'locatlhost:8080/projectname/location' 등으로 주소를 입력합니다.
> - URL 내용 중 프로젝트명을 반드시 입력하지 않고 호출시키는 아래와 같은 방법이 있습니다.
> - 아래와 같이 작업 시 'locatlhost:8080/location'으로 보다 용이한 호출이 가능합니다.
> - 참고로 Document base는 프로젝트명이 작성되어 있을 것입니다.

```
- 서버 더블클릭 → Modules 탭 → 서버 클릭 → Edit 클릭 → Path 내용 전부 제거
```

<br>

### 🔔 Spring Maven Project 개발 방법
### 📌 Maven Project 생성 방법
> - Package Explorer 창에 마우스를 대고 우클릭합니다.
> - New → Maven project를 클릭합니다.
> - 테스트용 애플리케이션 제작을 위한 Create a simple project를 클릭합니다.
> - Group Id에 'kr.com'을 예시로 입력합니다.
> - Artifact Id에 'spring-board'를 예시로 입력합니다.
> - Packaging을 war로 선택합니다.
> - Name을 Artifact Id와 동일한 'spring-board'로 입력합니다.
> - Finish를 클릭하면 프로젝트가 생성됩니다.

### 📌 프로젝트명 설정
> - 용이한 개발 및 유지/보수를 위해서는 프로젝트명에 영문 소문자만 입력되어야 됩니다.
> - 왜냐하면 컴파일 과정에서 컴파일러가 대/소문자 구분을 명확히 하지 못하기 때문입니다.
> - 대문자 자체가 문제가 되는 것은 아니지만 한 번 컴파일되면 소문자로 수정되지 않습니다.
> - 협업 과정에서 일부 대문자가 있는 프로젝트명과 소문자가 혼용되면 에러가 발생됩니다.
> - 관련 에러 발생 시 캐시뿐만 아니라 로그까지 소멸시킨 뒤 프로그램을 구축해야 됩니다.
> - 즉, 프로젝트명에 대문자, 특수문자(공백 등), 언더바 등은 지양해야 좋습니다.

### 📌 WEB-INF 디렉토리 생성
> - WEB-INF 디렉토리는 클라이언트가 JSP에 직접적으로 접근하지 못하게 차단할 수 있습니다.
> - 서버에 의한 접근은 가능하지만 URL/URI와 연결된 HTTP를 통한 접근은 허용되지 않습니다.
> - 즉, JSP 파일 등의 보안을 강화하기 위해서는 WEB-INF 디렉토리 아래에 저장해야 됩니다.
> - WEB-INF 디렉토리를 생성하는 방법은 아래와 같습니다.
> - 참고로 INF는 information의 축약어입니다.

```
- root/src/main/webapp → 마우스 우클릭 → WEB-INF 폴더 생성
```

### 📌 WEB-INF 콘텐츠 생성
> - WEB-INF 내에 프로젝트 구성에 필요한 콘텐츠를 생성해면 됩니다.
> - WEB-INF 내에는 config, spring, views 디렉토리와 <a href="https://github.com/kim-src/study-spring/blob/main/spring-board/src/main/webapp/WEB-INF/web.xml">web.xml</a>이 포함될 수 있습니다.
> - spring 디렉토리 내에는 <a href="https://github.com/kim-src/study-spring/blob/main/spring-board/src/main/webapp/WEB-INF/spring/root-context.xml">root-context.xml</a>, <a href="https://github.com/kim-src/study-spring/blob/main/spring-board/src/main/webapp/WEB-INF/spring/servlet-context.xml">servlet-context.xml</a> 등이 포함됩니다.
> - views 디렉토리 내에는 jsp 등의 정적 콘텐츠가 포함됩니다.
> - 각각의 깃허브 링크에는 파일 내용이 포함됩니다.

### 📌 Lombok 설정
> - Lombok은 반복적인 Java 코드를 최소화하기 위해 개발된 도구입니다.
> - Lombok은 사용하기 위해서는 어노테이션을 부여하면 되며 사용 예시는 아래와 같습니다.
>    - @Getter/@Setter : 필드의 getter/setter 메서드를 어노테이션으로 생성할 수 있습니다.
>    - @ArgsConstructor : 각각의 목적에 맞는 생성자를 자동으로 생성할 수 있습니다.
>    - @Builder : 복잡한 객체 생성 시 사용하는 빌더 패턴을 구현할 수 있습니다.
>    - @Cleanup : 파일 input/output과 같은 자원을 자동으로 정리할 수 있습니다.
> - <a href="https://projectlombok.org/download">Lombok은 링크된 사이트</a>에서 다운로드 받을 수 있습니다.
> - Lombok과 관련된 jar 파일을 클릭하고 경로 등을 설정하면 설치가 완료됩니다.

### 📌 jar 파일
> - Spring을 개발하다보면 jar 파일을 사용해야 될 때가 있습니다.
> - jar는 Java Archive 파일의 축약어이며 Java 로고 아이콘의 압축 파일입니다.
> - jar에는 여러 Java 클래스, 메타 데이터, 리소스 파일 등이 포함됩니다.
> - 사용자는 jar 파일 하나만으로도 애플리케이션의 기능을 쉽게 확장시킬 수 있습니다.
> - jar 파일은 실행 가능한 압축 파일 형태일 수 있으며 더블 클릭하면 실행되는 경우가 있습니다.
> - jar 파일의 예시는 각종 라이브러리와 STS, lombok 설치 파일 등입니다.

<br>

### 🔔 Spring MVC 구축
### 📌 Model 구축
> - 데이터베이스에 접근하기 위해 MyBatis를 사용하였습니다.
> - MyBatis는 SQL 매핑 프레임워크 중 하나이며 SQL 문을 XML 또는 어노테이션으로 관리합니다.
> - resources/config 디렉토리 내에 <a href="https://github.com/kim-src/study-spring/blob/main/spring-board/src/main/resources/config/mybatis-config.xml">MyBatis를 설정하는 xml 파일</a>을 생성하였습니다.

### 📌 View 구축
> - JSP를 이용하여 테스트용 웹 페이지를 생성하였습니다.
> - 해당 웹 페이지는 JSTL 및 EL을 이용하여 구현되었습니다.
> - <a href="https://kim-src.github.io/posts/Spring-%EA%B0%9C%EB%B0%9C%EC%9D%84-%EC%9C%84%ED%95%9C-JSP,-JSTL,-Servelet,-MVC-%ED%8C%A8%ED%84%B4%EC%9D%98-%EA%B4%80%EA%B3%84/#-jsp-java-server-page">JSP에 대한 설명은 링크된 글</a>에 잘 작성되어 있습니다.
> - 아래는 JSP 내용입니다.

``` jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
	<div>2024-06-21 강의 실습</div>
	<h1>${msg} Spring 작동 메커니즘</h1>
	<!-- EL 사용 아닐 경우 -->
	<% String msg = (String)request.getAttribute("msg"); %>
</body>
</html>
```

### 📌 Controller 구축
> - 웹 페이지 호출을 위한 컨트롤러를 구현하였습니다.
> - 웹 페이지 호출 시 GET 또는 POST 사용 방식의 예시도 있습니다.
> - <a href="https://kim-src.github.io/posts/Spring-%EA%B0%9C%EB%B0%9C%EC%9D%84-%EC%9C%84%ED%95%9C-JSP,-JSTL,-Servelet,-MVC-%ED%8C%A8%ED%84%B4%EC%9D%98-%EA%B4%80%EA%B3%84/#-controller">컨트롤러에 대한 설명은 링크된 글</a>에 잘 작성되어 있습니다.

``` java
package kr.com.web;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class HelloController {
	
	// GET/POST 모두 수용
	// @RequestMapping(value="/hello.do")
	// only GET 수용
	// @RequestMapping(value="/hello.do", method = RequestMethod.GET)
	// only POST 수용
	// @RequestMapping(value="/hello.do", method = RequestMethod.POST)
	
	@GetMapping(value="/hello.do")
	public String hello(Model model) {
		model.addAttribute("msg", "2024-06-21 강의 주제 : ");
		return "hello";
	}

}
```

<br>
<br>
<br>
