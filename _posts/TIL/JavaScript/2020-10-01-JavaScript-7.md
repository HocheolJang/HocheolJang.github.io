---
title:  "JavaScript-7(객체-2) "
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



</a>





- 브라우저 객체 모델(Browser Object Model)
    - 웹 브라우저에 구현된 JavaScript 객체 모델을 의미하며 window 객체의 프로퍼티로 조회할 수 있다.
    - Window객체 밑에 있다. (최상위 객체이기때문에 window라는 말을 써도되고 안써도 된다.)
    - 현재 웹 브라우저의 창이나 탭을 표현하기 위한 객체들이며, 웹 브라우저는 window 객체를 이용하여 브라우저 창을 표현할 수 있다.

    - 윈도우 객체를 다 보고싶다면 아래의 이 코드를 쓰면 콘솔창에서 볼 수 있다.
    ```javascript
        for(let win in window){
            console.log(`${win} : ${window[win]}`);
        }
    ```

    (화면의 일부만 가져왔습니다)
    <a href="https://ibb.co/fqqT9x9"><img src="https://i.ibb.co/n66KBLB/2020-10-01-11-13-29.png" alt="2020-10-01-11-13-29" border="0"></a>
    
    ```javascript
    setTimeout() // 일정 시간이 지난 후 매개변수로 제공된 함수를 실행합니다.
    // ex)
    setTimeout(프러터피명(함수표현식), 시간) // 해당시간이 지난 뒤 매개변수로 지정된 함수표현식이 구현된다
      const abc = function(){
        실행문
    }
    cosnt st = setTimeout(abc, 시간) // 시간 단위는 밀리초
    ```

    ```javascript
    const st = window.setTimeout(Hi, 2000); // 초

    function Hi(){
        alert("안녕하세요. JavaScript");
    }
    ```
  
    ```javascript  
    setInterval() // 일정 시간마다 매개변수로 제공된 함수를 실행합니다
    setInterval(변수, 시간);
        const it = setInterval(함수명, 시간)
    // 무한루프이다. 시간마다 계속 반복해야하니까. 그래서 멈출 수 있는 clearTimeout()이 필요하다
    ```
  
    ```javascript  
    clearTimeout() // 일정 시간 후 setTimeout()에서 실행된 함수를 중지합니다.
    ex)
      clearTimeout(st); 예시 st = setTimeout 객체명

    clearInterval() // 일정 시간마다 setInterval()에서 실행된 함수를 중지합니다.
    ex)
      clearInterval(it); 예시 it = setInterval 객체명
    ```

    ```javascript
        const si = setInterval(Hi, 2000);

        function Hi(){
            console.log('안녕하세요. JavaScript');
        }

        function clearInterv(){
            console.log('Hi() 중지되었습니다.');
            clearInterval(si);
        }
    
    <button onclick="clearInterv()">중지</button> // 클릭시 인터벌 중지.
    ```

- location 객체
    - 현재 브라우저의 표시된 HTML 문서의 주소를 얻거나, 브라우저에 새 문서를 불러올 때 사용합니다. 
    요새는 잘 안쓴다. 다른 모듈중에 좋은게 많이 나옴.
    DOM도 예전에는 많이 썼지만, 요새는 잘안쓰게된다. 어떤 브라우저에서는 안될 수도 있다
    브라우저객체이기때문에 브라우저마다 특색이 있을 수 있다 
        - href : 페이지의 url 전체 정보를 반환합니다. 또한 url을 지정하여 페이지를 이동할 수 있다
        - protocol : 콜론을 포함하는 http, https, ftp등 프로토콜 정보를 반환합니다
        - hostname : 호스트의 이름과 포트번호를 반환합니다.
        - pathname : URL 경로부분의 정보를 반환합니다.

        ```
        ex)
        https://blog.naver.com/success415
        -----
        protocol
               ---------------
               hostname
                              -------------
                              pathname
        ```
    위의 내용은 '유저가 어떤 페이지를 보고있는가?' '어떤 루트로 들어왔는가?' 확인할 때 이걸 많이 쓴다.

    ```javascript
        console.log(`현재 문서의 URL 주소는 : ${location.href} 입니다.`);
        console.log(`현재 문서의 protocol은 : ${location.protocol} 입니다.`);
        console.log(`현재 문서의 hostname은 : ${location.hostname} 입니다.`);
        console.log(`현재 문서의 pathname은 : ${location.pathname} 입니다.`);
    ```
  
    ```javascript
    <form name="myform">
        <p><label>네이버 <input type="radio" value="naver" name="site" checked></label></p>
        <p><label>다음 <input type="radio" value="daum" name="site"></label></p>
        <p><label>구글 <input type="radio" value="google" name="site"></label></p>
        <p><label>setInterval함수 예제<input type="radio" value="page" name="site"></label></p>
        <p><input type="button" value="이동" onclick="sendit()"></p>
    </form>
    <script>
        'use strict';
        function sendit(){
            const frm = document.myform;
            if(frm.site.value == 'naver'){
                location.href = 'https://www.naver.com';
            }else if(frm.site.value == 'daum'){
                location.href = 'https://www.daum.net';
            }else if(frm.site.value == 'google'){
                location.href = 'http://www.google.net';
            }else{
                location.href = '5_setInterval함수.html';
            }
        }
    ```
  
- history 객체
    - 브라우저의 history 정보를 문서와 문서 상태 목록으로 저장하는 객체입니다
    back button / forward button 등에 많이 쓰임. 자바스크립트는 사용자의 개인 정보를 보호하기위해 이 객체의 접근하는 방법을 일부 제한하고 있음
    
        - back() : 브라우저에서 뒤로 버튼을 누른 효과를 냅니다
        - go() : 매개변수로 전달된 숫자만큼 히스토리에 적용된 페이지로 이동합니다 (0또는 음수)
        - goForward() : 브라우저에서 앞으로 버튼을 누른 효과를 냅니다

    ```javascript
    <button onclick="goBack()">뒤로</button>
    <button onclick="go()">뒤로 2페이지 이동</button>
    <button onclick="goForward()">앞으로</button>
    <button onclick="goReload()">새로고침</button>
    
    'use strict';
    function goBack(){
        history.back();
    }
    function go(){
        history.back(-2);
    }
    function goForward(){
        history.forward();
    }
    function goReload(){
        // location.reload();
        history.go(0);
    }
    ```

- screen 객체
    - 장치의 디스플레이 정보를 담고있는 객체
    사용자의 해상도를 가져와서 뿌려줬는데 최근에는 __사용안함__
    최근에 반응형은 폰이냐 테블릿이나 노트북이냐에 따라 다르게 뿌려줌

- navigator 객체
    - 브라우저 공급자 및 버전 정보등을 포함한 브라우저에 대한 정보를 저장하는 객체입니다.
    예전에는 사용 많이 했는데, 지금은 사용 잘 안함.
    자바스크립트가 표준이 되기 전에 Dom 객체 가지각색으로 만들었었다
    그래서 예전에는 브라우저 정보에 맞게 정보를 뿌려줬다.
    그러나 현재는 표준화가 되어서 이제 navigator 객체로 사용자 정보가 굳이 필요없어짐.
    대신 geolocation 객체가 추가됨 : 지리위치 API (사용자의 위치정보를 확인할 수 있음)

    ```javascript
    navigator.geolocation.getCurrentPosition(success, fail);

    function success(location){
        console.log(location.coords.latitude);
        console.log(location.coords.longitude);
    }

    function fail(msg){
        console.log(msg.code);
    }
    ```
  
- 문서 객체 모델(Document Object Model)
    - XML이나 HTML문서에 접근하기 위한 일종의 인터페이스입니다.
    이 객체 모델은 문서내의 모든 요소를 정의하고, 각각의 요소에 접근하는 방법을 제공합니다.

    ```html
    // ex)
    <html lang="en">
    <head>
        <title>간단한 HTML 문서</title>
    </head>
    <body>
        <h2>HTML 문서</h2>
        <img src="apple.png">
    </body>
    </html>
    ```

    ```
        document 객체 (최상위 객체)
                  |     
                <html> lang (제일 처음으로 만나는 태그, 랭귀지는 자식은 아니고, 그냥 html을 꾸며주는 것)
           -------|--------------------------------
          |                                       |
        <head>	                        		<body> (html의 자식태그, 둘의 사이는 형제 태그)
    
        <title> (head 태그의 자식)		 <h2> (text로 자식이 있음) <img> - src
    
    ```

    ```html
    <body>
    <h2 name="model">문서 객체 모델 - 1</h2>
    <ul>
        <li name="model">HTML</li>
        <li>CSS</li>
        <li id="js" class="js">JavaScript</li>
        <li id="js" class="js">jQuery</li>
        <li class="server">Apache</li>
        <li class="server">PHP</li>
        <li class="server">MySQL</li>
        <li id="js" class="js">Node.js</li>
        <li id="js" class="js">React</li>
    </ul>
    <script>
        'use strict';
        const tagName = document.getElementsByTagName("li");
        for(let i=0; i<tagName.length; i++){
            tagName.item(i).style.color = "gold";
        }

        const className = document.getElementsByClassName("js");
        for(let i=0; i<className.length; i++){
            className.item(i).style.color = "deepskyblue";
        }

        const id = document.getElementById("js"); 
        id.style.color = "deeppink"; // 배열이 아니라서 for문을 돌릴 수 없음, id중 첫번째 것만 색이 변함

        const name = document.getElementsByName("model");
        for(let i=0; i<name.length; i++){
            name.item(i).style.color = "red";
        }

        const querySelector = document.querySelectorAll("li.server"); // 
        for(let i=0; i<querySelector.length; i++){
            querySelector.item(i).style.color = "blue";
        }
    </script>
    </body>
    ```
    결과값
    <a href="https://imgbb.com/"><img src="https://i.ibb.co/gyCVK3R/2020-10-01-11-39-33.png" alt="2020-10-01-11-39-33" border="0"></a>
  
    - DOM Tree 를 알아야 한다 ! 자식태그, 자손태그까지. (자손태그에는 자식도 포함된다)

    - document
        - 웹 페이지 그 자체를 의미합니다. 웹 페이지에 존재하는 HTML 요소에 접근하고자 할 때 반드시 document 객체로부터 시작해야 합니다.

        - Method (메소드)
            - getElementsByTagName() : 해당 태그 이름의 요소를 모두 선택합니다.
	            // const p = document.getElementsByTagName('p');
            - getElementById() : 해당 아이디의 요소를 선택합니다.
            - getElementsByClassName() : 해당 클래스에 속한 요소를 모두 선택합니다.
            - getElementsByName() : 해당 name 속성값을 가지는 요소를 모두 선택합니다.
            - querySelectorAll() : 해당 선택자로 선택되는 요소를 모두 선택합니다.
	            // const p = document.querySelector All('div p');

        ```html
        <title>문서 객체 모델 - 2</title>
        <script>
        'use strict';
        window.onload = function(){
            const gnb = document.getElementById('gnb');
            console.log(gnb); // <nav id='gnb'>...</nav>
            console.log(gnb.parentNode); // <div>...</div> 
            console.log(gnb.children[0]); // <ul>...</ul>
            console.log(gnb.children[0].nextElementSibling); // null
            console.log(gnb.children[0].children[1].nextElementSibling); // <li>내용 3</li>
            console.log(gnb.children[0].firstElementChild); // firstChild (텍스트 노드 포함) , <li class='first'>내용 1</li>
        }
        </script>
        </head>
        <body>
        <h2>문서 객체 모델 - 2</h2>
        <div>
            <nav id="gnb">
                <ul>
                    <li class="first">내용 1</li>
                    <li>내용 2</li>
                    <li>내용 3</li>
                </ul>
            </nav>
        </div>
        </body>
        ```
    