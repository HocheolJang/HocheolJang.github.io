---
title:  "JavaScript-8(노드, form객체, 정규식, 이벤트) "
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

### 노드(node)
HTML DOM은 노드라고 불리는 계층적 단위에 정보를 저장합니다.
HTML DOM은 노드들을 정의하고, 그 사이의 관계를 설명해주는 역할을 합니다.
HTML 문서의 정보는 노드 트리라고 불리는 계층적 구조에 저장됩니다.
노드 트리는 노드들의 집합이며 노드간의 관계를 보여줍니다.
노드 트리는 최상위 레벨인 루트 노드로부터 시작하고, 가장 낮은 레벨인 텍스트 노드까지 내려갑니다.
HTML DOM을 이용하여 노드 트리에 포함된 모든 노드에 접근 할 수 있습니다.
    
#### 노드 종류
- 문서 노드(document node) : 문서 전체를 나타내는 노드
- 요소 노드(element node) : HTML 요소는 요소 노드이며, 속성 노드를 가질 수 있는 유일한 노드입니다.
- 속성 노드(attribute node) : HTML 요소의 속성은 속성 노드이며, 요소 노드에 관한 정보를 가지고 있습니다.
하지만 해당 요소 노드의 자식 노드에는 포함되지 않습니다.
- 텍스트 노드(text node) : HTML 문서의 모든 텍스트는 텍스트 노드입니다.
- 주석 노드(comment node) : HTML 문서의 모든 주석은 주석 노드입니다.
    
#### 노드 간의 관계
- parentNode : 부모 노드
- childNodes : 자식 노드 리스트
- firstChild : 첫번째 자식 노드
- lastChild : 마지막 자식 노드
- nextSibling : 다음 형제 노드
- previousSibling : 이전 형제 노드
- TIP. 빈 텍스트 : 
익스플로러를 제외한 대부분의 브라우저는 요소와 요소 사이에 빈 공백 또는 개행이 이루어지면 텍스트노드로 처리됩니다.
따라서 노드간의 관계에 텍스트 노드가 중간에 사용되면 노드 이동이 불명확해 질 수 있습니다.
    
#### 노드 추가
- appendChild() : 새로운 노드를 해당 노드의 자식 노드 리스트 맨 마지막에 추가합니다.
- insertBefore() : 새로운 노드를 특정 자식 노드 바로 앞에 추가합니다.
- insertData() : 새로운 노드를 텍스트 데이터에 새로운 텍스트로 추가합니다.

```html
<h2>노드의 추가</h2>
<p id="item1">JavaScript</p>
<p id="item2">jQuery</p>
<hr/>
<div id="list">
    <p id="server">node.js</p>
    <p>css</p>
    <p>HTML</p>
</div>
<hr/>
    <p id="text">지금 시간은 오전 11시 30분입니다.</p>
<hr/>
<button onclick="appendNode()">노드 추가1</button>
<button onclick="insertNode()">노드 추가2</button>
<button onclick="appendText()">텍스트 추가</button>
<script>
    'use strict';
    function appendNode(){
        const parent = document.getElementById('list');
        const newItem = document.getElementById('item1');
        parent.appendChild(newItem);
    }
    function insertNode(){
        const parent = document.getElementById('list');
        const serverItem = document.getElementById('server');
        const newItem = document.getElementById('item2');
        parent.insertBefore(newItem, serverItem)
    }
    function appendText(){
        const text = document.getElementById('text').firstChild;
        text.insertData(7, "아주 피곤한 ");
    }
    </script>
```
    
#### 노드 생성
- createElement() : 새로운 요소 노드를 만들 수 있습니다.
- createAttribute() : 새로운 속성 노드를 만들 수 있습니다. 만약 같은 이름의 속성 노드를 이미 존재한다면, 기존 속성 노드는 새로운 속성 노드로 대체됩니다.
- createTextNode() : 새로운 텍스트 노드를 만들 수 있습니다.

```html
<h2>노드의 생성</h2>
<p id="el">새로운 문장이 이 문장 앞에 추가됩니다.</p>
<p id="attr">이 단락에 새로운 속성이 추가됩니다.</p>
<p id="text"></p>

<button onClick="createNode()">요소 노드 생성</button>
<button onClick="createAttr()">속성 노드 생성</button>
<button onClick="createText()">텍스트 노드 생성</button>

<script>
    'use strict';
    function createNode(){
        const elNode = document.getElementById('el'); // <p id="el">새로운 문장이 이 문장 앞에 추가됩니다.</p>
        const newNode = document.createElement('p');    // <p></p>
        newNode.innerHTML = "<b>새로운 요소입니다.</b>";    // <p><b>새로운 요소입니다.</b></p>
        document.body.insertBefore(newNode, elNode);
    }
    function createAttr(){
        const attr = document.getElementById('attr');   // <p id="attr">이 단락에 새로운 속성이 추가됩니다.</p>
        const newAttr = document.createAttribute('style');  // style=""
        newAttr.value = 'color: deepskyblue';   // style="color: deepskyblue"
        // <p id="attr" style="color: deepskyblue">이 단락에 새로운 속성이 추가됩니다.</p>
        attr.setAttributeNode(newAttr); 
    }
    function createText(){
        const textNode = document.getElementById('text');
        const newText = document.createTextNode('새로운 텍스트입니다.');
        textNode.appendChild(newText);
    }
    </script>
```

#### 노드 제거
- removeChild() : 자식 노드 리스트에서 특정 자식 노드를 제겅합니다. 성공적으로 노드가 제거되면 제거된 노드를 반환합니다. 노드가 제거될 때에는 제거되는 노드의 모든 자식들도 다같이 제거됩니다.
- removeAttribute() : 속성의 이름을 이용하여 특정 속성 노드를 제거합니다.

```html
<h2>노드의 제거</h2>
<div id='list'>
    <p>HTML</p>
    <p id="item">CSS</p>
    <p id="js" style="background-color: gold; color: deeppink">JavaScript</p>
    <p>jQuery</p>
</div>
<button onclick="removeNode()">요소 노드 삭제</button>
<button onclick="removeAttr()">속성 노드 삭제</button>

<script>
    'use strict';
    function removeNode() {
        const parent = document.getElementById('list');
        const removeItem = document.getElementById('item');
        const result = parent.removeChild(removeItem);
        console.log(result);
        console.log(result.nodeName);
    }
    function removeAttr(){
        const js = document.getElementById('js');
        js.removeAttribute('style');
        
    }
</script>
```
#### 노드 복제
- cloneNode() : 기존의 존재하는 노드와 동일한 새로운 노드를 생성하여 반환합니다.
- 복제할 노드.cloneNode(자식노드 복제여부);
- 자식노드 복제여부 : 전달될 값이 true면 복제되는 노드의 모든 속성과 자식 노드도 같이 복제되고, false면 속성 노드만 복제하고 자식 노드를 복제하지 않습니다.

```html
<h2>노드의 복제</h2>
<h3 id="item">복제된 아이템입니다.</h3>
<div id="list">
    <p>HTML</p>
    <p>CSS</p>
    <p>JavaScript</p>
    <p>jQuery</p>
</div>
<button onclick="cloneElement()">노드 복제</button>
<script>
    'use strict'
    function cloneElement(){
        const parent = document.getElementById('list');
        const originItem = document.getElementById('item');
        parent.appendChild(originItem.cloneNode(true));
    }
</script>
```

#### 노드 교체
- repaceChild() : 기존의 요소 노드를 새로운 요소 노드로 교체할 수 있습니다.
-  교체된 노드 = 부모노드.replaceChild(새로운 자식노드, 기존 자식노드);
- repaceData() : 텍스트 노드의 텍스트 데이터를 바꿀 수 있습니다.
- 텍스트 노드.replaceData(오프셋, 교체할 문자수, 새로운 데이터);

```html
<h2>노드의 교체</h2>
<div id="parent">
    <p id="first">김사과</p>
    <p>오렌지</p>
    <p>반하나</p>
</div>
<p id="second">이메론</p>
<hr/>
<p id="text">좋아하는 과일은 사과 입니다.</p>

<button onclick="changeNode()">요소 노드 교체</button>
<button onclick="changeText()">텍스트 노드 교체</button>


<script>
    'use strict';
    function changeNode(){
        const parent = document.getElementById('parent');
        const first = document.getElementById('first');
        const second = document.getElementById('second');
        parent.replaceChild(second, first);
    }
    
    function changeText(){
        const text = document.getElementById('text').firstChild;
        text.replaceData(9, 2, "오렌지");
        
    }
</script>
```

### 폼(Form) 객체

일반적인 폼에 접근할 때 사용합ㄴ다. id 또는 name을 이용하여 접근합니다. 또한 documents.forms 컬렉션을 이용하여 접근 할 수도 있습니다.
    
```html
<form name="myform" id="regform" method="post" action="regist.php">
    아이디 : <input type="text" name="userid" id="id"><br>
    비밀번호 : <iput type="password" name="userpw" id="pw"><br>
    <input type="submit" value="전송">
</form>
```    
  
#### 폼에 접근하는 방법

```javascript
const frm = document.myform;
const frm = document.getElementById('regform');
```

#### 아이디로 value 접근하는 방법

```javascript
const id = document.myform.userid.value;
const id = frm.userid.value;
const id = frm.elements[0].value;
const id = frm.elements['userid'].value;
const id = document.getElementById('id').value;
```

```html
 <h2>폼 객체</h2>
    <form name="frm1">
        <input type="search" name="search" placeholder="검색어 입력"><br>
        <input type="submit" value="확인">
    </form>
    <form name="frm2">
        <input type="text" name="userid" id="id" placeholder="아이디 입력" value="apple"><br>
        <input type="password" name="userpw" placeholder="패스워드 입력"><br>
        <input type="submit" value="확인">
    </form>
    <script>
        'use strict';
        const frm1 = document.frm1;
        const frm2 = document.frm2;
        console.log(frm1.search.placeholder);   // 검색어 입력
        console.log(frm2.userid.placeholder);   // 아이디 입력
        console.log(frm2.userid.value);         // apple
        console.log(document.forms[1][0].value);    // apple
        console.log(document.forms['frm2'].elements['userid'].value);   // apple
        console.log(document.getElementById('id').value);   // apple
    </script>
```



### 자바스크립트 정규표현식
정규표현식(Regular Expression)은 문자열을 처리하는 방법 중의 하나로 특정한 조건의 문자를
'검색'하거나 '치환'하는 과정을 매우 간편하게 처리할 수 있도록 하는 수단이다 - 생활코딩 -

#### 표현방법
- ^x : 문자열이 x로 시작한다 
- x$ : 문자열이 x로 끝난다 
- .x : 임의의 한 문자를 표현한다 
- x+ : x가 1번이상 반복한다 
- x? : x가 존재하거나 존재하지 않는다 
- x* : x가 0번이상 반복한다 
- x|y : x또는 y를 찾는다 
- (x), (x)(y), (x)(?:y) : ()안의 내용을 캡쳐하며, 그룹화 한다 
- x{n} : x를 n번 반복한 문자를 찾는다 
- x{n,} : x를 n번 이상 반복한 문자를 찾는다 
- x{n,m} : x를 n번 이상 m번 이하 반복한 문자를 찾는다 

- [xy] : x,y중 하나를 찾는다
- [^xy] : x,y를 제외하고 문자 하나를 찾는다 
- [x-z] : x~z 사이의 문자중 하나를 찾는다 
- \^ : 특수문자를 문자로 인식함 
- \b : 문자와 공색사이의 문자를 찾는다 
- \B : 문자와 공백사이가 아닌 값을 찾는다 
- \d : 숫자를 찾는다 
- \D : 숫자가 아닌 값을 찾는다 
- \s : 공백문자를 찾는다 
- \S : 공백이 아닌 문자를 찾는다 
- \t : Tab 문자를 찾는다 
- \v : Vertical Tab 문자를 찾는다 
- \w : 알파벳 + 숫자 + _ 를 찾는다
- \W : 알파벳 + 숫자 + _을 제외한 모든 문자를 찾는다

```javascript
// example
const expPwText = /^.*(?=^.{4,20}$)(?=.*\d)(?=.*[a-zA-Z])(?=.*[!@#$%^&*()+=]).*$/;
const expNameText = /[가-힣]+$/;
const expHpText = /^\d{3}-\d{3,4}-\d{4}$/;
const expEmailText = /^[A-Za-z0-9\.\-]+@[A-Za-z0-9\.\-]+\.[A-Za-z0-9\.\-]+$/;
```

#### 정규식을 체크하는 방법
test() : 정규식 표현식에 대입한 문자열이 부합하면 true, 아니면 false를 반환합니다.

```javascript
const 상수이름 = /정규식 패턴/;
const 문자열 = 값;
상수이름.test(문자열); -> true or false
```

### 이벤트(Event)
이벤트란 웹 브라우저가 알려주는 HTML 요소에 대한 사건의 발생을 의미합니다. 웹 페이지에 사용된 자바스크립트는 발생한 이벤트에 반응하여 특정 동작을 수행할 수 있습니다. 따라서 자바스크립트를 비동기식 이벤트 중심의 프로그래밍 모델이라고 합니다.

#### 이벤트 타입(Event Type)
이벤트 타입은 발생한 이벤트의 종류를 나타내는 문자열로 이벤트명이라고도 합니다. 가장 많이 사용하는 키보드, 마우스, HTML DOM, window 객체등을 처리하는 이벤트가 폭넓게 제공되고 있습니다.

ref. https://developer.mozilla.org/en-US/docs/Web/Events

```html
<h2>이벤트 타입</h2>
<p id="text"></p>
<p onclick="changeText(this)">문자열을 클릭하세요.</p>
<script>
    window.onload = function(){
        const text = document.getElementById('text');
        text.innerHTML = "<i>HTML 문서가 모두 로드되었습니다.</i>";
    }
</script>
<script>
    function changeText(el){
        el.innerHTML = "<b>문자열의 내용이 변경되었어요.</b>";
    }
</script>
```

#### 이벤트 타겟(Event Target)
이벤트가 일어날 객체를 의미합니다.

#### 이벤트 리스너(Event Listener)
이벤트가 발생했을 때 그 처리를 담당하는 함수를 의미합니다. 이벤트 핸들러라도고 부르며, 지정된 타입의 이벤트가 특정 요소에서 발생하면, 웹 브라우저는 그 요소에 등록된 이벤트 리스너를 실행합니다.

```javascript
<input type="button" onclick="sendit()" value="가입완료">
	     ------  ------- --------
	    이벤트타겟  이벤트명  이벤트리스너
```

#### 이벤트 리스너를 만드는 방법
1. 프로퍼티로 이벤트를 등록하는 방법
window.onload = function(){
	이벤트 실행문..
}

    * 프로퍼티로 이벤트를 등록하는 방법은 모든 브라우저가 대부분 이벤트 타입으로 지원하고 있습니다. 단점은 이벤트 타입별로 오직 하나의 이벤트 리스너만을 등록 할 수 있다는 점입니다.

2. 객체나 요소의 메소드에 이벤트 리스너를 전달하는 방법

```javascript
이벤트타겟1.addEventListener(이벤트타입, 이벤트리스너); // 등록
이벤트타겟2.addEventListener(이벤트타입, 이벤트리스너);	// 등록
이벤트타겟1.removeEventListener(이벤트타입, 이벤트리스너);	// 제거

function 이벤트리스너(){
	이벤트 실행문..
}
```

```html
<h2>이벤트 리스너</h2>
<p><button id="eventBtn">이벤트 버튼</button></p>
<p><button id="delBtn" onclick="delEvent()">이벤트 삭제 버튼</button></p>
<p id="text"></p>
<script>
    'use strict';
    const btn = document.getElementById('eventBtn');
    btn.addEventListener('click', clickBtn);
    btn.addEventListener('mouseover', mouseOverBtn);
    btn.addEventListener('mouseout', mouseOutBtn);


    function clickBtn(){
        document.getElementById('text').innerHTML = '<b>버튼을 클릭했어요</b>';
    }
    function mouseOverBtn(){
        document.getElementById('text').innerHTML = '<b>버튼 위에 마우스가 올라갔어요</b>';
    }
    function mouseOutBtn(){
        document.getElementById('text').innerHTML = '<b>버튼 밖으로 마우스가 나갔어요</b>';
    }

    function delEvent(){
        btn.removeEventListener('mouseover', mouseOverBtn);
        btn.removeEventListener('mouseout', mouseOutBtn);
        document.getElementById('text').innerHTML = '<b>이벤트 리스너가 삭제되었어요</b>';
    }
    </script>
```

#### 이벤트 객체(Event Object)
이벤트 객체란 특정 타입의 이벤트와 관련이 있는 객체입니다. 이벤트 객체는 해당 타입의 이벤트에 대한 상세 정보를 저장하고 있습니다. 모든 이벤트 객체는 이벤트의 타입을 나타내는 type 프로퍼티와 이벤트 대상을 나타내는 target 프로퍼티를 가집니다. 이벤트 객체는 이벤트 리스너가 호출될 때 인수로 전달됩니다.

```javascript
<input type="button" onclick="sendit()" value="가입완료">

function sendit(e){	// e : 이벤트 객체
	console.log(e.target); // 이벤트 타겟
	console.log(e.type); // 이벤트 타입      
}
```

```html
<h2>이벤트 객체 - 1</h2>
<input type="button" id="btn" value="버튼">
<script>
    'use strict';
    const btn = document.getElementById('btn');
    btn.addEventListener('click', clickBtn);

    function clickBtn(e){
        console.log(e.target.id);       // btn
        console.log(e.target.value);    // 버튼
        console.log(e.type);            // click
    }
</script>
```

```html
<h2>이벤트 객체 - 2</h2>
<input type="button" id="btn1" value="버튼1">
<input type="button" id="btn2" value="버튼2">
<input type="button" id="btn3" value="버튼3">
<script>
    'use strict';
    const btn1 = document.getElementById('btn1');
    const btn2 = document.getElementById('btn2');
    const btn3 = document.getElementById('btn3');

    btn1.addEventListener('click', clickBtn);
    btn2.addEventListener('click', clickBtn);
    // btn3.addEventListener('click', function(){
    //     console.log('버튼 3이 눌렸어요.');
    // });
    btn3.addEventListener('click', (event) => {
        console.log(`event.target.id : ${event.target.id}`);
    });
    
    function clickBtn(e){
        switch(e.target.id){
            case "btn1":
                console.log('버튼 1이 눌렸어요.');
                break;
            case "btn2":
                console.log('버튼 2가 눌렸어요.');
                break;
        }
    }
</script>
```

#### 이벤트 전파
이벤트 전파란 이벤트가 발생했을 때 브라우저가 이벤트 리스너를 실행시킬 대상 요소를 결정하는 과정을 의미합니다. 이벤트의 대상이 window 객체와 같은 단일 객체라면 이벤트의 전파는 일어나지 않습니다. 하지만 document 객체나 HTML 문서의 요소에서 이벤트가 일어나면 대상 요소를 결정하기 위해 이벤트의 전파가 일어납니다. 이벤트 전파 방식은 버블링 전파방식과 캡처링 전파방식으로 나뉩니다.

- 버블링 전파방식
    - 이벤트가 발생한 요소부터 시작하여 DOM트리에 따라 위쪽으로 올라가며 전파되는 방식입니다.
- 캡처링 전파방식
    - 이벤트가 발생한 요소까지 DOM트리의 최상위부터 아래쪽으로 내려가며 전파되는 방식입니다. addEventListener() 메소드의 세번째 인수에 true를 전달하면 됩니다.

- event객체.stopPropagation() : 이벤트 전파를 막습니다.

```html
<h2>이벤트 전파</h2>
<div id="divBox">
    <p id="pBox">박스 안의 여러 곳을 <span id="spanBox">클릭</span>하세요.</p>
</div>
<p id="text"></p>
<script>
    'use strict';
    // 버블링 전파방식
    document.getElementById('divBox').addEventListener('click', clickDiv);
    document.getElementById('pBox').addEventListener('click', clickP);
    document.getElementById('spanBox').addEventListener('click', clickSpan);
    // 캡처링 전파방식
    // document.getElementById('divBox').addEventListener('click', clickDiv, true);
    // document.getElementById('pBox').addEventListener('click', clickP, true);
    // document.getElementById('spanBox').addEventListener('click', clickSpan, true);

    function clickDiv(e){
        document.getElementById('text').innerHTML += 'div 요소를 클릭했어요.<br>';
        e.stopPropagation();
    }
    function clickP(e){
        document.getElementById('text').innerHTML += 'p 요소를 클릭했어요.<br>';
    }
    function clickSpan(e){
        document.getElementById('text').innerHTML += 'span 요소를 클릭했어요.<br>';
    }

</script>
```


    
    
    
