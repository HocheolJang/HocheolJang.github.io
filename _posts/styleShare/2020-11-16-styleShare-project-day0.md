---
title: "[프로젝트일지] 스타일쉐어 클론 프로젝트 1일차"
excerpt: "2주간 진행할 스타일쉐어 프로젝트를 기록합니다"

categories:
  - styleShare
tags:
  - styleShare
  - project
comments: true
toc: true
toc_sticky: true
# other options
---

## 개요

<img src="https://i.ibb.co/h2xWRXL/2020-11-16-6-27-04.png" style="zoom:67%;" />

- 목적 : [스타일쉐어](https://www.styleshare.kr/) 를 클론하면서 리액트와 장고의 기본기를 향상한다
- 일정 : 2020년 11월 16일 (월) ~ 11월 27일 (금), 12일간 진행

## 오늘 한 일

- 팀 선정 / 자리배치
- 트렐로, 노션, 슬랙 셋업
- 프론트엔드 초기 세팅(CRA) , Git
- 메인 페이지 (점보트론, 인기 제품) 컴포넌트 작업 시작 ! 


## 시작

아침부터 바빴다. 사람들과 어떤 프로젝트를 하게 될 지, 어떤 프로젝트를 1차와 2차에 나눠서 할 지 예상하고 추측하기 바빴다. (결론적으로 많은 것이 틀렸다 ㅋㅋㅋ) 우리는 1등부터 12등까지 뽑힌 사이트들을 다 둘러보며 어떤 것이 좋은 지, 각자 어떤 프로젝트를 하고싶은지 이야기를 나눴다. 

오전 11시 조가 발표되었다.

<img src="https://i.ibb.co/JzDFPg6/image.jpg" style="zoom:67%;" />

" 과연 나는 어떤 조로 갈 것인가! "

<img src="https://i.ibb.co/6RJHSJc/2020-11-17-9-21-08.png" style="zoom:50%;" />

(아래 내용이 더 있었지만 너무 길어서 잘림...)

어쨌든 이 슬랙방이 울리자마자 모두가 소리를 지르며, 하이파이브를 하고 서로 뭉치기 바빴다. 멘토님들은 단체로 14기 방으로 들어와서 표정을 확인하셨고, 나 역시도 내가 원했던 사이트를 하게 되어서 매우 기분이 좋았다. 득표수가 높아서 스타일쉐어를 프로젝트로 하게될 줄은 알았지만 2차가 아닌 1차라서 조금 당황했던 것만 빼고 말이다. 조원들 모두가 실력도 좋고 좋은 사람들인 것을 알기에 너무 다행이었다. 프로젝트를 하는데 있어서 실력도 실력이지만 사람이 가장 중요하다고 회사를 다니면서 뼈저리게 느꼈기때문에 더더욱 간절했다.

어쨌든 프로젝트 시작 ! 기술블로그인데 이렇게 에세이만 써도 되나 싶지만, 어쨌든 코드를 작성하는 것외에도 이런 시간이 있었던건 사실이니까. 내일부터는 조금 더 코드랑 기술 중심으로 작성해보도록 하겠습니다...에세이 형식이 아니라...계속 쓰면서 발전시키겠습니다

팀을 모아서 가장 먼저 했던 것은 자리배치, 팀명 정하기 그리고 **같이 점심먹기** 였다 ㅋㅋㅋㅋㅋ(한국인은 또 같이 밥먹으면서 쌓는 정이 있으니...) 그 이후 약 2시간동안 긴 회의를 했다. 모두가 사이트를 하나씩 구석구석 살펴봤다. 사이트의 전체적인 구성이 어떻고, 여기에는 어떤 기능이 있으며, 이걸 눌렀을 때는 여기로 이동되고, 저거를 눌렀을 때는 이 화면이 띄어지는 것을 살펴보았다. 그리고 빠르게 우선순위를 정했다. 한정된 시간안에 어떤 것부터 집중해서 할 것인지 정하는 것은 매우 중요하다. 나는 PM으로서 전체적인 회의를 이끌면서 선택과 집중을 하기위해 노력했다. 사실 욕심은 매우 컸다. 그래도 많이 쳐내려고 해서 쳐낸 것 같았는데 나중에 정리할 때 보니 그래도 많더라. 그래도 그 시간을 통해 확인할 수 있었던 것은 모두가 잘하고싶어하는 열정으로 뭉쳐있다는 것?정도를 느꼈다. 그리고 다들 설렘과 동시에 초조함이 있었다. 시간은 짧고 해야할 것은 많으니. 나는 PM으로서 더 많이 쫄렸다. 평소에도 말이 많은 편인데 초조해지니 더 말이 많아지더라...(이자리를 빌어 팀원들께 미안합니다)

오늘 가장 많은 시간을 썼던 것은 회의와 더불어 초기세팅이다. 트렐로로 서로의 작업을 볼 수 있도록 세팅하고, 문서로 정리해야할 것은 노션에 정리하고, 또 서로 원만한 커뮤니케이션을 위해 슬랙방을 만들었다. 본격적인 프론트엔드 개발을 위해 CRA(create react app)로 세팅했다. CRA는 빠르게 세팅할 수 있다고 하지만 초보자인 나에게는 꽤나 시간이 걸렸다. 깃허브 만들고 연결하고 모두가 클론 받고 작업을 시작했다. 그 시간이 저녁 9시쯤 됐을까...? 그 때부터 각자 컴포넌트를 나눠서 작업을 시작했다.

하루가 참 길면서도 짧다. 하루종일 코딩과 개발에 관련된 것들을 하고 있는데 시간이 부족하다. 12일동안 우리는 얼마나 만들어낼 수 있을까? 내일은 또 얼만큼 발전해있을까? 멋지게 해내리라고 생각한다 ! 백엔드도 일을 많이 했는데... 내가 봤던 것은 데이터 모델링한 사진 한 장이었지만 나는 그 한 장의 사진을 위해 그들이 얼마나 치열하게 이야기 나누고 작성한 지 알기에 ㅎㅎㅎ

모두들 오늘 하루도 고생하셨어요 ~~~
내일 만나요 ! 




