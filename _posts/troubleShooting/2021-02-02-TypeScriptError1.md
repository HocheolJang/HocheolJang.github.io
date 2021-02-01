---
title: "[TS]Cannot use JSX unless the '--jsx' flag is provided 처리 방법"
excerpt: "에러를 처리하는 방법을 공유합니다 !"

categories:
  - TroubleShooting
tags:
  - typeScript
  - React
  - error
comments: true
# other options
---

오늘부터 작업하면서 만나는 여러 에러들을 처리하는 방법들을 공유할 예정입니다 ! TroubleShooting이라는 말을 Error를 처리할 때 써도 되는지 잘 모르겠지만, 그래도 어쨌든 문제를 해결하는 것이니까 ㅋㅋㅋError처리 및 여러가지 문제를 처리한 방법을 여기다가 공유할게요 !

### ' Cannot use JSX unless the '--jsx' flag is provided '

**만약 TS로 React를 하던 중 위와 같은 에러가 뜬다면?**

TypeScript와 React 조합으로 초기 세팅하고 프로젝트를 하다가 이 에러를 많이 만날 것입니다.
그럴 때 아래와 같이 해결하면 됩니다 ~ 저도 이렇게 하니까 바로 해결 됐어요 !VScode를 쓰시는 분은 아래처럼 따라하시면 됩니다. 사실 다른 IDE까지는 확인하지못했습니다.

1. **VScode 상에서 command + shift + p 버튼을 눌러주세요 !**

2. **'select typescript version' 입력**
   <img src="https://i.ibb.co/Dzxqy7D/2021-02-02-1-29-55.png">

3. **Use workspace Version 4.x.x 클릭**
   ![](https://i.ibb.co/nDHqDHF/2021-02-02-1-30-09.png)

아마 이렇게 하면 없어지실거에요 !
혹시 위와 같은 문제를 겪으시는 분이 있다면 꼭 해결해보세요 !

오늘 하루도 화이팅입니다 !

Ref)

1. [[typescript]Cannot use JSX unless the '--jsx' flag is provided](https://www.icatpark.com/entry/typescript-Cannot-use-JSX-unless-the-jsx-flag-is-provided)
2. [[Cannot use JSX unless the '--jsx' flag is provided](https://stackoverflow.com/questions/50432556/cannot-use-jsx-unless-the-jsx-flag-is-provided)]
