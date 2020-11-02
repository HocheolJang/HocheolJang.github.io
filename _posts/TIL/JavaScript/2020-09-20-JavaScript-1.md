---
title:  "JavaScript-1(역사, 특징)"
excerpt: "자바스크립트(입문용) 정리합니다"

categories:
  - JavaScript
tags:
  - JavaScript
comments: true
toc: true
toc_sticky: true
classes: wide
# other options
---
  
### 1.JavaScript의 역사 (믿거나말거나)

- 넷스케이프 브라우저가 유행하던 시절 모든 사이트는 정적인 웹사이트였다. 브랜던 아이크라는 사람이 "동적인 웹사이트 만들어보자"라고 생각을 했고,
그 때 만든게 모카라는 언어였다. 그 이후에 LiveScript라는 이름으로 바꿨다가 Java가 유명해지자 그 유명세에 묻어가기 위해
JavaScript라는 이름으로 바꿨다고 한다. 이게 지금까지 이어졌다.        
JavaScript가 잘 성장하자 마이크로소프트는 그걸 은근히 빼껴 JScript라는 것을 만들게 되었지만 잘 안된듯...
(마이크로소프트는 원래 다른 회사의 것을 잘 카피했다고 한다. DOS도 한 중소회사에서 만들었던 것을 빼껴서 상용화한게 마이크로소프트라고 한다.
윈도우도 맥의 OS를 빼껴서 만든거라고 하더라. 그 이후 넷스케이프도 컴파일해서 빼낀 것이 익스플로어였고 이게 WindowOS에 묻어서 대박이 나며
브라우저 전체 시장의 점유율 90%를 만들게 되었다)


### 2. JavaScript의 특징

- 웹의 동작을 구현하기 위한 언어
- 웹 브라우저에서 사용 (단, Node.js 는 서버에서 동작)
- 웹 브라우저에는 자바스크립트 엔진(인터프리터)가 내장되어있다.
- HTML문서 내에서 `<script>` 태그 사이에 작성한다.
- 대소문자를 구별합니다. (HTML과 CSS는 구별하지않음)
- 객체 기반의 스크립트 언어입니다. (객체지향적 언어는 아니다)

### 3. JAVA Script 출력하는 방법

- `<script></script>` 의 위치는 어디에 놓여도 관계없음 `<head>`태그 혹은 `<body>` 코드 사이에 두면 된다.
- 위에서부터 내려오면서 읽히니까, 스크립트 위치 어디에다가 둘 지 늘 생각하고 써야한다.
    1. document.write를 써서 JS 출력 확인 가능!
        - document는 body를 의미하고, Write 는 해야하는 일을 의미
        ``` javascript
        document.write("안녕하세요. JavaScript(화면))
        ```
        - 문자는 꼭 ""나 ''를 써야한다.
        - ECMA5 이후로는 ;를 안적어도 된다. 그러나 ;를 쓰면 좋은 습관 (문장의 끝에 마침표를 쓰는 의미)
          한 줄이 끝났다는 의미는 세미콜론으로 받아들임. 되도록 한 줄에는 한 코드만 쓴다!
    2. console.log()함수를 사용해 브라우저 console창에서 출력
        - 가장 흔하게 쓰는 방법. 콘솔창은 playground~          
        ```javascript
        console.log("안녕하세요.JavaScript(콘솔)");
        ```

    3. 내부에 JS코드 쓰기도 하지만, 외부에 JS파일 만들어서 관리하는 방법을 더 많이 씀. html 복잡해지면 안돼!
        - `<script src="자바스크립트 파일 경로"></script>`
        - JavaScript 파일은 .js 확장자로 저장합니다.
        - JavaScript의 주석문은 한줄/다줄 주석문 다르게 쓴다 // 내용 (한줄 주석문) /* 내용 */ (여러줄 주석문)
        ``` javascript
       <script src="js/script.js"></script>
        ```
