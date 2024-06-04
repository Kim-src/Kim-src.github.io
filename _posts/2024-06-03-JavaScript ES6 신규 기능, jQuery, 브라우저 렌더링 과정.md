---
title: JavaScript ES6 신규 기능, jQuery, 브라우저 렌더링 과정
date: 2024-06-03 18:00:00 +09:00
categories: [1. Fundamental, Frontend]
tags: [Fundamental, HTML, CSS, JavaScript, Frontend, JavaScript, Anonymous Function, Callback Function, Synchronous Function, Asynchronous Function, jQuery]
---

<!-- 2024-05-31 글 작성 시작; 2024-06-04 페이지 호출 완료 -->
<h2>강의 내용 복습 : 코리아IT 신촌점 강의 (2024-05-22,23,27 강의)</h2>
> - Tool :  
<img alt="VS Code" src="https://img.shields.io/badge/-VS_Code-007ACC?style=flat-square&logo=visual-studio-code&logoColor=white">
<img alt="JavaScript" src="https://img.shields.io/badge/-JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black">
<img alt="jQuery" src="https://img.shields.io/badge/-jQuery-0769AD?style=flat-square&logo=jquery&logoColor=white">

<br>

### 🔔 JavaScript
### 📌 JavaScript 개념 소개
> - JavaScript는 웹 페이지에 동적 기능을 부여하기 위해 개발되었습니다.
> - JavaScript는 변수 선언/수정이 자유롭고 데이터 타입이 동적으로 결정되는 것이 특징입니다.
> - JavaScript는 주로 웹 브라우저 내에서 실행되거나 Node.js같은 환경에서 직접 실행됩니다.
> - JS는 스크립팅 언어로 분류되는데, 스크립팅 언어란 기능 실행이 목적인 언어를 의미합니다.
> - 스크립팅 언어는 복잡한 컴파일 과정이 필요없고 인터프리터에 의해 실행됩니다.
> - 인터프리터란 소스 코드를 기계어로 변환하지 않고 직접 실행하는 프로그램을 의미합니다.

### 📌 인터프리터(interpreter) vs 컴파일러(compiler)
> - 프로그래밍 언어를 실행하기 위해 사용되는 인터프리터는 컴파일러와 대조되는 도구입니다.
> - 인터프리터는 사람이 이해할 수 있는 소스 코드를 순서대로 한 줄씩 해석하고 실행합니다.
> - 컴파일러는 사람이 이해할 수 있는 코드를 바이너리 코드로 구성된 기계어로 변환합니다.
> - 인터프리터에 의해 실행되는 언어는 JavaScript, Python, PHP 등이 있습니다.
> - 컴파일러에 의해 실행되는 언어는 Java, C++, C, Swift 등이 있습니다.

### 📌 JavaScript vs Java 유사점
> - JavaScript와 Java는 명확히 다른 언어이지만 코드 작성 방법은 비슷한 편입니다.
> - JavaScript에서는 Java와 마찬가지로 변수와 메서드를 선언하고 작성해야 됩니다.
> - Java에서는 변수 선언 시 String, int 등의 데이터 타입을 지정해야 됩니다.
> - JavaScript에서는 변수 선언 시 const, let, var 등의 키워드를 입력해야 됩니다.
> - Java에서는 메서드를 생성할 때 보통 이미 정의된 메서드를 사용합니다.
> - JavaScript에서도 메서드를 생성할 때 보통 이미 정의된 메서드를 사용합니다.
> - 그런데 JavaScript는 Java보다 코드 작성이 유연하고 데이터 타입이 동적으로 결정됩니다.
> - 예를들면 Java의 Array의 경우 한 번 선언하면 배열의 크기와 요소를 수정하기 번거롭습니다.
> - 이와 다르게 JavaScript의 배열은 데이터 추가/수정/삭제가 자유롭습니다.
> - 이처럼 JavaScript는 코드 작성이 쉽지만 유지/보수가 어렵고 휴먼 에러 발생 위험성이 큽니다.

### 📌 JavaScript vs Java 차이점
> - JavaScript는 스크립트 언어, Java는 컴파일 언어로 분류됩니다.
> - JavaScript는 인터프리터, Java는 컴파일러에 의해 실행됩니다.
> - JavaScript로 작성된 소스 코드는 인터프리터에 의해 직접적으로 실행됩니다.
> - Java로 작성된 코드는 컴파일러에서 바이트 코드로, JVM에서 기계어로 변환된 후 실행됩니다.
> - JavaScript 코드는 객체/함수/블록으로 관리되고 Java 코드는 객체/클래스로 관리됩니다.
> - JavaScript는 프로토타입 기반의 객체 지향 언어이며 객체를 생성하고 관리합니다.
> - Java는 클래스 기반의 객체 지향 언어이며 객체를 정의하고 인스턴스화(실체화)합니다.
> - 클래스 기반이기 때문에 Java의 모든 코드는 클래스 내부에 위치해야 됩니다.
> - ES6 이후 JavaScript에서도 클래스를 사용할 수 있지만 함수나 블록으로 코드가 관리됩니다.

### 📌 렌더링 과정에서의 JavaScript
> - 브라우저에서 웹 문서를 렌더링하는 과정은 아래와 같습니다.
> - JavaScript의 경우 HTML 파싱 중 ```<script>``` 태그가 파싱되었을 때 실행됩니다.
> - 브라우저에서 웹 문서 렌더링을 완료하면 뷰포트(viewport; 실제 화면)에 내용이 표시됩니다.
> - 참고로 DOM (Document Object Model)은 웹 페이지를 구성하는 요소를 노드로 표현한 것입니다.
>    - HTML 파싱 : 렌더링 시 브라우저는 HTML 문서를 파싱하며 DOM 트리를 생성합니다.
>    - CSS 파싱 : CSS 파일들이 파싱되어 HTML 요소의 스타일을 정의하는 CSSOM 트리가 생성됩니다.
>    - 렌더 트리 생성 : DOM과 CSSOM이 결합된, 실제 화면에 보여지는 렌더 트리를 형성합니다.
>    - 레이아웃 : 렌더 트리 형성 후 각 요소가 화면에서 차지하는 위치와 크기를 계산합니다.
>    - 페인팅 : 레이아웃을 토대로 요소들이 화면에 표시됩니다.
>    - JavaScript 실행 : HTML 파싱 중 script 태그가 파싱되면 JavaScript 기능을 실행합니다.

<br>

### 🔔 ES6 이후 JavaScript 신규 기능
### 📌 ES6 (ECMAScript 2015)
> - ECMA (European Computer Manufactures Association)는 정보 통신 기술 표준 유관 협회입니다.
> - ECMA는 다양한 기술 표준을 개발하고 관리하는 곳이며 가장 유명한 것은 ECMAScript 표준입니다.
> - ECMAScript는 스크립팅 언어들의 표준이며 이에 대한 구현체 중 하나는 JavaScript입니다.
> - ECMAScript 표준은 프로그래밍 언어의 문법, 유형, 기능 실행 모델 등을 정의합니다.
> - ECMAScript의 목적은 개발자들이 일관된 프로그래밍을 할 수 있는 환경을 구성하는 것입니다.
> - ES6 버전에서는 아래와 같은 JavaScript 개선 사항들을 도입하였습니다.
>    - 변수 선언 방식 추가 : const 및 let 키워드 추가
>    - 함수 정의 방식 추가 : 화살표 함수(Arrow Functions) 추가
>    - 클래스 기반의 문법 도입 : 기존 프로토타입 기반의 문법에서 추가된 문법
>    - 변수 삽입 방식 추가 : 백틱(`) 기반의 ${expression} 구문 추가
>    - 코드 공유 방식 추가 : export, import 키워드를 사용하여 코드 모듈화 및 공유 가능

### 📌 JavaScript에서의 신규 변수 선언 방식
> - JavaScript는 변수를 선언할 때 const, let, var 키워드를 사용합니다.
> - JavaScript는 변수를 선언할 때 데이터 타입을 명시하지 않아도 괜찮습니다.
> - 왜냐하면 데이터 타입이 동적으로 결정되고 자동으로 할당되기 때문입니다.
> - ES6 이전에는 var 키워드가 변수/상수를 선언하는 주요 키워드였습니다.
> - 따라서 코드 작성 자체는 더욱 편리하였지만 유지/보수 측면에서는 다루기 어려웠습니다.
> - 이를 보완하기 위해 개발된 것이 const 및 let 키워드입니다.
> - 아래는 const, let, var 키워드를 사용하여 변수를 선언 및 값을 수정한 예시입니다.

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
</body>
<script>
    /* 최초 변수 선언 */
    const a = 10;
    let b = 20;
    var c = 30;

    /* 변수에 할당된 값 출력 */
    document.write(a);
    document.write("<br>");
    document.write(b);
    document.write("<br>");
    document.write(c);
    document.write("<br>");

    /* 변수에 할당된 값 수정 */
    // a 변수에 할당된 값 수정 불가(const 키워드 변수 선언으로 인한 값 재할당 불가)
    // 그럼에도 수정하려고 하면 동기적인 코드 처리로 인한 JavaScript 코드 실행 중지
    // a = 1000;
    b = 1000;
    c = 1000;

    /* 수정된 값 출력 */
    document.write(a);
    document.write("<br>");
    document.write(b);
    document.write("<br>");
    document.write(c);
    document.write("<br>");
</script>
</html>
```

### 📌 JavaScript에서의 신규 함수 정의 방식

### 📌 JavaScript에서의 클래스 기반 문법
> - ES6 이후 기존의 프로토타입 기반의 문법 이외에도 클래스 기반의 문법 사용이 가능해졌습니다.
> - Java와 유사하게 객체 단위로 변수 및 메서드를 정의할 수 있습니다.
> - 단, 프로토타입 기반 문법에 클래스 기반 문법이 추가된 것이지, 대체된 것은 아닙니다.
> - 객체 단위로 정의된 변수 및 메서드는 타 객체에서 생성자 및 점 연산자로 접근 가능합니다.
> - 참고로 코드 작성 방식이 유사하다고 설명한 것이지, 구동 방식이 유사하게 된 것은 아닙니다.
> - 왜냐하면 JavaScript 전체적인 실행 과정은 설명하기 복잡할 정도이기 때문입니다.
> - 한 예시로 JIT (Just-In-Time) 컴파일의 경우 실시간으로 코드를 기계어로 변환합니다.
> - 하지만 이는 인터프리팅 단계를 거친 후이며 JIT 컴파일로 성능을 최적화 한 것입니다.
> - 다양한 컴파일 방식이 있으며 이는 JavaScript 사용 목적이나 브라우저에 따라 다양합니다.
> - 아래는 클래스 기반 문법을 사용한 예시입니다.

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
</body>
<script>
    /* 부모 클래스 생성 */
    // class 키워드를 사용하여 Phone 클래스 생성
    class Phone {
        // constructor 키워드를 사용하여 클래스의 속성 생성
        constructor(model, company) {
            this.model = model;
            this.company = company;
        }

        // 클래스의 메서드 정의
        phoneInfo() {
            document.write(`이 스마트폰은 ${this.model}이고 ${this.company}에서 제작하였습니다.`);
        }
    }

    // 변수 및 인스턴스 생성(실질적인 값 할당)
    let myPhone = new Phone("S23 Ultra", "Samsung");
    myPhone.phoneInfo();

    document.write("<br>");

    /* 자식 클래스 생성 */
    // class 키워드를 사용하여 User 클래스 생성
    // extends 키워드를 사용하여 Phone 클래스 상속
    class User extends Phone {
        // constructor 키워드를 사용하여 클래스의 속성 생성
        constructor(model, company, user) {
            // super 키워드를 이용하여 부모 클래스 생성자 호출 및 초기화
            super(model, company);
            this.user = user;
        }

        // Phone 클래스의 phoneInfo 메서드 오버라이딩
        phoneInfo() {
            document.write(`이 스마트폰은 ${this.model}이고 ${this.company}에서 제작하였으며 사용자는 ${this.user}입니다.`);
        }
        // Phone 클래스의 
    }

    // 변수 및 인스턴스 생성
    let myPhoneUser = new User("S23 Ultra", "Samsung", "Kim");
    myPhoneUser.phoneInfo();
</script>
</html>
```

### 📌 JavaScript에서의 신규 변수 삽입 방식
> - ES6 이후 백틱(`)을 사용하여 문자열 등에 변수를 정적/동적으로 삽입시킬 수 있습니다.
> - 출력할 문자열을 백틱(`)으로 감싸고 '${}' 내부에 변수를 입력하면 적용됩니다.
> - 기존에는 '변수 + "문자열" + 변수 + "문자열" 등으로 변수 삽입 과정이 번잡하였습니다.
> - 추가적으로 줄바꿈 역시 '\n'을 사용하지 않고도 간단히 처리할 수 있습니다.
> - 아래는 백틱 기반으로 문자열을 삽입하는 방식에 대한 예시입니다.

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
</body>
<script>
    // 문자열 내에 변수 삽입
    let name = "JavaMan";
    let skill = "JavaScript";
    
    document.write(`${name}이 Java가 아닌 ${skill}을 학습한다.`);

    document.write("<br>");

    // 문자열 내에 표현식(수학 공식) 삽입
    let price = 10000;
    let tax = 0.1;

    document.write(`대한민국에서 국세를 ${price}원 납부했으면, 지방세는 ${price * tax}원 납부해야 됩니다.`);

    document.write("<br>");

    // 문자열 내에 문장 삽입
    // 콘솔 출력 시 줄바꿈 발생
    // 뷰포트 출력 시 줄바꿈 미발생
    console.log(`아버지가
    방에
    들어가신다.`);

    let sentence = `아버지가
    방에
    들어가신다.`;

    console.log(sentence);
</script>
</html>
```

### 📌 JavaScript에서의 코드 모듈화 및 공유 방식
> - ES6 이후 export, import 키워드를 이용하면 코드를 모듈화 및 공유할 수 있습니다.
> - 모듈화 하는 방법은 다양하며 개별 함수, 여러 함수, 하나의 객체 등을 관리할 수 있습니다.
> - 코드 모듈화 시 주의해야 할 점은 script 태그의 type을 module로 지정해야 된다는 것입니다.
> - 또한 import 대상 파일이 JavaScript 확장자여야 된다는 것입니다.
> - 위 두 가지 규칙을 지켜주지 않으면 브라우저의 렌더링 과정에서 에러가 발생됩니다.
> - 추가적으로 브라우저 뷰포트에 출력하려고 하면 문제가 발생되었기에 콘솔에 출력하였습니다.
> - 아래는 객체를 모듈화하고 공유하는 방식에 대한 예시입니다.

``` javascript
export function add(a, b) {
    return a + b;
}

export function substract(a, b) {
    return a - b;
}

// 객체 변수 자체는 변경 불가
const calculateOperator = {
    // 함수에 할당되는 값은 변경 가능
    multiple(a, b) {
        return a*b;
    },
    divide(a, b) {
        return a / b;
    }
}

// 기본적으로 내보낼 값을 default로 설정했기에 import 편리
// Java와 달리 접근제한자 개념과 상이
// 즉, export default 자체는 하나의 키워드 역할
export default calculateOperator;
```

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>claculator</title>
</head>
<body>
</body>
<script type="module">
    // 이름으로 내보낸 개별 함수 가져오기
    import {add, substract} from './clacOperator.js';

    // 객체로 내보낸 모듈 가져오기
    import calculateOperator from './clacOperator.js';

    // 가져온 모듈을 활용하여 수학 계산
    console.log(add(10, 20));
    console.log(substract(10, 20));
    console.log(calculateOperator.multiple(10, 20));
    console.log(calculateOperator.divide(10, 20));
</script>
</html>
```

``` console
claculator.html:56 30
claculator.html:57 -10
claculator.html:58 200
claculator.html:59 0.5
```

<br>

### 🔔 Java 함수 개념
### 📌 콜백 함수
### 📌 익명 함수
### 📌 동기 함수
### 📌 비동기 함수

<br>

### 🔔 jQuery
### 📌 부제목
> - 글 내용

<br>

### 🔔 JavaScript 실습
### 📌 JavaScript 출력 이해
> - console 객체의 log 메서드, document 객체의 wirte 메서드를 사용하였습니다.
> - console.log에 파라미터를 삽입하면 입력한 내용이 브라우저 콘솔창에 출력됩니다.
> - document.wirte에 파라미터를 삽입하면 입력한 내용이 브라우저 뷰포트에 출력됩니다.

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
</body>
<script>
    console.log("콘솔창에 문구 출력1");
    console.log("콘솔창에 문구 출력2");
    console.log("콘솔창에 문구 출력3");

    document.write("브라우저에 문구 출력1 <br>");
    document.write("브라우저에 문구 출력2 <br>");
    document.write("브라우저에 문구 출력3");
</script>
</html>
```

### 📌 JavaScript 변수 및 메서드 이해
> - const, let, var 키워드를 이용하여 변수를 선언하였습니다.
> - 선언된 변수를 write 메서드를 이용하여 뷰포트에 출력하였습니다.
> - 초기 선언된 변수의 배열에 할당된 요소를 수정 후 출력하였습니다.
> - 수정된 변수의 배열에 할당된 요소에 정수 100을 추가 후 출력하였습니다.
> - join 메서드를 활용하여 배열 요소를 출력하였습니다.
> - for 반복문을 활용하여 배열 요소를 출력하였습니다.
> - 향상된 for 반복문을 활용하여 배열 요소를 출력하였습니다.

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
</body>
<script>
    /* 변수 선언 */
    // const 키워드를 이용하여 변수 선언
    const arrayConstEmpty = [];
    const arrayConstFilled = [1, 2, 3, 4, 5];

    // let 키워드를 이용하여 변수 선언
    let arrayLetEmpty = [];
    let arrayLetFilled = [1, 2, 3, 4, 5];

    // var 키워드를 이용하여 변수 선언
    var arrayVarEmpty = [];
    var arrayVarFilled = [1, 2, 3, 4, 5];

    // document 객체의 write 메서드를 이용하여 정의된 변수 출력
    // document : DOM (Document Object Model)에 접근할 수 있도록 하는 객체
    document.write(arrayConstEmpty);
    document.write("<br>");
    document.write(arrayConstFilled);
    document.write("<br>");
    document.write(arrayLetEmpty);
    document.write("<br>");
    document.write(arrayLetFilled);
    document.write("<br>");
    document.write(arrayVarEmpty);
    document.write("<br>");
    document.write(arrayVarFilled);
    document.write("<br>");

    document.write("<br>");
    document.write("<br>");
    document.write("<br>");

    /* 변수 요소 수정 */
    // 정의된 변수를 이용하여 배열 요소 수정
    // const 키워드로 정의된 변수는 요소 수정 불가
    // arrayConstEmpty = [10, 20, 30, 40, 50];

    // 정의된 변수를 이용하여 배열 요소 수정
    arrayLetEmpty = ['A', 'B', 'C', 'D', 'E'];

    // 정의된 변수를 이용하여 배열 요소 수정
    // 최하단에 위치한 배열 요소로 최종 적용
    arrayVarEmpty = [10, 20, 30, 40, 50];
    arrayVarEmpty = [13, 14, 15];

    // 배열 요소 수정 결과 출력
    document.write(arrayConstEmpty);
    document.write("<br>");
    document.write(arrayLetEmpty);
    document.write("<br>");
    document.write(arrayVarEmpty);
    document.write("<br>");

    document.write("<br>");
    document.write("<br>");
    document.write("<br>");

    /* 변수 요소 추가 */
    // push 메서드를 이용하여 배열 요소에 정수 100 삽입
    arrayLetEmpty.push(100);
    arrayLetFilled.push(100);
    arrayVarEmpty.push(100);
    arrayVarFilled.push(100);

    // 배열 요소 추가 결과 출력
    document.write(arrayConstEmpty);
    document.write("<br>");
    document.write(arrayConstFilled);
    document.write("<br>");
    document.write(arrayLetEmpty);
    document.write("<br>");
    document.write(arrayLetFilled);
    document.write("<br>");
    document.write(arrayVarEmpty);
    document.write("<br>");
    document.write(arrayVarFilled);
    document.write("<br>");

    document.write("<br>");
    document.write("<br>");
    document.write("<br>");

    /* join 메서드 */
    // join 메서드를 이용하여 변수에 할당된 값을 한꺼번에 출력하려고 합니다.
    // join 메서드는 배열의 모든 요소를 연결하여 하나의 문자열을 생성합니다.
    // joint 메서드는 구분자(쉼표 등)를 이용하여 결과물의 형식을 조정합니다.
    document.write(arrayConstEmpty.join(', '));
    document.write("<br>");
    document.write(arrayConstFilled.join(', '));
    document.write("<br>");
    document.write(arrayLetEmpty.join(', '));
    document.write("<br>");
    document.write(arrayLetFilled.join(', '));
    document.write("<br>");
    document.write(arrayVarEmpty.join(', '));
    document.write("<br>");
    document.write(arrayVarFilled.join(', '));
    document.write("<br>");

    document.write("<br>");
    document.write("<br>");
    document.write("<br>");

    /* for 반복문 */
    // for 반복문을 이용하여 배열 요소를 인덱스 순서대로 출력하였습니다.
    // Java의 for 문과 달리 i는 데이터 타입이 아닌 const, let, var 키워드로 선언해야 됩니다.
    for(let i = 0; i < arrayLetFilled.length; i++) {
        document.write(arrayLetFilled[i]);
    }

    document.write("<br>");
    document.write("<br>");
    document.write("<br>");
    
    /* 향상된 for 반복문 */
    // for 반복문을 이용하여 배열 요소를 인덱스 순서대로 출력하였습니다.
    // Java의 for 문과 달리 i는 데이터 타입이 아닌 const, let, var 키워드로 선언해야 됩니다.
    for(let forArrayLetFilled of arrayLetFilled) {
        document.write(forArrayLetFilled);
    }
</script>
</html>
```

<br>
<br>
<br>
