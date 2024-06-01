---
title: JavaScript jQuery, 익명 함수, 동기 함수, 비동기 함수 개념
date: 2024-05-31 18:00:00 +09:00
categories: [1. Fundamental, Frontend]
tags: [Fundamental, HTML, CSS, JavaScript, Frontend, JavaScript, Anonymous Function, Callback Function, Synchronous Function, Asynchronous Function, jQuery]
---

<!-- 2024-05-31 글 작성 시작; 2099-01-01 페이지 호출 완료 -->
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

### 📌 JavaScript vs Java 유의점
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

### 🔔 JavaScript 주요 개념
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
>    - 문자열 삽입 방식 추가 : 백틱`````` 기반의 `${expression}` 구문 추가

### 📌 JavaScript에서의 변수 생성 키워드
> - JavaScript는 변수를 선언할 때 const, let, var 키워드를 사용합니다.
> - JavaScript는 변수를 선언할 때 데이터 타입을 명시하지 않아도 괜찮습니다.
> - 왜냐하면 데이터 타입이 동적으로 결정되고 자동으로 할당되기 때문입니다.
> - ES6 이전의 경우 var 키워드가 변수/상수를 선언하는 주요 키워드였습니다.
> - 따라서 코드 작성 자체는 더욱 편리하였지만 유지/보수 측면에서는 다루기 어려웠습니다.
> - 이를 보완하기 위해 개발된 것이 const 및 let 키워드입니다.

### 📌 const, let, var 키워드 비교

### 📌 콜백 함수
### 📌 익명 함수
### 📌 동기 함수
### 📌 비동기 함수

<br>

### 🔔 jQuery
### 📌 부제목
> - 글 내용

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
