---
title: "[코딩테스트] JavaScript로 푸는 codility 1번 문제 풀이"
excerpt: "codility 연습문제 1번입니다. "

categories:
  - algorithm
tags:
  - algorithm
comments: true
# other options
---

취업을 위한 코딩테스트 연습한다고 codility로 연습을 하고있습니다. 사실 처음 봤을 때 '응? 뭔말이지?' 했습니다. 사실 저는 아직 자료구조나 알고리즘에 대한 공부가 부족해서 '출제자의 의도는 무엇인지', '어떻게 푸는 것이 좋은 것인지' 전혀 모릅니다. 다른 사람들의 답변을 참고해서라도 공부해보려 합니다. 다른 사람이 푸는 방식을 보고 저도 생각해볼 수 있고, 또 공부가 될 수 있다고 생각하기 때문입니다. 아래의 푸는 방식은 어떤 분이 [파이썬으로 푼 방식](https://www.youtube.com/watch?v=5YLDEvJi1XI)을 참고하여 제가 자바스크립트로 바꿔서 푼 것입니다. 사실 그 분과 푸는 방식은 동일합니다. 만약 조금 더 좋은 방법이 있는지 찾아보고 있다면 업데이트 하겠습니다.



## 문제

```
A *binary gap* within a positive integer N is any maximal sequence of consecutive zeros
that is surrounded by ones at both ends in the binary representation of N.

For example, number 9 has binary representation `1001` and contains a binary gap of length 2. The number 529 has binary representation `1000010001` and contains two binary gaps:
one of length 4 and one of length 3. The number 20 has binary representation `10100`
and contains one binary gap of length 1. The number 15 has binary representation `1111`
and has no binary gaps.
The number 32 has binary representation `100000` and has no binary gaps.

Write a function:

function solution(N);

that, given a positive integer N, returns the length of its longest binary gap.
The function should return 0 if N doesn't contain a binary gap.

For example, given N = 1041 the function should return 5, because N has binary
representation `10000010001` and so its longest binary gap is of length 5.
Given N = 32 the function should return 0, because N has binary representation '100000'
and thus no binary gaps.

Write an ***\*efficient\**** algorithm for the following assumptions:

 - N is an integer within the range [1..2,147,483,647].

```

출처 : [코딜리티Lesson 1번](https://app.codility.com/programmers/lessons/1-iterations/)

### 문제 해석

해석해보면 그렇게 어려운 내용은 아니다. 'binary gap'이라는 것을 구하면 된다. 말 그대로 2진법수의 gap?이라고 해야하나? 예를 보면 조금 더 이해가 쉽다. 10진법 9는 2번법 1001이 된다. 그럼 1과 1사이에 0이 2개가 있으니 binary gap은 2가 된다. 10진법 529는 2진법으로 변환하면, 1000010001가 된다. 그럼 1이 3번이 나오니까 첫번째 1과 두번째 1의 거리를 구하고, 두번째 1과 3번째 1의 거리를 구해야한다. 첫번째 gap은 4, 두번째 gap은 3이 나온다. 그럼 더 긴쪽인 4가 정답이 된다. 만약 10진법 15처럼 2진법 1111인 경우, 0이 하나도 없기때문에 0을 리턴하면 된다.



## 내가 푼 답

```javascript
let N = 1041; // testCase 

function solution(N) {
  
    // step 1. 10진수를 2진수로 전환 처리하고, 자리수간의 거리를 계산해줍니다.
	
  	let result = ''; // 최종적으로 나올 결과값
    let num = parseInt(N); 
    let binaryNum = (num.toString(2)); // 10진수를 2진수로 전환

  
    let arr = [] // 자릿수를 넣을 빈 배열 선언
    for(let i = 0; i < binaryNum.length; i++){
        if (binaryNum[i] === '1'){
           arr.push(i)
        }
    }
  	console.log(binaryNum) // 10000010001
    console.log(arr) // [0, 6, 10] 1의 자릿수만큼의 배열로 만들었어요 ! 위의 숫자를 보시면 이해되실거에요
    
    // step 2. 자리수간의 거리를 계산해줍니다.
    
    arr2 = [];
    for (let i = 0; i < arr.length; i++){
     if (i !== arr.length -1) {
       temp = arr[i+1] - arr[i]
       temp = temp - 1 // 두 값을 뺀 다음 -1을 해줘야 1과 1사이의 0의 갯수가 나옵니다.
       arr2.push(temp)
      }
    }
    console.log(arr2) // [ 5, 3 ] 반복문을 돌면서 나온 gap들의 배열
  
  if (arr2.length === 0){ // 2진수가 1111 인경우, 위의 배열의 값이 안나올 것입니다. 0으로 리턴!
    return 0 
  } else {
    return result = Math.max.apply(null, arr2) // 배열내에서 가장 큰 값을 계산하는 방법 !
  }  
}

```



너무 재밌었다 ! ㅋㅋㅋ 문제를 잘 이해하고 해결해야하는 문제를 step별로 쪼개서 하나씩 접근하기 !
console.log만 있다면...차근차근 하나씩 확인하면서 문제풀 수 있을 것같다 !

