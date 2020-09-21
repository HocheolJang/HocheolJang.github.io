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
classes: wide
# other options
---

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
    // example
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
    // example
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
    // example
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


### 3.연산자(Operator)

- 산술연산자 : 사칙연산을 다루는 기본적인 연산자

    ```
    + : 덧셈   
    - : 뺄셈    
    * : 곱셈    
    / : 나눗셈    
    % : 나눈 나머지값    
    ** : 거듭제곱    
    ```
  
    ```javascript
    // example
    let num1 = Number(prompt('첫번째 숫자를 입력하세요'));
    let num2 = Number(prompt('두번째 숫자를 입력하세요'));
    let result = num1 + num2;
    console.log((`num1 + num2 = ${result}`));
    // console.log(('num1 + num2 =' + result)); // 위아래는 같은 형태로 출력되지만 위가 덜 귀찮은 형태
    result = num1 - num2;
    console.log((`num1 - num2 = ${result}`));
    result = num1 * num2;
    console.log((`num1 * num2 = ${result}`));
    result = num1 / num2;
    console.log((`num1 / num2 = ${result}`));
    result = num1 % num2;
    console.log((`num1 % num2 = ${result}`));
    result = num1 ** num2;
    console.log((`num1 ** num2 = ${result}`));
    ```

- 비교연산자 : 피연산자의 상대적인 크기를 판단하여 참/거짓으로 반환    

    ```
    > : 왼쪽의 값이 오른쪽의 값보다 크면 참을 반환합니다.
    < : 오른쪽의 값이 왼쪽의 값보다 크면 참을 반환합니다.
    >= : 왼쪽의 값이 오른쪽의 값보다 크거나 같으면 참을 반환합니다.
    <= : 오른쪽의 값이 왼쪽의 값보다 크거나 같으면 참을 반환합니다.
    == : 값이 같으면 참을 반환함
    === : 값이 같고, 타입까지 같으면 참을 반환함
    != : 타입에 관계업이 값이 다르면 참을 반환함
    !== : 두 식의 값이 같지않고 타입까지 같지않으면 참을 반환함)
    ```
    ```javascript
    // example
    let num1 = 3, num2 = 5;
    let str1 = "3", str2 = "abcde", str3 = "bcd";
    let result = (num1 > num2);
    console.log(`num1 > num2 : ${result}`);
    result = (str2 <= str3);
    console.log(`str2 <= str3 : ${result}`); // true가 나옴. 사전순으로 이해하면됨. a가 b보다 뒤에 나옴. 더 크다
    result = (num1 == str1);
    console.log(`num1 == str1 : ${result}`); // 타입이 다르지만 값이 같기때문에 true로 반환됨
    result = (num1 === str1);
    console.log(`num1 === str1 : ${result}`); // 타입이 다르지만 값이 같기때문에 true로 반환됨
    ```  
  
- 대입연산자
    - 변수에 값을 대입할 떄 사용하는 연산자

    ```
    = (왼쪽변수에 오른쪽 값을 대입할 때)
    += (왼쪽변수에 오른쪽 값을 더한 후, 그 결과를 왼쪽변수에 대입)
    ex)
    let a = 10;
    a += 1; // a = a+1;과 같은 뜻이다 // 무조건 오른쪽부터 더해라는 이야기
    -= (왼쪽변수에 오른쪽 값을 뺀 후에, 그 결과를 왼쪽 변수에 대입)
    *= (왼쪽변수에 오른쪽 값을 곱한 후에, 그 결과를 왼쪽 변수에 대입)
    /= (왼쪽변수에 오른쪽 값을 나눈 후에, 그 결과를 왼쪽 변수에 대입)
    %= (왼쪽변수에 오른쪽 값의 나머지값을 구한 후에, 그 결과를 왼쪽 변수에 대입)
    **= (왼쪽변수에 오른쪽 값의 거듭제곱 후, 그 결과를 왼쪽 변수에 대입)
    ```

    ```javascript
    // example
    let num1 = 10, num2 = 10, num3 = 10;
    num1 += 5;
    console.log(`num1 += 5 : ${num1}`);
    console.log(`num2 -= 5 : ${num2}`);
    ```        
    
    
- 증감연산자
    - 증감연산자는 값을 1씩 증가하거나, 감소시킬 때 사용하는 연산자. 연산자가 어느쪽에 위치하느냐에 따라 순서 및 결과가 달라짐
    
    ```
    ++변수 : 변수의 값을 1 증가시킨 후 다음 연산을 진행
    변수++ : 먼저 다른 연산을 수행하고나서, 변수의 값을 1증가시킵니다
    --변수 : 변수의 값을 1 감소시킨 후 다음 연산을 진행
    변수-- : 먼저 다른 연산을 수행하고나서, 변수의 값을 1감소시킵니다
    
    let a = 5;
    ++a; // a = a+1; a++;
    
    let b = 5;
    let b = ++a; // b = 6;

    let a = 5;
    let b = a++; // b = 5;
    ```

    ```javascript
    // example  
    let num1 = 10;
    console.log(`num1의 값 : ${num1}`); // 10
    console.log(`++num1의 값 : ${++num1}`); // 11
    console.log(`num1의 값 : ${num1}`); // 11
    console.log(`num1++의 값 : ${num1++}`); // 'num1++의 값 : ' + num1++ // 11
    console.log(`num1의 값 : ${num1}`); // 12
    ```        
      
- 논리연산자
    - 주어진 논리식을 판단하여 참과 거짓을 반환함
    
    ```
    A && B -- AND 연산 : 두 논리식이 모두 참이면, 참으로 반환
        ex) ID / PW 둘 다 True이면, 로그인 성공 ! True / True 일때만 True, 나머지는 전부 False 
    A || B -- OR 연산 : 두 논리식중 한 가지라도 참이면, 참으로 반환
        ex) false false 일 때만 false 로 나옴 , 나머지는 모두 True
    !A -- NOT 연산 : 논리식의 결과가 참이면 거짓으로, 거짓이면 참으로 변환하는 연산자
        ex) let b1 = true;
            console.log(!b1); 결과값은 False가 나옴
  
    A	&&	 B		결과
    true		true		true
    true		false		false
    false		true		false
    false		false		false
  
    A	||	 B		결과
    true		true		true
    true		false		true
    false		true		true
    false		false		false
  
    ```

    ```javascript
    // example  
    let num1 = 10, num2 = 5;
    let result1 = (num1 == num2); // False
    let result2 = (num1 >= num2); // True
    console.log(`result1 && result2 : ${result1 && result2}`);
    console.log(`result1 || result2 : ${result1 || result2}`);
    console.log(`!result1 : ${!result1}`);
    ```        
    
- 비트연산자
    - 잘 안쓰지만 상식적으로 알면 좋다~
    - 논리연산자와 비슷하지만 비트단위로 논리연산을 수행함

    ```
    & : 대응되는 비트가 모두 참이면 참을 반환하는 연산자
        25 & 18 = ?
        11001 (25-10진법)
        10010 (18-10진법)
        10000
        따라서 25 & 16 = 16(10진법)

    | : 대응되는 비트중 하나라도 참을 반환하는 연산자
    ^ : 대응하는 비트가 서로 다르면 참을 반환하는 연산자
    << : 지정한 수만큼 비트를 왼쪽으로 이동시킴
    >> : 지정한 수만큼 비트를 오른쪽으로 이동시킴
    ```    

    ```    
    - bit은 컴퓨터 용량의 최소단위, 0 또는 1을 저장하는 단위
    - 1byte = 8bit
    - KB(킬로바이트) : 1KB = 1024byte
    - MB(메가바이트) : 1MB = 1024KB
    - GB(기가바이트) : 1GB = 1024MB
    - TB(테라바이트) : 1TB = 1024GB
    - PB(페타바이트) : 1PB = 1024TB
    - 헥사 / 제타 / 로타

    - 이진법 연산까진 아는게 좋다
        32  16  8   4   2   1
        1   1   0   0   1   0 (50)
            1   1   0   0   1 (25)
            1   0   0   1   0 (18)
                    1   0   1 (5)   
    - 25(10진법) = 11001(2진법)
    - 18(10진법) = 10010(2진법)           
    ```
  
    ```javascript
    // example  
    let num1 = 25, num2 = 18;
    console.log(`num1 & num2 : ${num1 & num2}`)
    console.log(`num1 | num2 : ${num1 | num2}`)
    // 둘 중 하나라도 참이면 참
    //  25 = 11001
    //  18 = 10010
    //  ?? = 11011 = 27
    console.log(`num1 ^ num2 : ${num1 ^ num2}`)
    // 값이 서로 다르면 참(1)
    //  25 = 11001
    //  18 = 10010
    //  ?? = 01011 = 11 
    console.log(`num1 << num2 : ${num1 << 2}`)
    //  25 = 11001인데, 2칸을 왼쪽으로 옮기면
    //  1100100 (값 100)
    console.log(`num1 >> num2 : ${num1 >> 2}`)
    //  25 = 11001인데, 2칸을 오른쪽으로 옮기면
    //  110이 됨 (값 6)
    ```        

- 삼항연산자 (많이 씀)
    - 조건식에 따른 참, 거짓에 따라 반환값이 달라지는 연산자      
    ex) 변수 = 조건식? 반환값1(True일 경우) : 반환값2(False일 경우)

    ```javascript
    // example  
    let num1 = Number(prompt('첫번째 숫자를 입력하세요'));
    let num2 = Number(prompt('두번째 숫자를 입력하세요'));
    let result = (num1 > num2) ? num1 : num2;
    console.log(`두 수중 큰 수는 ? ${result}`);
    ```        