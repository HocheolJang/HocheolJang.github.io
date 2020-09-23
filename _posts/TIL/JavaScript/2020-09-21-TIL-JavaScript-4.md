---
title:  "TIL_JavaScript-4(제어문 - 조건문, 반복문) "
excerpt: "자바스크립트(입문용) 정리합니다"

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

---

### 제어문

- 프로그램의 순차적인 흐름을 제어할 때 사용하는 실행문

#### 조건문
  - 프로그램 내에서 주어진 조건문의 결과에 따라 별도의 명령을 수행하도록 제어하는 실행문입니다.
    - if 문
        - 범위에 대한 조건을 줄 때 유리합니다.
	    - 조건식의 결과가 참(true)이면 주어진 실행문을 실행하고, 거짓(false)이면 아무것도 실행하지 않는 문장입니다.
        - {}(중괄호)의 역할은 조건식의 결과가 참(true)인 경우 여러줄의 실행문을 실행하기 위해 사용합니다.
            ```
            if(조건식) {
                조건식의 결과가 참일 때 실행할 문장;
                ...
              }
            ```
          
            ```javascript
            // example
            'use strict';
            const age = Number(prompt('나이를 입력하세요.'));
            if(age >= 19) 
                console.log('성인입니다.'); // if문 영향
                console.log('프로그램을 종료합니다.');  // if 영향 X
            ```
        
    - if ~ else 문
        - if문과 같이 사용할 수 있는 else문은 if문의 조건식의 결과가 거짓(false)일 때 실행문을 실행합니다.
            ```
            if(조건식) {
                조건식의 결과가 참일 때 실행할 문장;
            }else{
                조건식의 결과가 거짓일 때 실행할 문장;
            }
            ```
           
            ```javascript
            // example
            'use strict';
            const age = Number(prompt('나이를 입력하세요.'));
            if(age >= 19){
                console.log('성인입니다.');
            }else{
                console.log('미성년입니다.');
            }
            ```

    - if ~ else if ~ else 문
        - else if문은 if문처럼 조건식을 설정할 수 있으므로 중첩된 if문을 좀 더 간결하게 표현할 수 있다.
        - 하나의 조건문 안에서 if문과 else문은 단 한번만 사용할 수 있습니다.
        - 하지만 else if문은 여러번 사용하여 다양한 조건을 설정할 수 있습니다. (단, else문은 생략 가능)
        
            ```
            if(조건식1) {
                조건식1의 결과가 참일 때 실행할 문장;
            }else if(조건식2){
                조건식2의 결과가 참일 때 실행할 문장;
            }else if(조건식3){
                조건식3의 결과가 참일 때 실행할 문장;
            }
            ...
            else{
                모든 조건식의 결과가 거짓일 때 실행할 문장;
            }
            ```
            
            ```javascript
            // example
            'use strict';
            const age = Number(prompt('나이를 입력하세요.'));
            if(age >= 19){
                console.log('성인입니다.');
            }else if(age >= 14){
                console.log('청소년입니다.');
            }else if(age >= 7){
                console.log('어린이입니다.');
            }else{
                console.log('유아입니다.');
            }
            ```
	    
	- switch 문
	    - 특정 값과 일치하는 것을 찾을 때 유리합니다.
	    - switch문은 if ~ else문과 마찬가지로 주어진 조건 값에 따라 프로그램이 다른 명령을 수행하도록 하는 조건문입니다.
	    - switch문은 if ~ else문 보다 가독성 및 속도 측면에서 더 유리합니다.
        
            ```
            switch(비교값){
            case 값1:
            비교값이 값1과 일치할 경우 실행할 문장;
            break;
            case 값2:
            비교값이 값2와 일치할 경우 실행할 문장;
            break;
            ...
            default:
            비교값이 모두 일치하지 않을 경우 실행할 문장;
            }
            ```
            
            ```javascript
            // example
            'use strict';
            let input = prompt('아동, 청소년, 성인 중 선택하세요.');    // 청소년
            switch(input){
                case "아동":
                    input += " : 입장료 무료";
                    // input = input + " : 입장료 무료"; -> "아동 : 입장료 무료"
                    break;
                case "청소년":
                    input += " : 입장료 2000원";
                    // "청소년 : 입장료 2000원"
                    break;
                case "성인":
                    input += " : 입장료 5000원";
                    break;            
                default:
                    alert('입력 값을 확인하세요.');
                    input = '입력 값을 확인하세요.';
            }
            console.log(input);
            ```
	    
#### 반복문
  - 프로그램 내에서 같은 명령을 일정 횟수만큼 반복하여 수행하도록 제어하는 실행문입니다.
    - while 문
	    - 특정 조건식을 만족하는 동안 계속해서 주어진 실행문을 반복합니다.            
            ```
            while(조건식){
            조건식의 결과가 참인 동안 반복될 실행문;
            }
            ```
            
            ```javascript
            // example
            'use strict';
            let i = 1;
            while(i<=5){
            console.log('안녕하세요. JavaScript!');
            document.write('안녕하세요. JavaScript!<br>');
            i++;
            }
            ```
        
            ```javascript        
            let i = 1, sum = 0;
            while(i<=10){
            sum += i;
            /*
                sum = sum + i;
                1번째 : sum = 0 + 1; -> sum = 1;
                2번째 : sum = 1 + 2; -> sum = 3;
                3번째 : sum = 3 + 3; -> sum = 6;
                4번째 : sum = 6 + 4; -> sum = 10;
                5번째 : sum = 10 + 5; -> sum = 15;
                6번째 : sum = 15 + 6; -> sum = 21;
                7번째 : sum = 21 + 7; -> sum = 28;
                8번째 : sum = 28 + 8; -> sum = 36;
                9번째 : sum = 36 + 9; -> sum = 45;
                10번째 : sum = 45 + 10; -> sum = 55;
            */
            i++;
            }
             console.log(`1부터 10까지의 총합 : ${sum}`);
            ```        
        
            ```javascript        
            let i = 1;
            let sum = 0;
            while(i <= 100){
            if(i % 2 == 0) sum += i;
            i++;
            }
            console.log(`1 ~ 100까지의 짝수의 합 : ${sum}`);
	        ```
        
    - do ~ while문
        - while문은 루트에 진입하기 전에 먼저 조건식부터 검사를 합니다.
        - 하지만 do ~ while문은 먼저 루프를 한 번 실행한 후에 조건식을 검사합니다.
            ```
            do {
                조건식의 결과가 참인 동안 반복될 실행문;
            }while(조건식);
            ```
            ```javascript
            // example
            'use strict';
            let i = 1, j = 1;
            while(i > 3) {
                console.log(`i : ${i++}`);
            }
            do {
                console.log(`j : ${j++}`);
            }while(j > 3);
            ```
        - for 문
            - for문은 while문과 달리 자체적으로 초기값, 조건식, 증감식을 모두 포함하고 있는 반복문입니다.
            - while문 보다는 간결하게 반복을 표현할 수 있습니다.
            
            ```
            for(초기값; 조건식; 증감식){
                조건식의 결과가 참인 동안 반복할 실행문;
            }
            ```
    
            ```javascript
            // example
            'use strict';
            for(let i=1; i<=10; i++){
                console.log('안녕하세요. JavaScript');
            }
            ```
        
            ```javascript        
            'use strict';
            let i;
            for(i=1; i<=5; i++){
                console.log(`${i}번째 반복`);
            }
            console.log(`현재 i의 값은 : ${i}`);
        
          
            ```javascript        
            'use strict';
            let sum = 0;
            for(let i=1; i<=10; i++){
                sum += i;
            }
            console.log(`1 ~ 10까지의 총합 : ${sum}`);
            ```
        
        - continue 문
            - 반복중인 루트 내에서 사용하여 해당 루프의 나머지 부분을 건너뛰고, 다음 조건식의 판단으로 넘어가게 합니다.
            - 보통 반복문 내에서 특정 조건에 대한 처리를 제외하고자 할 때 사용합니다.
            
            ```javascript
            // example
            let num = 3;
            for(let i=1; i<=100; i++){
            if(i % num == 0){
                document.write('짝! ');
                continue;
            }
            document.write(`${i} `);
            }
            ```
        - break 문
            - 반복중인 루프 내에서 사용하여 해당 반복문을 완전히 종료시키고 반복문 바로 다음에 위치한 실행문으로 프로그램의 흐름을 이동시킵니다.
            - 루프 내에서 조건식의 판단 결과에 상관없이 반복문을 빠져나가고 싶을 때 사용합니다.
            
            ```javascript
            // example
            'use strict';
            while(true){
            let sel = Number(prompt('원하는 메뉴를 선택하세요. 1. 회원등록 2. 회원목록 3. 회원수정 4. 종료'));
            if(sel == 1) alert('회원등록이 필요합니다');
            if(sel == 2) alert('회원목록 페이지로 이동합니다');
            if(sel == 3) alert('회원수정 페이지로 이동합니다');
            if(sel == 4) {
                alert('프로그램을 종료합니다');
                break;         // 무한방문할 수 있도록 하다가 4번을 누르면 break가 걸려서 종료하게 만들 수 있다
              }
            }
            ```
        
            ```javascript
            'use strict'; 
            // for문에 ;;라고 쓰면 무한루프가 돈다
            for(;;){
            let sel = Number(prompt('원하는 메뉴를 선택하세요. 1. 회원등록 2. 회원목록 3. 회원수정 4. 종료'));
            if(sel == 1) alert('회원등록이 필요합니다');
            if(sel == 2) alert('회원목록 페이지로 이동합니다');
            if(sel == 3) alert('회원수정 페이지로 이동합니다');
            if(sel == 4) {
                alert('프로그램을 종료합니다');
                break;         // 무한방문할 수 있도록 하다가 4번을 누르면 break가 걸려서 종료하게 만들 수 있다
              }
            }
            ```
        - 중첩 for 문
            - for문이 2개이상 겹쳐있는 프로그램을 의미함
            
            ```
            for(초기값; 조건식1; 증감식) {
            조건식 1의 결과가 참인동안 반복할 실행문
            for(초기값, 조건식2; 증감식){
            조건식2의 결과가 참인 동안 반복될 실행문;
                }
            }
            ```
          
            ```javascript
            for(let i=1; i<=3; i++){
            for(let j=1; j<=5; j++){
                console.log('안녕하세요 자바스크립트')
               }
            }
            // Q. 몇 번 돌까요? 15번 돈다
            ```
          
            ```javascript
            
            // 구구단
        
            for(let i=2; i<=9; i++){
               document.write(`<p> ${i}단<p>`);
               for(let j=1; j<=9; j++){
                  document.write(`${i} * ${j} = ${i * j}<br>`)
                  }
            }
            ```

        - for ~ in 반복문
            - 객체의 속성들을 반복하여 작업을 수행할 수 있습니다.
            - for in 구문은 객체의 key 값에 접근할 수 있지만, value 값에 접근하는 방법은 제공하지 않습니다.
            - 객체의 key값과 value 값을 뽑아내는데 유용합니다.
            - 객체의 키값의 갯수만큼 반복하여 첫번쨰키값부터 마지막 키값까지 반복합니다.
            
            ```
            for(변수선언, in 배열){
                배열의 요소만큼 반복할 실행문;
            }
            for (let i in arr){
                console.log(arr[i]);
            }
            ```

            ```javascript
            
            // example
            var obj = {name:"홍길동", class:"A반", age:20};
            for (var i in obj){
              document.write(i + " : " + obj[i] + "<br>");
            }
             /* 결과 :
             name : 홍길동
             class : A반
             age : 20
             */
            ```

        - foreach 반복문
            - foreach 반복문은 오직 Array 객체에서만 사용가능한 메서드입니다.
            - 배열의 요소들을 반복하여 작업을 수행할수 있습니다. 
            - foreach구문의 인자로 callback함수를 등록할수 있고, 배열의 각 요소들이 반복될 떄 이 callback 함수가 호출됩니다.
            - callback 함수에서 배열요소의 인덱스와 값에 접근할수 있습니다.

            ```
            배열이름.foreach(function(변수){
                배열의 요소만큼 반복할 실행문;
            })
            ```
          
            ```javascript
            // example
            test = [1, 2, 3];
            test.forEach(function(item, index) {
              console.log(index);
            });
             /*
             결과 :
             0
             1
             2
             */
            ```

            ```javascript
            var arr = ['가', '나', '다', '라']
            arr.foreach(function(item,index,arr2){
              console.log(item, index, arr2[index+1]);
              })
              /*
              결과 :
              가 0 나
              나 1 다
              다 2 라
              라 3 undefined
              */
            ```