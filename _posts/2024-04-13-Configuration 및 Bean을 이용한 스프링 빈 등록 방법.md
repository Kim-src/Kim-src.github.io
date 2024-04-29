---
title: Configuration 및 Bean을 이용한 스프링 빈 등록 방법
date: 2024-04-13 18:00:00 +09:00
categories: [1. Fundamental, Spring]
tags: [Fundamental, Spring, Annotation, Configuration, Bean, DI, Dependency Injection, Constructor Method, Autowired, Spring Bean]
---

<!-- 2024-04-13 글 작성 시작; 2024-04-13 페이지 호출 완료 -->
<h2>강의 내용 복습 : 김영한의 스프링 입문 강의 (섹션 4)</h2>
> - Tool :  
<img alt="IntelliJ" src="https://img.shields.io/badge/-IntelliJ-000000?style=flat-square&logo=intellij-idea&logoColor=white" />
<img alt="Spring Boot" src="https://img.shields.io/badge/-SpringBoot-6DB33F?style=flat-square&logo=spring&logoColor=white" />

<br>

### 🔔 핵심 개념
### 📌 스프링 빈(bean)
> - 스프링 프레임워크에서 빈은 스프링 컨테이너에 의해 관리되는 애플리케이션 객체입니다.
> - 스프링 빈의 특징적인 역할은 의존성 주입이 있습니다.

### 📌 스프링 빈 등록(= 정의) 방법
> - 과거 스프링 프로젝트에서는 xml 파일 내에서 bean 태그를 사용하여 정의했습니다.
> - 최근 방식의 스프링 빈 등록 방법은 어노테이션을 이용하는 것입니다.
> - 이 방식에는 @Component를 포함한 어노테이션이 사용되며 클래스를 스프링 빈에 등록시킵니다.
> - 등록 방법은 자동(컴포넌트 스캔 방식) 및 수동(Java 클래스 설정)으로 구분됩니다.

### 📌 스프링 빈 등록 자동 방식 : 컴포넌트 스캔 방식
> - @ComponentScan을 이용하여 관련 패키지에서 어노테이션이 포함된 클래스를 검색합니다.
> - 어노테이션의 종류는 @Controller, @Service, @Repository가 있습니다.
> - 이들 어노테이션이 포함된 클래스를 빈으로 자동 등록합니다.

### 📌 스프링 빈 등록 수동 방식 : Java 클래스 설정
> - @Configuration 어노테이션이 포함된 클래스를 생성시킵니다.
> - 그리고 애플리케이션 구성 메서드에 @Bean 어노테이션이 포함시켜서 수동으로 빈을 등록합니다.

### 📌 스프링 빈의 역할 : 의존성 주입(DI; Dependency Injection)
> - 스프링 컨테이너에서 스프링 빈 사이의 의존성을 관리합니다.
> - @Autowired 어노테이션을 사용하면 스프링 빈 인스턴스에 필요한 의존성이 자동으로 주입됩니다.
> - @Autowired는 보통 생성자 메서드를 구현한 코드에 포함시킵니다.
> - 생성자 이용 방식이 아닌 것으로는 필드 주입 방식, setter 주입 방식 등이 있습니다.

### 📌 스프링 컨테이너의 역할 : 라이프 사이클 관리
> - 스프링 컨테이너는 빈의 전체 생명주기를 관리하며 이를 '라이프 사이클 관리'라고 합니다.
> - 라이프 사이클 관리는 스프링 빈의 생성, 의존성 주입, 초기화, 사용, 소멸 등을 포함합니다.
> - @PostConstruct, @PreDestroy 등을 이용하면 빈의 초기화나 소멸 시점을 정의할 수 있습니다.
> - 개발자는 이들을 이용하여 객체의 생성/소멸 시 필요한 로직을 실행할 수 있습니다.

<br>

### 🔔 강의 내용
### 📌 다양한 스프링 빈 등록 방법
> - @Service 및 @Repository는 @Component를 이용하여 스프링 빈에 클래스를 등록하는 방법입니다.
> - 이와달리 @Configuration, @Bean은 Java를 이용하여 스프링 빈에 클래스를 등록하는 방법입니다.
> - 두 방법에는 장단점이 있으며 xml 파일을 이용한 스프링 빈 등록 방법보다는 최신입니다.
> - 두 방법 중 실무에서는 <a href="https://kim-src.github.io/posts/%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-%EC%8A%A4%EC%BA%94%EC%9D%84-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EC%8A%A4%ED%94%84%EB%A7%81-%EB%B9%88-%EC%A0%95%EC%9D%98-%EB%B0%8F-Autowired/">컴포넌스 스캔 방식</a>이 주로 사용됩니다.
> - 참고로 @Configuration에는 @Service & @Repository와 마찬가지로 @Component가 포함됩니다.

### 🔔 로직 이해
### 📌 <a href="https://github.com/Kim-src/Study-Spring/blob/main/src/main/java/hello/hellospring/SpringConfig.java">SpringConfig</a>
> - Java 클래스 설정 방식으로 스프링 빈에 클래스를 등록하는 방식과 관련된 코드입니다.
> - 전체 코드 내용은 아래와 같습니다.

``` java
package hello.hellospring;

import hello.hellospring.repository.MemberRepository;
import hello.hellospring.repository.MemoryMemberRepository;
import hello.hellospring.service.MemberService;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class SpringConfig {

    @Bean
    public MemberService memberService() {
        return new MemberService(memberRepository());
    }

    @Bean
    public MemberRepository memberRepository() {
        return new MemoryMemberRepository();
        // new 키워드를 사용하면 인터페이스의 인스턴스를 직접 생성할 수 없습니다.
        // 즉, 인터페이스를 구현한 구현체의 인스턴스를 생성해야 됩니다.
    }
}
```

<br>
<br>
<br>
