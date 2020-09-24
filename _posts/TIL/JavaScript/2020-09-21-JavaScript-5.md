---
title:  "JavaScript-5(배열, 사용자정의함수) "
excerpt: "자바스크립트(입문용) 정리합니다"

categories:
  - JavaScript
tags:
  - JavaScript
comments: true
toc: true
toc_sticky: true
classes: wide

---

### 배열 (array)
  - 자바스크립트에서 배열은 이름과 인덱스로 참조되는 정렬된 값의 집합.
  - 배열을 구성하는 각각의 값을 배열요소라고 하며, 배열에서의 위치를 가리키는 숫자를 인덱스라고 합니다.
  - 배열을 만드는 방법
  
    ```    
    let 배열이름; // 배열의 선언
    배열이름 = [요소1, 요소2, 요소3, 요소4...] ; // 배열의 초기화
    ```    
    
    ```javascript    
    let arr;
    arr = [100, 150, 250, 250];
    //or
    let arr = [100, 150, 200, 250];
    console.log(arr[2]); // 200
    ```
    
    ```javascript
    let arr = ['장사과', 20, 150.34, true]
    
    console.log(arr[0]) // 장사과
    console.log(arr[2]) // 150.34
    for (i = 0; i < arr.length; i++){
        console.log(arr[i])
    } // i 에 인덱스가 들어가며 모든 값 추출

    for(let i of arr){
        console.log(i);
    } // i 는 값(value)가 들어가는 것. 왜...? 이유를 더 찾아볼게요..

    arr.forEach(function(i){
        console.log(i);
    }) // i값은 value 왜...? 이유를 더 찾아볼게요..
    ```
    
    ```javascript    
    /*
    let 배열이름 = Array(요소1, 요소2, 요소3);
    or
    let 배열이름 = new Arrya(요소1, 요소2, 요소3);
    */
    let arr = new Array(100, 150, 200, 250);
    ```        

  - 자바스크립트 배열의 특징
    1. 배열 요소의 타입이 고정되어있지 않으므로, 같은 배열에 있는 배열 요소의 타입이 다를 수 있습니다.
        ```javascript    
        let arr = [1, 2, true, '김사과', 100.5];
        ```
        
    2. 배열 요소의 인덱스가 연속적이지 않아도 되며, 특정 배열의 요소가 비어있을 수도 있음
        ```javascript    
        let arr1;
        arr[0] = 1;
        arr[1] = 2;
        arr[5] = '김사과';
        ```

    3. 자바스크립트의 배열은 Array 객체로 다뤄집니다.
    - push() : 배열의 요소를 추가합니다
    - pop() : 배열의 마지막 주소에 있는 값을 제거합니다
    - shift() : 배열의 첫번째 주소에 있는 값을 제거합니다
    - concat() : 두 개의 배열을 합쳐주는 함수입니다
    - join() : 배열 요소에 사이에 있는 문자를 삽입합니다
    - reverse() : 배열을 역순으로 재배치합니다
    - sort() : 배열을 오름차순으로 정렬합니다.
    
    ```javascript    
    let arr1 = ['김사과', 20, 160.5, true];
    console.log(arr1); // ['김사과', 20, 160.5, true];
    
    arr1.push('여자');
    console.log(arr1); // ['김사과', 20, 160.5, true, "여자"]
    
    arr1.pop();
    console.log(arr1); // ['김사과', 20, 160.5, true]
    
    arr1.shift();
    console.log(arr1); // [20, 160.5, true]

    let arr2 = ['학생', '서울'];
    arr1 = arr1.concat(arr2);
    console.log(arr1) // [20, 160.5, true, "여자", "학생", "서울"]

    arr2 = arr2.join("|");
    console.log(arr2); // [학생|서울]
    arr1.reverse();
    console.log(arr1) // ["서울", "학생", "여자", true, 160.5, 20]

    let arr3 = ['c','b','a','z','o'];
    arr3. sort(); // 내림차순으로 정렬됨, 오름차순은 기존함수 없음
    console.log(arr3) // ["a", "b", "c", "o", "z"]
    ```

### 사용자정의함수(function)

1. 함수선언식

    ```    
    함수이름(); // 함수 실행전에 호출해도 실행가능
    
    function 함수이름 (){
        함수가 호출되었을 때 실행할 문장;
    }
    함수이름(); // 함수 실행전에 호출해도 실행가능
    ```

2. 함수 표현식

    ```    
    상수();	// 함수 선언전에 호출 불가능

    const 상수 = function(){	// 익명함수
	    실행문;
    }
    상수();	// 함수 선언후에 사용 가능
    ```    

3. 매개변수를 입력하여 호출하는 함수
   - 디폴트 매개변수 : 함수를 호출할 때 명시된 인수를 전달하지 않았을 경우에 사용하게 될 기본값
   - 나머지 매개변수 : 생략 접두사(...)를 사용하여 특정 위치의 인수부터 마지막 인수까지를 한 번에 지정할 수 있다
    ```    
    function 함수이름(매개변수1, 매개변수2 ..){
        함수가 호출되었을 때 실행할 문장;
    }
    함수이름(값1, 값2, ...); // 호출
   
    const 상수 = function(매개변수1, 매개변수2 ..){
	    실행문;
    }
    상수(값1, 값2 ...);
    ```

    - 디폴트 매개변수

    ```    
    function 함수이름 (매개변수 1 = 값1, 매개변수 2= 값2..){
    함수가 호출되었을 때 실행할 문장;
    }
    함수이름(); // 값1, 값2가 기본값으로 설정
    ```

    ```javascript   
    //example
    const cal = function(num1=1, num2=1){   // 디폴트 매개변수
    console.log(`${num1} + ${num2} = ${num1 + num2}`);
    console.log(`${num1} - ${num2} = ${num1 - num2}`);
    console.log(`${num1} * ${num2} = ${num1 * num2}`);
    console.log(`${num1} / ${num2} = ${num1 / num2}`);
    ```

    - 나머지 매개변수
   
    ```    
    function 함수이름(매개변수1, ...매개변수2){
    함수가 호출되었을 때 실행할 문장;)
    }
    ```
    
    ```javascript   
    //example
    function func3(x1, x2, ...x3){
    console.log(`x1의 값 : ${x1}`);
    console.log(`x2의 값 : ${x2}`);
    console.log(`x3의 값 : ${x3}`);
    }
    ```
        
4. 리턴값이 있는 함수
    ```    
    function 함수이름(매개변수1, 매개변수2 ..){
	    실행문;
	    return 값;
    }
    let 변수 = 함수이름(값1, 값2..);	// return 값이 변수에 저장
    ```
       
    ```javascript
    //example
    function func4(start, end){
    let sum = 0;
    for(let i=start; i<=end; i++){
        sum += i;
    }
    return sum ;
    ```

5. 함수 표현식에서 이름이 있는 함수
    ```    
    const 상수 = function 함수이름(매개변수1, 매개변수2 ..){
	    실행문;
	    ..
	    함수이름();
	    return 값;
    }

    함수이름(값1, 값2..); (X)
    상수(값1, 값2..); (O)
    ```    

6. 함수를 만들고 직접 호출하는 함수
    ```        
    (function(){
	    실행문;
	    ..
    })();
    ```    

7. 화살표 함수
    - ECMA6에 추가된 문법. function 키워드를 사용하여 함수를 만들 것보다 간단하게 표현한다. 화살표 함수는 항상 익명이다.

    ```    
    ex. 일반 함수
    const Hello1 = function() { console.log('안녕하세요. JavaScript') }
    Hello1();

    ex. 화살표 함수
    const Hello1 = () => console.log('안녕하세요. JavaScript');
    Hello1();
    ```    
    ```javascript
    
    ```
   
    매개변수가 있는 경우
    ```javascript
    const Hello1 = x => console.log(x);
    func2(10);
    
    const Hello1 = (x, y) => x + y;
    const result = Hello1(10, 3); // 13

    const Hello1 = (x, y) => {
        let sum = 0;
        for(let i = x; i <= y; i++){
            sum += i;
        }
        return sum;
    }
    const result = Hello1(1, 10); // 55
    ```    
   
- {} 를 사용하면 return 키워드를 반드시 작성해야한다.
    ```javascript
    const func5 = (x, y) => x + y;
    const result = func5(10, 3);	// 13
    const func6 = (x, y) => { x + y };
    const result = func6(10, 3);	// undefind
    ```    

- TIP. "호이스팅"
    - 자바스크립트 엔진이 script 태그를 만나면 자바스크립트 파일을 먼저 읽고 선언된 함수를 메모리에 저장합니다.
    이 과정이 끝나면 코드가 위에서 부터 차례대로 실행되며 '함수 선언식'으로 만들어진 함수의 경우 메모리에 저장되어 있기 때문에 문제없이 실행되지만,
    '함수 표현식'으로 만든 함수는 아직 값이 할당되기 전이기 때문에 에러가 발생합니다. 함수 선언식으로 선언된 함수는 '호이스팅' 된다고 표현합니다.


