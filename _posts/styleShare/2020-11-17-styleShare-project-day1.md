---
title: "[프로젝트일지] 스타일쉐어 클론 프로젝트 2일차"
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

- 메인 페이지 컴포넌트 만들기
  - 점보트론 (광고판) 90% 완성
  - 인기 상품 90% 완성
  - 인기 브랜드 50% 완성



1. 점보트론 (광고판)
   
<img src="https://i.ibb.co/HTQ8c0c/ezgif-com-gif-maker.gif" />
   

   
   그냥 이미지에 텍스트까지 적혀있는 하나의 이미지인줄 알았는데 뜯어보니 이것도 다 코딩으로 한 것이더라... 이미지는 이미지대로 있고 텍스트는 또 다 데이터를 받아서 진행하는 것같아서 나도 최대한 그렇게 하려고 노력했다. 지금은 하드코딩으로 내가 코드에 직접 카피를 다 담아뒀지만 추후에는 백엔드에서 받을 수 있도록 준비하고있다. 슬라이드를 어떻게 구현할 지 매우 고민했는데 다행히 react의 [slick](https://react-slick.neostack.com/)이라는 라이브러리가 있어서 그걸 가져다가 썼다. 그걸 안했으면 어떻게 했을 지....시간적 여유가 있다면 직접 코드를 다 쓰는게 가장 좋긴 하지만, 라이브러리를 가져다 쓰는 것도 연습해봐야겠다 ! 다행히 잘 구현됐는데 현재 90% 완성이라고 생각한 이유는 자동슬라이드, 드래그로 슬라이드 넘기기는 가능한데 버튼을 넘겼을 때는 안넘어간다. 그 부분을 조금 더 보완해야겠다. 그리고 현재 3장인데 6장까지는 만들어볼 생각이다...
   
2. 인기 상품 

   <img src="https://i.ibb.co/pyRkcs9/2020-11-18-9-40-33.png" />

   나름 현재 사이트와 거의 유사하게 구현했다 ! 아직 저 뒷 탭들을 구현하지는 못했지만 메인은 다 구현했고 각 상품의 이미지 위에 hover될 때마다 scale이 1.1배 커지는 것도 따라서 구현했다. 나름 있어보이는듯해!!! ㅋㅋㅋㅋㅋ 얼른 컴포넌트들 다 결합해서 얹어보고싶다! 이거할 때 힘들었던 것은 딱히 없었다. 딱 계산했던대로 나와서 너무 좋았던 컴포넌트 !

3. 인기 브랜드

   <img src="https://i.ibb.co/4Jh2ZQF/2020-11-18-9-46-09.png"/>

   악! 어제 이것까지 다 하고 집에 가고싶었는데 실패 ㅜㅜ 잘 되어가다가 각 브랜드별 박스크기를 정하고 서로 마진을 주기위해 노력했는데 실패했다. 그 간격을 벌리려고 박스를 만들어서 이미지를 넣었더니 갑자기 이미지들이 너무 커져버렸다. 다시 방법을 찾아야겠다! 그리고 이 것도 역시 슬라이드 버튼이 문제다 ㅜㅜ 자동으로 넘어가는 것은 라이브러리 기본 속성이라 문제 없고 버튼도 사실 기본 버튼을 써도 되지만 최대한 스타일쉐어랑 비슷하게 구현해보려고 했다. 약간 시간이 더 걸리는 중 ㅜㅜㅜ 할 수 있을거야! 오늘은 꼭 할 수 있으리라고 믿는다. 



## 오늘 느낀점

생각했던 것보다는 속도가 잘 나오고 있다. 프론트도 각자 모두의 일을 하고있고 백엔드도 차근차근 진행되고있다. 이것들을 합쳤을 때 어떻게 될 지는 장담할 수 없지만 어쨌든 분명 잘 되리라고 생각한다. 그걸 믿고 하는 수 밖에! 개발자들에게 시간을 더 많이 줘야한다...! 왜냐면...쉽게 구현될 것같던 것도 어쩔 때는 하루를 쓸 수가 있기 때문에 ... ㅜㅜㅜ 계속 삽질하다보면 분명 실력이야 더 늘겠지만 ! ㅎㅎㅎ 그리고 역시 프로젝트를 만드는건 재미있다. 뭔가 신선하고 새로워! 매일 매일이 도전의 연속이다. 내일은 또 어떤 삽질이 나를 기다릴 것인가. 화내지말고 웃으면서 재미있게 하자!