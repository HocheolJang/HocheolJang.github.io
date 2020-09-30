---
title:  "JavaScript-6(객체) "
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

### 객체 (object)

- 특징
    - 자바스크립트는 객체지향프로그래밍을 흉내내고 있지만, 다른 언어에 비해 실질적인 객체지향적인 프로그래밍은 아님.
    C ++ 이 가장 객체지향적인 프로그래밍을 알 수 있다. 그 다음은 자바정도!
    - 메모리 내에 stack에는 주소를 담고 실제값은 heep에 저장됨

    - 키(key)와 값(value)으로 구성된 프로퍼티(property)들의 집합입니다.
    프로퍼티의 값은 자바스크립트에서 사용할 수 있는 모든 값을 담을 수 있습니다.

- 배열 VS 객체
    - 배열 (카테고리끼리 묶어서 담는 집합)
        - const student = ['김사과', '반하나', '오렌지'];
    - 객체 (한사람에 대한 정보?를 담는 집합)
        - const student = {num:1, name:'김사과', kor:90, math:100, eng:60}

- 필드, 메소드를 다 모아서 프로퍼티(property)라고 부름
    ```javascript 
    const dog = {
    name: '해피',  -- 필드 
    family: '포메리안', -- 필드
    color: 'white',
    age: 4,
    play: function(){     -- 메소드
    console.log('뛰어놀아')
    }
    }
    console.log(dog.name); // 해피
    dog.play(); // 뛰어놀아
    ```

- 객체를 저장하는 방법 

    - 방법 1
        ```javascript
        const student1 = {num:1, name:'김사과', kor:90, math:100, eng:60}
        const student2 = {num:2, name:'반하나', kor:90, math:100, eng:60}  
        ```
    - 방법 2
        ```javascript
        const student = [
        {num:1, name:'김사과', kor:90, math:100, eng:60},
        {num:2, name:'반하나', kor:90, math:100, eng:60} 
        ]
        console.log(student[0]) // 김사과
        // const student[0] const student[1] 이렇게 불러오면된다.
        ```

- 프로퍼티(Property)
    - 프로퍼티는 키(이름)와 프로퍼티 값으로 구성됩니다. 키로 유일하게 값을 식별할 수 있습니다.
    프로퍼티키는 프로퍼티를 식별하기위한 식별자이며, 프로퍼티 값으로 사용할 수 있는 값은 빈 문자열을 포함하는 모든 문자열 또는 symbol값입니다.

- 객체를 생성하는 3가지 방법
    ```
    1. 리터럴
    2. 생성자 (가장 보편적)
    3. 클래스 (앞으로의 추세로 갈듯. 다른언어가 가장 많이 쓰는 방법이기때문에)
    ```
    1. 리터럴 표기법을 이용한 객체의 생성  
        - 자바스크립트에서 객체를 생성하는 가장 쉽고, 간단한 방법이다.
        ```
        const 객체이름 = {
        프러퍼티명1 : 값1,
        프러퍼티명2 : 값2,
        ...
        프러퍼티명n : function(){
        }
        }
        ```
        ```javascript 
        const dog1 = "뽀미";
        const dog2 = {
            name: "루시",
            family: "포메리안",
            color: "white",
            age: 9,
            weight: 3.5,
            play: function(){
                console.log("뛰어논다");
            }
        }

        console.log(`dog1 : ${dog1}`);
        console.log(`dog2 : ${dog2}`);
        console.dir(dog2);
        // 객체에 어떤 정보가 있는지 확인하려면 console.dir로 객체를 찍으면 안에 있는 프로퍼티 값 확인가능

        console.log(`don2.name : ${dog2.name}`);
        console.log(`don2.family : ${dog2.family}`);
        console.log(`don2.color : ${dog2.color}`);
        console.log(`don2.age : ${dog2.age}`);
        console.log(`don2.weight : ${dog2.weight}`);
        console.log(`don2.play : ${dog2.play}`);
        dog2.play();
        ```
       
    2. 생성자를 이용한 객체의 생성  
        - new 연산자를 사용하여 객체를 생성하고 초기화할 수 있음. 이 때 사용되는 메소드를 생성자라고 하며,
        이 메소드는 새롭게 생성되는 초기화하는 역할을 함. 이건 붕어빵의 틀 같은 방식으로 만들어내는 것이다. 
        생성자(붕어빵틀)을 만들어두면 객체(붕어빵)를 만들때마다 쓰면 되니까 코딩의 양이 확 줄어들 수 있다

        ```
        function 생성자이름(매개변수1, 매개변수2 ..){
        프러퍼티이름 1 = 값1;
        프러퍼티이름 2 = 값2;
        프러퍼티이름 n = function(){}
        }
        ```

        ```
        const 객체이름1 = new 생성자이름(값1, 값2 ...);
        const 객체이름2 = new 생성자이름(값1, 값2 ...);
        const 객체이름n = new
        ```
        
        ```javascript 
        function triangle(b, h){ // b = 10, h=10
            this.base = b;
            this.height = h;
            this.area = function(){
                return this.base * this.height / 2;
            }
        }
        // 프로퍼티 앞에 파라미터와 구분하기 위해 this라고 붙인다.

        const tg1 = new triangle(10, 10);
        const tg2 = new triangle(20, 5);

        // 객체를 이렇게 만들면,
        console.log(`tg1.base : ${tg1.base}`);
        console.log(`tg1.height : ${tg1.height}`);
        console.log(`tg1.area() : ${tg1.area()}`);
        console.dir(tg1);

        console.log(`tg2.base : ${tg2.base}`);
        console.log(`tg2.height : ${tg2.height}`);
        console.log(`tg2.area() : ${tg2.area()}`);
        console.dir(tg2);
        ```
       
        - 프로토타입(prototype)
            - 자바스크립트의 모든 객체는 프로토타입이라는 객체를 가지고 있습니다. 모든 객체는 그들의 프로토타입으로부터 프러퍼티와 메소드를 상속받습니다.
        이처럼 자바스크립트의 모든 객체는 최소한 하나이상의 다른 객체로부터 상속을 받으며, 이 때 상속되는 정보를 제공하는 객체를 프로토타입이라고 합니다.
        (tg1 <--- object.prototype) 템플릿 역할이라는게 객체를 만들때 객체의 틀과 같은 뜻이다. 생성자가 객체의 틀을 만들기 위해 만들어진 함수이니
        그 안에 프러퍼티 정의된 형태가 템플릿이죠 그 내용을 가지고 있는 객체가 프로토타입입니다
        
        ```javascript 
        function Dog(name, color, age){
            this.name = name;
            this.color = color;
            this.age = age;
        }
        // 프로퍼티랑 변수를 구분하기 위해 프로퍼티명 앞에다가 this.를 추가해준다. 
        const rucy = new Dog("루시", "White", 9);
        
        rucy.family = '포메리안'
        rucy.breed = function(){
            return this.color + ' ' + this.family;
        }

        // const rucy = new Dog('루시', 'white', 9);
        const bbomi = new Dog('뽀미', 'white', 4);
        
        console.log(rucy);
        console.log(rucy.name);
        console.log(rucy.color);
        console.log(rucy.age);
        console.log(rucy.family);
        console.log(rucy.breed());

        console.log(bbomi);
        console.log(bbomi.name);
        console.log(bbomi.color);
        console.log(bbomi.age);
        console.log(bbomi.family); // undefined
        console.log(bbomi.breed()); // error
        ```
       
        ```javascript 
        function Dog(name,color,age){
            this.name = name;
            this.color = color;
            this.age = age;
        }
        Dog.prototype.family = '포메리안';
        // 이렇게 하면, this.family = '포메리안'; 처럼 되게 하는거다.
        Dog.prototype.breed = function(){
            return this.color + ' ' + this.family;
        }
        const rucy = new Dog('루시', 'white', 9);
        const bbomi = new Dog('뽀미', 'white', 4);

        console.log(rucy);
        console.log(rucy.name);
        console.log(rucy.color);
        console.log(rucy.age);
        console.log(rucy.family);
        console.log(rucy.breed());

        console.log(bbomi);
        console.log(bbomi.name);
        console.log(bbomi.color);
        console.log(bbomi.age);
        console.log(bbomi.family); // 에러가 안생김 // 프로토타입을 써서 추가했기때문에 아예 프로퍼티가 추가된거임
        console.log(bbomi.breed()); // 에러가 안생김 // 프로토타입을 써서 추가했기때문에 아예 프로퍼티가 추가된거임
        ```

    3. 클래스를 이용한 객체의 생성
        - 클래스는 객체를 만들기 위한 용도로만 쓰는 함수같은 느낌!        
       ```
        const 변수명 = class {
        constructor(매개변수1, 매개변수2,){
            프러퍼티 이름 1 = 값1;
            프러퍼티 이름 2 = 값2;
        }
        메소드이름(매개변수1, 매개변수2){
        }
        }
        ```

        ```javascript
         const 객체이름 = new 변수명(값1, 값2);
         const 계좌정보 = class {
         constructor(계좌번호, 이름, 통장이름){
         this.계좌번호 = '111-11-11111',
         this.이름 = '사과',
         this.통장이름 = '저축통장',
         this.담당자 = '홍길동'
         }
        function set금액(price){
        if(price<0){
            나가버려
        }
        this.price = price;
        }
        }
        ```
        ```javascript
        let Dog = class {
            // 생성자는 객체가 생겨날 때 가장 먼저 호출하는 함수
            #family = '포메리안';
            static count = 0;

            constructor(name, color, age){
                this.name = name;
                this.color = color;
                this.age = age;
                this.weight = 3.5;
            }
            play(){
                console.log(`${this.name}가 놉니다.`);
            }
            get getWeight(){
                return this.weight;
            }
            set setWeight(weight){
                this.weight = weight;
            }
        }

        const rucy = new Dog('루시', 'white', 9);
        console.dir(rucy);
        console.log(rucy.name);
        console.log(rucy.color);
        console.log(rucy.age);
        console.log(rucy.getWeight);
        rucy.setWeight = 4.0;
        console.log(rucy.getWeight);
        console.log(rucy.family);
        rucy.play();
        rucy.name = "똥개";
        console.log(rucy.name);

        // class를 써서 만드는 방법을 아마 가장 많이 쓰게될 것이다.
        // 결국 다른 언어들이 class로 많이 하니까 JavaScript도 점차 따라가게 됨.

        ```
       
        - ECMA 6에서 생긴 문법
        - class는 모든 브라우저 다 되지만, 고급 class 기능은 크롬에서만 정상적으로 돌아가고 나머지 브라우저는 지원이 안될 때가 많다.

- 내장객체

    - Math 객체
        - Math 객체는 수학에서 자주 사용하는 상수와 함수들을 미리 구현해놓은 자바스크립트 표준 내장객체입니다
            - min() : 인수로 전달받은 값중에서 가장 작은 수를 리턴한다 인수가 전달되지 않으면 Infinity를 리턴함. 또한 비교할 수 없는 값이 포함되어있으면
        NaN을 리턴하게 됨
            - max() : 인수로 전달받은 값중에서 가장 큰 수를 리턴한다 인수가 전달되지 않으면 -Infinity를 리턴함. 또한 비교할 수 없는 값이 포함되어있으면
        NaN을 리턴하게 됨
            - round() : 인수로 전달받은 값을 소수점 첫번째 자리에서 반올림해서 그 결과를 리턴함
            - floor() : 인수로 전달받은 값과 같거나 작은 수중에서 가장 큰 정수를 리턴함
            - ceil() : 인수로 전달 받은 값과 같거나 큰 수중에서 가장 작은 정수를 리턴함
            - random() : 0보다 크거나 같고 1보다 작은 무작위 소수를 리턴함
            
        ```javascript
        console.log(Math.min());
        console.log(Math.min(1, 10, -10, 1000, 0)); // -10
        console.log(Math.min(1, 10, -10, "-1000", 0)); // 
        console.log(Math.min(1, 10, -10, "문자열", 0)); // 
        console.log(Math.max());

        console.log(Math.round(10.49)); // 10
        console.log(Math.round(10.5));  // 11
        console.log(Math.round(-10.5)); // -10
        console.log(Math.round(-10.51));    // -11

        console.log(Math.floor(10.49));    // 10
        console.log(Math.floor(10.5));     // 10
        console.log(Math.floor(-10.5));    // -11
        console.log(Math.floor(-10.51));   // -11

        console.log(Math.ceil(10.49));    // 11
        console.log(Math.ceil(10.5));     // 11
        console.log(Math.ceil(-10.5));    // -10
        console.log(Math.ceil(-10.51));   // -10

        const rm = Math.random(); // 0 ~ 0.99999999..
        console.log(rm);    // 0.12377488104318535
        ```

        - Q. 만약 1이상 10미만의 값을 추출하려면 어떻게 해야하는가?
        ```javascript
        console.log(Math.floor((Math.random()* 9) + 1)) // 1 ~ 9 사이의 값 나온다
        // random 함수 사용시 : 0 ~ 0.9999값 추출됨
        console.log(parseInt(Math.random() * 10) + 1)   // 1 ~ 10 값 나온다
        let RM = Math.random()
        console.log(Math.round(RM * 10)) // 0 ~ 10 사이의 값이 나온다.
        ```
      
        - Q. 로또 번호를 추첨한다면?
        ```javascript
        let lotto = Math.random();  // 0 ~ 0.99999
        // 1 ~ 45
        lotto = Math.floor(lotto * 45) + 1
        console.log(`로또 번호 : ${lotto}`);
        ```

    - String 객체
        - 자바스크립트에서 문자열을 손쉽게 만들 수 있는 객체입니다. 또한 문자열을 쉽게 다룰 수 있습니다.
            - length : 문자열의 길이를 저장할 수 있는 것 
            - str.indexOf('a') : 특정 문자나 문자열이 처음으로 등장하는 위치를 리턴합니다.
            - chatAt() : 특정 문자열에서 전달 받은 인덱스에 위치한 문자를 리턴합니다.
            - includes() : 특정 문자열에서 전달받은 문자열이 포함되어있는지 여부를 리턴하게 됨.
            - substring() : 전달받은 시작 인덱스부터 종료 인덱스 바로 앞까지 문자열을 추출하여 새로운 문자열을 리턴함 (다른 언어는 이것밖에 없어서 이걸로 씀)
            - substr() : 전달받은 시작인덱스부터 전달받은 개수만큼 문자열을 추출하여 새로운 문자열을 리턴함 (이걸 많이 씀)
            - split() : 구분자를 기준으로 나눈 후 나뉜 문자열을 하나의 배열에 저장합니다
            - str =  "드라이브, 등산, 음악감상, 게임"
            - arr = str.split(',')
            - arr[0] = '드라이브'
            - arr[1] = '등산'
            - replace() : 원본 문자열의 일부를 전달받은 문자열로 치환합니다
            - trim() : 문자열의 앞뒤 공백을 제거합니다
            - toUpperCase() : 영문자 중 소문자를 대문자로 변환합니다
            - toLowerCase() : 영문자 중 대문자를 소문자로 변환합니다

        ```
        const str = 'JavaScript';
        const strobj = new String('JavaScript');
        
        (str == strObj); // true, 값만 비교,
        (str === strobj); // false, 값과 형까지 비교, str은 string이고 strobj는 object이다.
        ```
      
        ```javascript
        const str1 = '안녕하세요. JavaScript';
        
        console.log(str1.length); // 10 (글자수 카운트)

        console.log(str1.indexOf('j')); // 찾지 못했기 때문에 -1 출력됨
        console.log(str1.indexOf('a')); // 여러개의 a중 처음 나오는 문자 순서출력, 8
        console.log(str1.indexOf('Java'));  // 문자열인 경우 첫번째 문자 위치를 검색 7
        
        console.log(str1.charAt(8)); // a

        console.log(str1.includes('Java')); // 대소문자 구별한다. true
        console.log(str1.includes('java')); // 대소문자 구별한다. false
        
        console.log(str1.substring(7)); // JavaScript // 매개변수가 1개일 경우 해당 위치부터 끝까지
        console.log(str1.substring(7, 11)); // Java
        console.log(str1.substr(7, 4)); // Java

        const str2 = "김사과|오렌지|반하나|이메론|박수박|오피치";
        const student = str2.split("|");
        for(let stu of student){
            console.log(stu);
        } // 한 명씩 순서대로 출력됨

        console.log(str1.replace('안녕하세요.', 'Hello!'));

        const str3 = "          JavaScript          ";
        console.log(`|${str3}|`); //           JavaScript          출력
        console.log(`|${str3.trim()}|`); // |JavaScript| 출력

        console.log(str3.toLowerCase()); // javascript
        console.log(str3.toUpperCase()); // JAVASCRIPT
        ```      

    - Date 객체
        - 날짜, 시간등을 쉽게 처리할 수 있는 내장 객체입니다. 굉장히 많이 쓰인다.
        ```javascript
        const startDate = "2020-09-20 10:17:00";
        // 2020년 9월 20일 10시 17분 처럼 표기하려면 substr등으로 값을 분리해준 후 해야한다.      
        ```      
        - 연도(year)
            - 2자리로 표기하게되면 1900년 ~ 1999년을 이야기하는 것
            - 4자리로 표기해야한다. (2000 ~ )
        - 월 (month) : 0월(일반적인 1월)부터 11월(일반적인 12월)까지 있어
        - 시 (hour) : 0 ~ 24시 표현가능
        - 분 (minute) : 0분 ~ 59분
        - 초 (seconds) : 0초 ~ 59초

    - Date 객체 만드는 방법
        ```          
        new Date() : 현재 날짜 시간을 저장한 객체가 만들어집니다.
        ex)
        const currentTime = new Date(); 
        new Date("날짜 문자열") : 해당 특정 날짜와 시간을 가리키는 객체가 만들어집니다.
    
        const thisDate = new Date("2020-09-20 10:25:00")
        ``` 
             
        ```              
        new Date("밀리초") : 1970년 1월 1일 0시 ~ 해당 밀리초만큼 지난 날짜 객체가 만들어집니다
        ex ) 타임스템프
        new Date("2000") = 1970년 1월 1일 0시 0분 2초
        예전에 많이 쓰던 방법이다
        2038년 1월 19일 3분 14초까지가 최대치이다 (PC에서 쓸 수 있는 최대치)
    
        new Date(년, 월, 일, 시, 분, 초, 밀리초) : 해당 특정날짜시간을 가리키는 객체가 만들어집니다
        ```      


