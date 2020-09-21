---
title:  "TIL_JavaScript-3(타입변환, 대화상자, 연산자)"
excerpt: "자바스크립트(입문) 정리합니다"

categories:
  - TIL
  - JavaScript
tags:
  - TIL
  - JavaScript
comments: true
toc: true
toc_sticky: true
# other options
---


<h3>목차</h3>

- [1.변수](#1변수)
- [2.상수](#2상수)
- [3.데이터타입](#3데이터타입)
  

### 1.타입변환

- 변수는 타입이 고정되어있지않음 같은 변수에 다른 타입의 값을 대입할 수 있음
(자바스크립트만 가능, 다른 언어들은 내가 직접 타입을 정해줌)

1. 묵시적 타입 변환
    - 특정 타입의 값을 기대하는 곳에 다른 타입의 값이 오면, 자동으로 타입 변환해서 사용
    ```javascript
    let a = "10";
    let b = "20";
    let result = a + b; // 값 1020  (문자열의 연결)
    result = a - b; // -10 값 나옴 (숫자형으로 바꾼다음 계산함)
    ```
   
- JS는 덧셈만 연결이 되고 나머지 연산은 숫자로 변환해서 값을 구함
    ```javascript
    let c = "문자";
    result = a - c; // NaN 출력됨 (Not a Number) -- 정의되지않은 값이나 표현할 수 없는 값
    // NaN : 0을 0으로 나누거나, 숫자로 변환할 수 없는 연산을 시도할 경우 반환됨
    ```

    ```javascript
    let a = 10 + "문자열";
    console.log(a)
    let b = "3" * "5" ;
    console.log(b)
    // 문자열 형태지만 자동으로 숫자형으로 바뀌어서 계산함
    let c = 1 - "문자열";
    console.log(c)
    let d = "10" - "20";
    console.log(d)
    ```
  
2. 명시적 타입 변환
    - 자바스크립트는 자동으로 타입변환을 사용하지만, 명시적으로 타입을 변환할 방법도 제공함
        - Number() : 문자를 숫자로 변환
        - String() : 숫자나 불린의 값을 문자형으로 변환
        - Boolean() : 문자나 숫자등의 자료를 불린형으로 변환
        - Object() : 모든 자료형을 객체형으로 변환
        - ParseInt() : 문자를 int형으로 변환 // 정수형
        - ParseFloat() : 문자를 float형으로 변환 // 실수형

    ```javascript
    let num1 = "10";
    let num2 = "5";
    console.log("현재 num1의 타입 : " + (typeof num1)); // string
    console.log("num1 + num2 : " + (num1 + num2)); // 105
    console.log("Number(num1) + Number(num2) : " + (Number(num1) + Number(num2))); // 15
    ```

### 2.대화상자

- alert() : 사용자에게 메세지를 보여주고, 확인을 기다립니다
- confirm() : 사용자에게 메세지를 보여주고, 확인이나 취소를 누르면 그 결과를 불린값으로 반환함
- prompt() : 사용자에게 메세지를 보여주고 사용자가 입력한 !! 문자열 !! 을 반환함

    ```javascript
    window.alert("안녕하세요 JavaScript") // window는 생략가능
    let result = window.confirm('확인 또는 취소를 눌러주세요') // 앞에 변수값을 선언해줘야 값을 반환해서 넣어줌
    console.log(result); // 확인을 누르면 True, 취소를 누르면 False 값이 나옴
    
    prompt("이름을 입력하세요");
    let name = prompt('너의 이름을 알려줘');
    console.log(name);
    
    let num1 = window.prompt('첫번째 숫자입력');
    let num2 = prompt('두번째 숫자를 입력해줘여');
    console.log(num1 + num2); // 이렇게 쓰면 문자열 + 문자열 형태로 반환됨 (디폴트값)
    console.log(Number(num1) + Number(num2)); // 이렇게 값을 변환해줘야 숫자로 나옴 
    ```


### 3.데이터타입
- 타입이란 프로그램에서 다룰 수 있는 값의 종류를 의미함
    - 숫자형(number)
        - 다른 언어는 정수, 실수형 따로 있는데, JS는 무조건 숫자형 (모든 수를 실수 하나로만 표현함)
            ```javascript
            let num1 = 10, num2 = 11.11, num3 = 10e6; // 10e6은 10의 6승을 의미함
            console.log(num1);
            console.log(num2);
            console.log(num3);
            ```
    - 문자열형(string)
        - JS에서는 쌍따옴표("문자")나 따옴표 ('문자')에 둘러싸인 문자의 집합을 의미함
        - 문장안에 "" 혹은 ''로 넣고싶은경우 다른걸로 감싸주면된다
            ```javascript
            let str1 = "장호철 : '여러분 반가워요'";
            let str2 = '장호철 : "여러분 반가워요"';
            let str3 = "\"안녕하세요. \n자바스크립트\"";
            let str4 = `자바스크립트에서는 문자열을 쌍따옴표나 따옴표로 둘러싸인 문자의 집합을 의미합니다.`
            ```
          
            ```javascript
            let num1 = 10; // 숫자형
            let str1 = "Hello JavaScript" // 문자열형
            let num2 = 5;
            let str2 = "Hello World"
            console.log(num1 + num2);
            console.log(num1 + str1);
            console.log(str1 + str2);
            
            console.log("장호철 : '여러분, 반가워요'");
            console.log('장호철 : "여러분, 반가워요"');
            console.log("안녕하세요. \n자바스크립트"); // \백슬러쉬를 쓰면 다음줄로 넘어감
            ```
          
        - 다른 언어는 문자와 문자열을 다르게 판단하지만, JS는 스스로 판단한다
        - '+'의 의미 : 1. 산술 연산자 (덧셈) 2. 연결 연산자 (문자열 결합)
    - 불리언형(boolean)
        - 불리언 값은 true(참), false(거짓)으로 표현합니다
            ```javascript
            let b1 = true; // 1으로 봐도 됨
            let b2 = false; // 0으로 봐도 됨
            let b3 = (10 > 5); // 자연스럽게 b3에는 true가 들어감
            let b4 = (10 < 3);
            console.log('b1의 결과 :' + b1)
            console.log('b2의 결과 :' + b2)
            console.log('b3의 결과 :' + b3)
            console.log('b4의 결과 :' + b4)
            ```
    - undefined, null 형
        - null이란 object 타입이며, 아직 값이 정해지지않은 것을 의미함
        - undefined는 null과는 달리, 아직 타입이 정해지지 않은 것을 의미함
        - undefined는 초기화 되지않은 변수나 존재하지 않는 값을 접근할 때 반환됨
            ```javascript
            let num1;
            console.log(num1)
            
            let obj1 = {}; // {}를 넣으면 객체를 만들겠다는 이야기이다
            let obj2 = null;
            console.log(obj1);
            console.log(obj2);
            ```
    - 심볼형(Symbol)
        - ECMAScript6에서 추가된 데이터 타입
        - 유일하고 변경 불가능한 기본값을 만든다
        - 객체 속성의 key값으로도 사용가능
            ```javascript
            const sym1 = Symbol('a');
            const sym2 = Symbol('a');
            console.log(sym1 === sym2); // 같는지 확인할 때
            // == 값이 같은지 묻는 것 (value가 같은지 검사)
            // "10" == 10 은 true이고 , "10" === 10 은 false가 나온다
            // == 은 value만 비교하는 것이고, === 값과 타입을 동시에 비교한다
            // 심볼은 독자적인 key값을 가지는 것이다
            
            const sym3 = Symbol();
            const sym4 = sym3;
            // 이렇게 쓰면, 같아질 수 있다
            console.log(sym3 === sym4); //이건 true가 나온다
            ```
          
    - 객체형(object)
        - 우리가 인식할 수 있는 사물을 저장하는 형태
        - 객체는 여러 프로퍼티나 메소드를 같은 이름으로 묶어놓은 집합체
        - 값이 명사의 형태를 띄면 프로퍼티로 보면 된다
        - 값이 동사의 형태로 되면 메소드로 보면 된다
            ```javascript
            let dog = {name: "루시", age: 10, weight: 2.0 };
            console.log("이름 : " + dog.name);
            console.log("나이 : " + dog.age);
            console.log("몸무게 : " + dog.weight);
            ```
        