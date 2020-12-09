---
title: "[TIL] 알고리즘 문제 풀이"
excerpt: "알고리즘 문제 중 기억에 남는 것을 정리합니다"

categories:
  - algorithm
tags:
  - algorithm
comments: true
toc: true
toc_sticky: true
# other options
---

문제

주어진 숫자 배열에서, 0을 배열의 마지막쪽으로 이동시켜주세요.
원래 있던 숫자의 순서는 바꾸지 말아주세요.

(새로운 배열을 생성해서는 안 됩니다.)

```
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```

내가 푼 답

```javascript
const moveZeroes = nums => {
  let zeroCnt = 0 // 0을 세는 변수
  for(let i = 0; i < nums.length; i++){
    if (nums[i] == 0){
    zeroCnt += 1   // 배열을 돌면서 0의 갯수를 센다
  }
  }
nums = nums.filter(function(item){
    return item !== 0
  }) // 배열 내에 0이 아닌 것만 추출
  for (let i = 0; i < zeroCnt; i++){
  nums.push(0)    // 0의 갯수만큼 맨 뒤에 0 추가
  }
  return nums
}

```

<img src="https://i.ibb.co/9hrNK1z/2020-11-19-11-24-51.png" style="zoom:67%;" />

4.172초가 빠른건지 느린건지 모르겠다... 일단 풀긴 풀었다! 문법을 잘 몰라서 계속 console 찍어보고 무식하게만 푼다 ㅜㅜ 조금 더 다양한 method 공부가 필수 ! 그래도 매일 파이썬으로만 하다가 오늘 자바스크립트로 해결했다...뭔가 기분이 좋다! 기분이 좋아서 남기는 알고리즘 문제 ㅋㅋㅋㅋ

