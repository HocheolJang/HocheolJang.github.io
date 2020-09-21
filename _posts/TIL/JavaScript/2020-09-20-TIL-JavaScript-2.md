---
title:  "TIL_JavaScript-2(변수, 상수, 데이터타입)"
excerpt: "자바스크립트(입문) 정리합니다"

categories:
  - TIL
  - JavaScript
tags:
  - TIL
  - JavaScript
comments: true
# other options
---


<h3>목차</h3>

- [1.변수](#1변수)
- [2.상수](#2상수)
- [3.데이터타입](#3데이터타입)
  

### 1.변수

- 변수는 데이터를 저장할 수 있는 메모리 공간. 값은 변경될 수 있다.
- let을 사용하여 변수를 선언하고, 선언하지않은 변수를 사용하려고 하면 오류가 발생함
- Ram memory에 저장함.
- let 변수명; (변수의 선언! 메모리에 방을 만들어줘!)
- 변수명 = 값; (변수의 초기화, 방의 크기를 만들어줘!)
- 변수명은 특수문자, 숫자로 시작하기보다는 정확한 명사형으로 써주는게 좋다 (num, price, name, age)
- 실제 JS에서 쓰는 단어와 겹쳐서 쓰면 에러날 수 있다. number라고 쓰면 원래 있던 것과 겹치게된다. num이라고 쓰거나 뒤에 숫자를 붙여라.
- 변수를 만들 때 쓰던 키워드 var는 더이상 쓰지않음. 옛날에 쓰던 방법이고 let은 최근에 도입되면서 쓰는 방법
- '='의 의미는 '같다'가 아니라 '할당했다'는 의미
- var은 선언을 안했는데도 쓸 수있게 되고, 밑에서 또 쓰는 일이 생길 수 있다.
- let을 쓰면 문법을 체크해주는 로직이 들어감. 그래서 에러가 발생하는 일을 줄일 수 있게 해준다
- 변수를 선언하지않아도 값이 나오긴한다. 그러나 문제가 될 소지가 많다
- use strict 은 strict mode 를 사용한다는 의미이며, 코드를 엄격한 모드로 사용하게 합니다
- java script의 `<script>` 밑에 "use strict"; 라고 써준다

    ```javascript
    let num;
    num = 10;  // let num = 10; 변수의 선언과 초기화를 동시에 진행가능
    console.log(num);
    ```

### 2.상수

- const 상수명; 라고 선언함
- 한 번 선언된 상수는 다시 재정의, 재할당 할 수 없음
- 절대 불변의 값일 때만 쓴다
- 이왕이면 상수를 쓰기를 권유함 (JS에서는 생각보다 중간에 값을 바꿀 경우 잘 없음)
- 가장 좋은건 메뉴얼 보고 공부하는게 좋다 (w3schools도 좋지만, mdn이 더 좋다)


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
        