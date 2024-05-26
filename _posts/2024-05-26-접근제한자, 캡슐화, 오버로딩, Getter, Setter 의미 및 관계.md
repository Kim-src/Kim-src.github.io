---
title: 접근제한자, 캡슐화, 오버로딩, Getter, Setter 의미 및 관계
date: 2024-05-26 18:00:00 +09:00
categories: [1. Fundamental, Java]
tags: [Java, Fundamental, Access Modifier, Encapsulation, Overloading, Information Hiding, Modularity, Getter, Setter, Executable Class, DTO Class, VO Class, DAO Class, Utility Class, Parameter, Return, Void]
---

<!-- 2024-05-20 글 작성 시작; 2024-05-26 페이지 호출 완료 -->
<h2>강의 내용 복습 : 코리아IT 신촌점 Java 강의 (2024-04-29,30 강의)</h2>
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
> - 외부로부터의 접근이 개방되어 있기 때문에 제한이 없습니다.
> - public은 보통 클래스 자체와 getter 및 setter 메서드 등에 사용됩니다.
> - public 접근제한자로 선언된 객체에 접근하려면 점(.) 연산자를 이용하면 됩니다.

### 📌 private 접근제한자
> - 외부로부터의 접근이 제한되어 있는 접근제한자입니다.
> - 동일 패키지에 있더라도 getter 및 setter 등 특정 메서드만을 통해서만 접근 가능합니다.
> - private은 보통 데이터가 저장되는 변수에 선언합니다.

### 📌 protected 접근제한자
> - 외부로부터의 접근이 부분적으로 허용되어 있는 접근제한자입니다.
> - 동일 패키지에 있을 경우 자유로운 접근이 가능합니다.
> - 외부 패키지에 있더라도 상속받은 하위 클래스에서는 자유로운 접근이 가능합니다.
> - 따라서 protected 접근제한자는 상속 관계인 클래스들끼리의 연결성을 제공합니다.

### 📌 default
> - 접근제한자를 지정해두지 않으면 default로 자동 지정됩니다.
> - 이 경우 동일 패키지의 다른 클래스에서만 접근 가능합니다.

<br>

### 🔔 응용 개념
### 📌 캡슐화
> - 캡슐화는 객체 지향 프로그래밍과 유관한 추상적인 개념입니다.
> - 캡슐화는 프로그래밍 중 변수와 메서드를 하나의 클래스로 결합하는 과정을 의미합니다.
> - 외부에서 캡슐화 된 데이터에 접근하기 위해서는 허용된 특정 메서드만을 사용해야 됩니다.
> - 캡슐화의 목적은 정보 은닉, 데이터 보호, 모듈화를 실현하는 것입니다.
>    - 정보 은닉 : 객체의 내부 구현을 변경하여도 외부의 코드에 영향을 주지 않습니다.
>    - 데이터 보호 : 데이터의 잘못된 접근이나 수정을 방지할 수 있습니다.
>    - 모듈화 : 각 클래스가 특정 기능을 수행하게 하여 코드의 복잡성을 감소시킬 수 있습니다.

### 📌 오버로딩(Overloading)
> - 오버로딩은 동일한 클래스 내에서 동일한 이름의 메서드를 여러 개 정의하는 기능을 의미합니다.
> - 오버로딩은 프로그래밍의 유연성과 가독성을 증대시킵니다.
> - 동일한 이름의 메서드는 동일한 기능을 수행하며 아래와 같은 규칙을 따릅니다.
>    - 동일한 메서드 이름 : 오버로딩은 메서드 이름이 동일해야 됩니다.
>    - 상이한 파라미터 : 파라미터의 타입, 개수, 순서가 하나 이상 달리 정의되어야 합니다.
>    - 자유로운 반환 타입 : 반환 타입은 메서드를 구분하는 데 사용되지 않습니다.

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
> - 이들의 역할은 클래스 필드(변수)의 값을 안전하게 읽거나 수정할 수 있게 하는 것입니다.
> - 특히 setter의 경우 가져오는 값의 데이터 타입을 지정하기 때문에 객체의 무결성이 증가됩니다.

### 📌 Eclipse에서 Getter and Setter 메서드 생성 방법
> - Getter and Setter 메서드는 IDE를 통해 쉽게 생성 가능합니다.
> - 변수가 선언된 객체의 작업 공간을 마우스로 우클릭합니다.
> - private 접근제한자를 이용하여 선언된 변수를 선택합니다.
> - 선택을 마쳤으면 하단의 Generate 버튼을 클릭하면 Getter and Setter가 자동 생성됩니다.
> - 물론 Getter and Setter 학습을 위해 메서드를 직접 타이핑하여 선언하여도 괜찮습니다.

### 📌 Car 객체 생성
> - 아래는 Car 객체의 필드(변수)를 대상으로 Getter and Setter를 정의한 예시입니다.
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
    // Getter의 경우 값을 반환해야 되기 때문에 return 키워드가 있습니다.
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
    // 값을 저장하는 Setter 메서드를 선언하였습니다.
    // Setter의 경우 값을 가져와야 되기 때문에 파라미터를 지정해야 됩니다.
    // 외부에서 Setter를 사용할 경우 데이터 타입에 맞는 Scanner 기능 등을 사용하면 됩니다.
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

### 🔔 응용 실습
### 📌 기본 생성자
> - Java에서 상위 클래스에 기본 생성자를 정의하면 하위 클래스에서 호출을 생략할 수 있습니다.
> - 예를들면 하위 클래스에 ```Car car = new Car();```를 입력하지 않아도 됩니다.
> - 그렇다고 하위 클래스에 상위 클래스를 호출하지 않아도 되는 것은 아닙니다.
> - 대신 하위 클래스에서 별도로 호출하지 않아도 컴파일 과정에서 super()가 삽입됩니다.
> - super()는 기본 생성자를 호출하는 코드이며 컴파일러가 자동으로 삽입시킵니다.

### 📌 DTO, VO, DAO, Utility 객체
> - 객체는 각기 다양한 목적과 기능을 갖고 있으며 대표적인 객체는 아래와 같습니다.
>    - 📌 DTO (Data Transfer Object)
>    - 데이터를 저장하기 위한 필드(변수)와 데이터에 접근하기 위한 메서드를 포함합니다.
>    - DTO의 예시로는 아래의 Car 객체가 있습니다.
>    - 📌 VO (Value Object)
>    - DTO와 비슷한 역할을 하는 객체입니다.
>    - 전통적으로는 데이터를 저장하는 역할만 하고 로직을 포함하지 않는 객체로 구분됩니다.
>    - 현대적으로는 DTO와 큰 차이가 없는 것으로 평가됩니다.
>    - 📌 DAO (Data Access Object)
>    - 데이터베이스 또는 외부 데이터 소스와의 상호작용을 하는 역할을 합니다.
>    - 코드에 SQL (Structured Query Language)을 포함합니다.
>    - 📌 Utility 객체
>    - 유틸리티 객체의 예시로는 random 메서드를 포함하는 Math 객체가 있습니다.
>    - 여러 객체에 다양한 목적으로 활용하는 객체를 일컫습니다.

### 📌 Car DTO 클래스 생성
> - 자동차 정보 데이터 관리를 위한 객체를 생성하였습니다.
> - 안전한 데이터 삽입 및 삭제 등을 위해 변수는 private 접근제한자로 선언하였습니다.
> - 그리고 변수로 파생되는 기능을 사용하기 위해 getter 및 setter 메서드를 사용하였습니다.
> - 저장된 데이터를 일괄적으로 처리할 수 있도록 carInfo 메서드를 정의하였습니다.
> - 오버로딩 된 메서드의 경우 규칙에 맞게 5가지를 정의하였습니다.
> - 참고로 컴파일러는 메서드를 구분할 때 파라미터의 타입, 개수, 순서에 집중합니다.
> - 즉, 사람 보기 좋게 경우의 수에 맞게 메서드를 정의하면 에러가 발생될 수 있습니다.

``` java
public class CarDTO {

    // 변수의 접근제한자를 private으로 설정하였습니다.
    private String carName;
    private String carCompany;
    private int carPrice;

    
    /* Getter */
    // 값을 반환하는 Getter 메서드를 선언하였습니다.
    // Getter의 경우 값을 반환해야 되기 때문에 return 키워드가 있습니다.
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
    // 값을 저장하는 Setter 메서드를 선언하였습니다.
    // Setter의 경우 값을 가져와야 되기 때문에 파라미터를 지정해야 됩니다.
    // 외부에서 Setter를 사용할 경우 데이터 타입에 맞는 Scanner 기능 등을 사용하면 됩니다.
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
    
    // 저장된 데이터를 일괄적으로 출력하기 위한 메서드를 정의하였습니다.
    public void carInfo() {
    	System.out.print("모델명 = " + this.getCarName());
    	System.out.print(", 제조사 = " + this.getCarCompany());
    	System.out.println(", 판매가 = " + this.getCarPrice());
    }
    
    
    /* 오버로딩 */
    // 데이터를 유연하게 처리하기 위해 CarDTO 메서드를 오버로딩하였습니다.
    // 오버로딩의 규칙은 파라미터
    public CarDTO() {
    }
    
    public CarDTO(String carName, String carCompany, int carPrice) {
    	this.carName = carName;
    	this.carCompany = carCompany;
    	this.carPrice = carPrice;
    }
    
    public CarDTO(String carName, String carCompany) {
    	this.carName = carName;
    	this.carCompany = carCompany;
    }
    
    public CarDTO(String carName, int carPrice) {
    	this.carName = carName;
    	this.carPrice = carPrice;
    }
    
    public CarDTO(String carName) {
    	this.carName = carName;
    }
    
    public CarDTO(int carPrice) {
    	this.carPrice = carPrice;
    }
    
}
```

### 📌 CarInfo 기본 클래스 생성
> - CarDTO 객체의 필드에 데이터를 저장하기 위해 CarInfo에서는 Scanner를 이용하였습니다.
> - Array를 이용하여 데이터가 인덱스 순서대로 저장되도록 설정하였습니다.
> - 참고로 필드(field)란 클래스 내에서 데이터가 저장되는 변수를 의미합니다.

``` java
public class CarInfo {
	
	public static void main(String[] args) {
		
		// Array를 이용하여 데이터를 일괄적으로 관리하였습니다.
		CarDTO[] carList = new CarDTO[5];
		// 입력을 통해 Car 데이터가 저장될 수 있도록 설정하였습니다.
		Scanner scan = new Scanner(System.in);
		
		// 순차적인 데이터 저장을 위해 반복문을 설정하였습니다.
		for(int i = 0; i < carList.length; i++) {
			// public 접근제한자의 Car 클래스를 호출하였습니다.
			// 매 반복문마다 새로운 인스턴스를 생성하였습니다.
			CarDTO car = new CarDTO();
			// 값은 Scanner 입력을 통해 할당시켰습니다.
			System.out.print((i+1) + "번째 자동차 모델명을 입력하세요. = ");
			car.setCarName(scan.next());
			System.out.print((i+1) + "번째 자동차 제조사를 입력하세요. = ");
			car.setCarCompany(scan.next());
			System.out.print((i+1) + "번째 자동차 판매가를 입력하세요. = ");
			car.setCarPrice(scan.nextInt());
			
			// 할당된 값은 carList에 일괄적으로 할당시켰습니다.
			// Array 대신 List를 이용하면 데이터 타입이 통일되어야 되기 때문에 이 부분에서 문제가 되었습니다.
			// List를 더 활용해보는 경험이 필요합니다.
			carList[i] = car;
			
		}
		
		scan.close();
		System.out.println();
		
		// 보유중인 자동차 정보를 향상된 for 반복문으로 출력하였습니다.
		// 향상된 for 반복문 사용 시 개별 변수를 다시 선언해야 됩니다.
		// 향상된 for 반복문은 carList의 전체 요소에 순차적으로 접근합니다.
		// carInfo()의 경우 Car 객체에 자동차 정보를 출력하도록 정의한 상태입니다.
		System.out.println("* 보유중인 자동차 정보");
		for(CarDTO car : carList) {
			car.carInfo();
		}
				
	}

}
```

### 📌 CarInfo 응용 클래스 생성
> - CarDTO 객체의 필드에 데이터를 저장하기 위해 CarInfo에서는 Scanner를 이용하였습니다.
> - CarInfo 기본 클래스와 응용 클래스의 차이점은 오버로딩 및 setter 메서드의 적용 여부입니다.
> - 응용 클래스에서는 trim 메서드를 이용하여 데이터 입력이 없을 경우를 처리하였습니다.
> - 그리고 isEmpty 메서드를 이용하여 경우에 따른 조건문을 작성하였습니다.
> - 참고로 trim 및 isEmpty의 경우 Java의 String 클래스에 기본적으로 내장된 메서드입니다.

### 📌 Setter 메서드의 효용성
> - 아래 구현된 CarInfoUpdate 클래스는 setter 메서드를 사용하고 있지 않습니다.
> - 이유는 생성자를 통해 CarList[i]에 데이터가 입력되며 초기화되었기 때문입니다.
> - 이미 CarDTO에 파라미터 값이 채워졌기 때문에 객체의 상태를 다시 변경할 필요가 없습니다.

``` java
import java.util.InputMismatchException;
import java.util.Scanner;

public class CarInfoUpdate {

	public static void main(String[] args) {
		
		// Array를 이용하여 데이터를 일괄적으로 관리하였습니다.
		CarDTO[] carList = new CarDTO[1];
		// 입력을 통해 Car 데이터가 저장될 수 있도록 설정하였습니다.
		Scanner scan = new Scanner(System.in);
		// 예외 처리를 위해 carPrice 변수를 0으로 초기화하였습니다.
		int carPrice = 0;
		
		// 순차적인 데이터 저장을 위해 반복문을 설정하였습니다.
		for(int i = 0; i < carList.length; i++) {
			// 값은 Scanner 입력을 통해 할당시켰습니다.
			// 값이 없는 경우 공백을 입력받을 수 있도록 trim 메서드를 사용하였습니다.
			// 참고로 nextInt에는 trim 메서드를 이용할 수 없습니다.
			System.out.println((i+1) + "번째 자동차 정보를 입력하세요.");			
			System.out.print("자동차 모델명(없으면 공백 입력) = ");
			// 공백을 포함한 라인 전체를 입력으로 받기 위해 nextLine 메서드를 사용하였습니다.
			String carName = scan.nextLine().trim();
			System.out.print("자동차 제조사(없으면 공백 입력) = ");
			// 공백을 포함한 라인 전체를 입력으로 받기 위해 nextLine 메서드를 사용하였습니다.
			String carCompany = scan.nextLine().trim();
			System.out.print("자동차 판매가(없으면 0 입력) = ");
			// nextInt 메서드에 정수가 아닌 다른 값이 입력되었을 경우를 위해 try-catch block을 설정하였습니다.
			// nextInt 메서드를 실행시킨 뒤 예상되는 에러가 발생되면 carPrice 변수에 0을 할당시켰습니다.
			try {
				carPrice = scan.nextInt();
				// 입력 버퍼를 비우기 위해 개행 문자('\n' 등)를 제거하였습니다.
				scan.nextLine();
			} catch(InputMismatchException e) {
				carPrice = 0;
				// 입력 버퍼를 비우기 위해 개행 문자('\n' 등)를 제거하였습니다.
				scan.nextLine();
			}
			
			// 조건문에 따라 값이 제대로 입력된 데이터만 필드(변수)에 할당되게 설정하였습니다.
			// isEmpty 메서드를 이용하여 필드가 비어있는지 확인하였습니다.
			// 생성자를 이용하여 carList 배열에 저장될 데이터를 초기화하였습니다.
			// CarDTO의 오버로딩 정의 시와 다르게 경우의 수에 맞게 조건문을 작성하였습니다.
			// 데이터를 입력받지 못하는 경우 null 값을 할당시켰습니다.
			// 참고로 int의 경우 null 값을 받지 못합니다.
			if(!carName.isEmpty() && !carCompany.isEmpty() && carPrice != 0) {
				carList[i] = new CarDTO(carName, carCompany, carPrice);
			} else if(!carName.isEmpty() && !carCompany.isEmpty()) {
				carList[i] = new CarDTO(carName, carCompany);
			} else if(!carName.isEmpty() && carPrice != 0) {
				carList[i] = new CarDTO(carName, null, carPrice);
			} else if(!carCompany.isEmpty() && carPrice != 0) {
				carList[i] = new CarDTO(null, carCompany, carPrice);
			} else if(!carName.isEmpty()) {
				carList[i] = new CarDTO(carName, null);
			} else if(!carCompany.isEmpty()) {
				carList[i] = new CarDTO(null, carCompany);
			} else if(carPrice != 0) {
				carList[i] = new CarDTO(null, null, carPrice);
			} else if(carName.isEmpty() && carCompany.isEmpty() && carPrice == 0) {
				carList[i] = new CarDTO(null, null, 0);
			}
		}
		
		// Scanner 클래스는 리소스가 해제되기 전 또는 프로그램 종료 전까지 계속 실행됩니다.
		// 따라서 close 메서드를 이용하여 리소스를 해제시키고 리소스 누수를 방지하였습니다.
		scan.close();
		System.out.println();
		
		// 보유중인 자동차 정보를 향상된 for 반복문으로 출력하였습니다.
		// 향상된 for 반복문은 carList의 전체 요소에 순차적으로 접근합니다.
		// carInfo()의 경우 CarDTO에서 자동차 정보를 출력하도록 정의한 상태입니다.
		System.out.println("* 보유중인 자동차 정보");
		for(CarDTO car : carList) {
			car.carInfo();
		}
				
	}	
	
}
```

### 📌 CalculatorOperation 클래스 생성
> - 수학 계산 공식이 담긴 객체를 생성하였습니다.
> - add 메서드를 생성하고 2~5개의 정수를 더할 수 있도록 오버로딩하였습니다.
> - CalculatorOperation 객체에는 덧셈과 삼항연산자 연산 공식을 포함합니다.

``` java
public class CalculatorOperation {

	// add 메서드를 생성하고 2~5개의 정수를 더할 수 있도록 오버로딩하였습니다.
	// 2개의 정수를 더하는 계산식을 생성하였습니다.
	public int add(int a, int b) {
		return a + b;
	}
	
	// 3개의 정수를 더하는 계산식을 생성하였습니다.
	public int add(int a, int b, int c) {
		return a + b + c;
	}
	
	// 4개의 정수를 더하는 계산식을 생성하였습니다.
	public int add(int a, int b, int c, int d) {
		return a + b + c + d;
	}
	
	// 5개의 정수를 더하는 계산식을 생성하였습니다.
	public int add(int a, int b, int c, int d, int e) {
		return a + b + c + d + e;
	}
	
	// 삼항연산자로 정수 2개의 값을 비교하는 계산식을 생성하였습니다.
	public boolean ternary(int a, int b) {
		return a > b ? true : false;
	}
	
}
```

### 📌 Calculator 클래스 생성
> - CalculatorOperation 객체에 저장된 수학 공식에 실제 값을 할당시켜 구현하였습니다.

``` java
public class Calculator {
	
	public static void main(String[] args) {
		
		CalculatorOperation operator = new CalculatorOperation();
		CalculatorOperation add2 = new CalculatorOperation();
		CalculatorOperation add3 = new CalculatorOperation();
		CalculatorOperation add4 = new CalculatorOperation();
		CalculatorOperation add5 = new CalculatorOperation();
		
		// add 메서드에는 정수 2개 또는 5개만 할당이 가능합니다.
		System.out.println(operator.add(10, 20));
		System.out.println(operator.add(10, 20, 30));
		System.out.println(operator.add(10, 20, 30, 40));
		System.out.println(operator.add(10, 20, 30, 40, 50));
		System.out.println(add2.add(10, 20));
		System.out.println(add3.add(10, 20, 30));
		System.out.println(add4.add(10, 20, 30, 40));
		System.out.println(add5.add(10, 20, 30, 40, 50));
		// ternary 메서드는 값을 비교하는 기능이 있습니다.
		System.out.println(operator.ternary(10, 20));
		
	}

}
```

<br>
<br>
<br>
