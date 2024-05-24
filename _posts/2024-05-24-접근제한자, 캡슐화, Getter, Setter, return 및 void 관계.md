---
title: 접근제한자, 캡슐화, Getter, Setter, return 및 void 관계
date: 2024-05-24 18:00:00 +09:00
categories: [1. Fundamental, Java]
tags: [Java, Fundamental, Access Modifier, Getter, Setter, Parameter, Return, Void]
---

<!-- 2024-05-20 글 작성 시작; 2024-05-24 페이지 호출 완료 -->
<h2>강의 내용 복습 : 코리아IT 신촌점 자바 강의 (2024-04-29,30 강의)</h2>
> - Tool :  
<img alt="Java" src="https://img.shields.io/badge/-Java-007396?style=flat-square&logo=java&logoColor=white" />
<img alt="Eclipse" src="https://img.shields.io/badge/-Eclipse-2C2255?style=flat-square&logo=eclipse&logoColor=white" />

<br>

### 🔔 접근제한자
### 📌 접근제한자 뜻
> - 접근제한자는 클래스의 인스턴스 등에 접근할 수 있는 범위를 제한하기 위해 사용됩니다.
> - 접근제한자는 프로그램의 데이터 보호 등의 보안에 있어 필수적입니다.
> - 접근제한자의 종류는 public, private, protected 등이 있습니다.

### 📌 public 접근제한자
> - 변수 등이 public으로 선언되었다면 어떠한 패키지의 어떠한 클래스에서도 접근 가능합니다.
> - 일반적으로는 변수는 private으로 선언하고 메서드는 public으로 선언합니다.
> - 이렇게 되면, 먼저 객체에 접근 후 점(.) 연산자를 통해 변수 등에 접근해야 됩니다.
> - 그런데 변수는 private으로 선언되어 있기 때문에 getter 또는 setter를 통해야 됩니다.

### 📌 private 접근제한자
> - private을 선언한 객체의 필드 내에서만 접근이 가능합니다.
> - 같은 패키지에 있더라도 외부 클래스에서는 접근할 수 없게 됩니다.

### 📌 protected 접근제한자
> - protected를 선언한 같은 클래스와 같은 패키지에 속한 클래스에서 접근 가능합니다.
> - 또는 다른 패키지에 있더라도 해당 클래스를 상속받은 하위 클래스에서는 접근 가능합니다.
> - 따라서 protected는 서로 상속 관계에 있는 클래스들끼리의 연결성을 제공합니다.

### 📌 default
> - 접근제한자를 지정해두지 않으면 default 접근제한자로 자동 지정됩니다.
> - 이 경우 동일 패키지의 다른 클래스에서만 접근 가능합니다.

### 📌 캡슐화

<br>

### 🔔 Getter and Setter
### 📌 Getter 메서드 및 Setter 메서드 의미
> - 개발자 입장에서 Getter는 클래스 내부의 값을 외부로 '반환하는' 역할을 합니다.
> - 사용자 입장에서 Getter는 외부 클래스의 값을 내부로 '가져오는' 역할을 합니다.
> - 개발자 입장에서 Setter는 외부에서 제공된 값을 클래스 내부에 '저장하는' 역할을 합니다.
> - 사용자 입장에서 Setter는 외부 클래스의 속성(변수)에 값을 '제공하는' 역할을 합니다.
> - 참고로 값은 입력 메서드나 설정된 함수 등으로 통해 제공됩니다.

### 📌 Getter and Setter 사용 이유
> - Getter and Setter는 객체 지향 프로그래밍에서 하나의 안전 장치 역할을 합니다.
> - 여러 클래스를 활용하는 객체 지향 프로그래밍은 접근제한자가 사용됩니다.
> - 이때 private 접근제한자로 선언된 변수의 경우 타 클래스에서 접근이 불가합니다.
> - 그래서 private 접근제한자로 선언된 변수에 대한 getter and setter 메서드가 필요합니다.
> - 이들의 역할은 클래스 필드의 값을 안전하게 읽거나 수정할 수 있게 하는 것입니다.
> - 특히 setter의 경우 가져오는 값의 데이터 타입을 지정하기 때문에 객체의 무결성이 증가됩니다.

### 📌 Eclipse에서 Getter and Setter 메서드 생성 방법
> - Getter and Setter 메서드는 IDE를 통해 쉽게 생성 가능합니다.
> - 변수가 선언된 클래스 필드를 마우스 우클릭합니다.
> - private 접근제한자를 이용하여 선언된 변수를 선택합니다.
> - 선택을 마쳤으면 하단의 Generate 버튼을 클릭하면 Getter and Setter가 자동 생성됩니다.
> - 물론 Getter and Setter 학습을 위해 메서드를 직접 타이핑하여 선언하여도 괜찮습니다.

### 📌 Getter and Setter 입력 예시
> - 아래는 자동차 클래스 필드에서 Getter and Setter를 생성한 예시입니다.
> - Getter and Setter의 실무적인 역할은 변수로 파생될 수 있는 기능만 사용하는 것입니다.

``` java
// 객체 접근제한자는 public으로 설정하였습니다.
public class Car {

    // 변수의 접근제한자를 private으로 설정하였습니다.
    private String carName;
    private String carCompany;
    private int carPrice;

    /* Getter */
    // 값을 반환하는 Getter 메서드를 선언하였습니다.
    public String getCarName() {
        return this.carName;
    }

    public String getCarCompany() {
        return this.carCompany;
    }

    public int getCarPrice() {
        return this.carPrice;
    }
    
    /* Setter */
    // 값을 가져오는 Setter 메서드를 선언하였습니다.
    // 가져올 값의 데이터 타입을 지정함으로써 객체의 무결성이 증가됩니다.
    public void setCarName(String carName) {
        this.carName = carName;
    }

    public void setCarCompany(String carCompany) {
        this.carCompany = carCompany;
    }

    public void setCarPrice(int carPrice) {
        this.carPrice = carPrice;
    }

}
```

<br>

### 🔔 return and void
### 📌 return 키워드와 void 타입의 관계
> - void 타입은 메서드 기능 구현 시 return으로 반환될 데이터가 없을 때 사용됩니다.
> - void 타입은 데이터 타입으로 분류되며 메서드의 기능을 예측할 수 있게 합니다.
> - return 키워드는 메서드 실행 시 변수 또는 값을 반환하는 기능을 수행합니다.
> - 만일 return 키워드로 반환되는 것이 있을 경우 void 대신 데이터 타입을 입력해야 됩니다.

### 📌 파라미터
> - 파라미터의 뜻은 매개변수이며 메서드가 실행될 때 필요한 값을 의미합니다.
> - 예를들면 setter 메서드를 통해 클래스 내부에 저장될 값의 속성을 설정할 수 있습니다.
> - 파라미터, return 키워드, void 타입의 사용 예시는 아래와 같습니다.

### 📌 여러 형태의 메서드
> - 메서드는 기능에 따라 파라미터 또는 반환될 데이터가 있거나 없습니다.

``` java
public static void main(String[] args) {

    // 파라미터가 있고 return도 있는 메서드
    Arrays.toString(arr01);

    // 파라미터가 있고 return은 없는 메서드
    System.out.println("여러 형태의 메서드");

    // 파라미터가 없고 return은 있는 메서드
    Math.random();

    // 파라미터가 없고 return도 없는 메서드
    System.out.println();

}
```

<br>
<br>
<br>
