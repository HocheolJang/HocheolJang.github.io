---
title: "[후기] 직방 클론 프로젝트"
excerpt: "치열하게 고민하고 코딩했던 2주간의 기록을 최종적으로 정리합니다"

categories:
  - TIL
tags:
  - project
comments: true
# other options

---

# Shabang Project

<img src="https://i.ibb.co/1L79yWV/login-Logo.png" style="zoom:67%;" />

## Overview

- 목 적 : [직방](https://www.zigbang.com/) 사이트를 클론하면서 리액트의 기본기를 향상한다

- 일 정 : 2020년 11월 30일 (월) ~ 12월 11일 (금), 12일간 진행

- 팀 구성 / 기술 스택 ( 총 6명 )
  - 프론트엔드 (Front-End) : 장호철, 김동하, 엄문주 (3명) / 참고 : [Github](https://github.com/wecode-bootcamp-korea/14-2nd-SHABANG-frontend)
    - React
    - Kakao Map API
    - Kakao Login
    - Google Login
    - JavaScript (ES6+)
    - HTML / CSS
    - SASS
    - Git / Github 
  - 백엔드 (Back-End) : 김정식, 김민서, 이민영 (3명) / 참고 : [Github](https://github.com/wecode-bootcamp-korea/14-2nd-SHABANG-backend)
  	- Django
	- Python
  	-  bcypt
  	-  Decorator
  
- 주요 구현 사항 (Bold로 표기된 것은 제가 작업한 영역입니다 )
	- 아파트
		- 검색기능
		- 필터기능
		- 매매가/전세가 비교
		- **주변시설**
	- 원룸 페이지
		- 데이터 클러스터링
		- Navbar
		- **주변시설**
  - **로그인 페이지**
		- 카카오 로그인
		- 구글 로그인 

## 후기

1차 프로젝트는 React의 Class형 문법과 SCSS를 사용했다면, 2차 프로젝트는 함수형 문법과 Styled Component로 구현하는 연습을 했다. Github도 Rebase해서 커밋을 깔끔하게 정리하는 것도 실제로 연습하면서 진행했는데 너무 재미있었다. 처음에는 어떻게 할 지 참 고민이었는데 뭐든지 하다보면 다 적응되는 것같다. 개발에 있어서 어쩌면 가장 중요한 것은 실력도 실력이지만 쫄지않는 자세, 낯선 것이 왔을 때 그 것을 즐겁게 받아드리는 마음이 더 중요한 것 아닐까. 하는 생각이 들었다. 더 많은 기능을 구현할 수 있었으면 좋았겠지만, 좋은 코드로 다듬는 것도 중요하니까 다듬는데 더 신경을 많이 썼던 시간이었다. 지금의 내 코드도 100점짜리는 아니겠지만 그래도 조금 단순했던 코드들을 뭔가 더 효율적으로 코드를 짜니 기분이 너무 좋았다. 리팩토링에 대해서 노력했었다고 생각했지만 이번에 리팩토링 하는 과정에서 진짜로 많이 배울 수 있었다. 파울러 아저씨의 <리팩토링> 책도 꼭 한 번 읽어봐야겠다.   

## 결과 화면

### 주변시설

우선 내가 맡은 페이지는 직방에 없는 기능이었다. 지도API를 꼭 구현해보고싶지만, 프로젝트 목표로 아파트, 원룸 페이지를 구현하기로 했으니 추가적인 지도는 없었다. 근데 꼭 하고싶다는 나의 의견에 다방에서 있는 위치 및 주변시설의 기능을 직방에 넣기로 했다. 그래서 아래의 형태처럼 해당 주소를 찍으면 그 주변의 편의시설, 안전시설, 학군 등을 보여주는 기능을 구현하기로 했다.

#### 다방 속 위치 및 주변시설 화면

<img src="https://i.ibb.co/YdkBWxr/2020-12-02-12-11-41.png" style="zoom:67%;" >



#### 실제 내가 구현한 화면

![](https://i.ibb.co/Hd5dhyb/image.gif)

우선 git rebase하는 과정에서 동료의 화면과 내가 구현한 것에 CSS 충돌이 있어서 dim처리된 화면이 일부 잘린 것처럼 표기 되어서 아쉬운 점이 있다. 그래도 우선 핵심 기능만 먼저 말하자면, 특정 아파트나 원룸을 클릭하면 그 id가 나에게 props로 떨어지게 되고 나는 그 값을 기준으로 서버에 해당 주소의 중심값과 주변시설에 대해서 요청을 한다. 그러면 서버에서 반경 1km내의 값을 다 보여주는 값을 보내준다. 나는 그 것에 따른 마커를 저장하여서 하나씩 보여준다. 사실 말로하기에는 매우 쉬워보이지만 실제 구현하기에는 조금 어려웠던 점이 있었다. 각각의 데이터를 따로 저장해야했고 마커 하나를 끌 때마다 re-render되는 이슈가 있었다. 그리고 re-render가 될 때마다 무조건 중심값으로 돌아와야했다. center좌표가 최초에 데이터를 받은 위치에 고정되어있었기때문이다. 이 때 매우 많이 힘들어했다. 그리고 리팩토링하면서 진짜 힘들었던 기억이 있다. 처음에는 kakao api문서처럼 각각의 좌표를 따로 찍었는데 멘토님께서 코드가 결국 반복되니까 추상화 작업을 하라고 했다. 이 때 코드를 합치고 나누고 하는 과정에서 진짜 힘들었다.

```javascript
const createMarkers = (items, type) =>
	items.map(({ latitude, longitude, name, distance }) => {
    const imageSrc = `/images/icon/${type}On.png`;
    const imageSize = new kakao.maps.Size(35, 35);
    const markerImage = new kakao.maps.MarkerImage(imageSrc,imageSize);
    const marker = new kakao.maps.Marker({
      position: new kakao.maps.LatLng(latitude, longitude),
      image: markerImage,
      clickable: true,
    });
    const infowindow = new kakao.maps.InfoWindow({
      content: `<div style="width: 150px; text-align:center; font-size: 16px; padding: 10px;">${name} (${distance}m)</div>`,
    });

    kakao.maps.event.addListener(
      marker,
      'mouseover',
      makeOverListener(map, marker, infowindow)
    );

    kakao.maps.event.addListener(
      marker,
      'mouseout',
      makeOutListener(infowindow)
    );
    return marker;
  });

const subways = nearbyList.subway;
const schools = nearbyList.school;
const stores = nearbyList.convenient_store;
const cafes = nearbyList.cafe;

setSubwaysMarkers(createMarkers(subways, 'subway'));
setSchoolsMarkers(createMarkers(schools, 'school'));
setStoresMarkers(createMarkers(stores, 'store'));
setCafesMarkers(createMarkers(cafes, 'cafe'));
};

const setMarkers = (markers, isRendering) => {
  markers.forEach((marker) => {
    marker.setMap(isRendering ? map : null);
  });
};

// componentDidMount
useEffect(() => {
  // fetch(`nearbyDataAPI/${targetRoomData[0].id}`)
  fetch(nearbyDataAPI)
    .then((res) => res.json())
    .then((res) => {
    const container = document.getElementById('nearbyMap'); // nearbyMap => 렌더링 되지 않으면.. 안 가져옴..
    const options = {
      center: new kakao.maps.LatLng(
        targetRoomData[0].lat,
        targetRoomData[0].lng
      ),
      level: 3,
    };
    map = new kakao.maps.Map(container, options);
    setNearbyList(res);
  });
}, []);

// useEffect componenDidUpdate 처럼 작동할 것 같지만.. 사실은 아니에요.
// useEffect 는 무조건 처음에 다 불린다.
useEffect(() => {
  Object.keys(nearbyList).length && getModalMap();
}, [nearbyList]);

useEffect(() => {
  schoolsMarkers.length && setMarkers(schoolsMarkers, isSchoolBtnOn);
  storesMarkers.length && setMarkers(storesMarkers, isStoreBtnOn);
  cafesMarkers.length && setMarkers(cafesMarkers, isCafeBtnOn);
  subwaysMarkers.length && setMarkers(subwaysMarkers, isSubwayBtnOn);
}, [
  isSubwayBtnOn,
  isStoreBtnOn,
  isCafeBtnOn,
  isSchoolBtnOn,
  schoolsMarkers,
  storesMarkers,
  cafesMarkers,
  subwaysMarkers,
]);
```

이렇게 코드를 추상화한 덕분에 약 200줄의 코드를 줄일 수 있었다. 원래는 학교, 편의점, 카페, 지하철 다 따로 코드가 있었으니 얼마나 복잡했겠는가. 진짜 길었는데 추상화의 위대함을 느낄 수 있었다. 이 코드를 내가 다 썼다고 할 수 없다. 기능 구현은 내가 다 했고 리팩토링의 시도 역시 많이 했지만 솔직하게멘토님께서 이렇게 줄이는 과정을 많이 도와주셨고 나는 이걸 계속 복습하면서 내 것으로 익히려 노력했다. 그래도 다 줄이고나니 얼마나 속이 다 시원하던지...

여기에 로드뷰 기능까지 얹이려고 시도했지만 결국 시간 내에 하기엔 어려웠다. 다음에 꼭 로드뷰를 다시 한 번 더 도전해봐야겠다.



### 로그인 페이지

<img src="https://i.ibb.co/7YSBzdn/2020-12-03-4-05-55.png" style="zoom:67%;" >

( 200 OK, 서버랑 통신 성공하고 처음으로 팝업이 떴을 때 ! 너무 기분이 좋아서 캡쳐했던 화면)



#### 카카오 / 구글 로그인

<img src="https://i.ibb.co/xGttYQ1/image.gif" style="zoom: 50%;" /><img src="https://i.ibb.co/x3VZYDq/image.gif" style="zoom:50%;" />

처음에는 어려울까봐 걱정했는데 API를 그대로 따라하니 금방 됐다 ! 난관이 있었다면 구글 API문서를 따라하니 버튼 커스텀하는 CSS가 매우 까다로웠다. 그래서 그 부분때문에 그냥 라이브러리를 가져오게되었다. 카카오 Login은 라이브러리 안쓰고 그냥 했으니 구글은 라이브러리를 쓰게 되었다. 로그인은 사실 기능구현보다 서버와의 통신과정에서 잠시 에러가 있어서 그 부분이 어려웠다. 서로 토큰을 주고받는 방법에서 커뮤니케이션 미스가 있었고 그 것만 해결하니 그 뒤로는 아무 문제가 없었다. 그리고 기존에 config.js만 써보다가 이번에 처음으로 env파일에 주요정보를 담는 것까지 해봤는데 다행히 잘 처리한 것같아서 너무 좋았다.



아래는 다른 팀원들이 진행했던 결과물입니다.

### 1. 아파트 페이지

#### 1.1 검색기능

![](https://i.ibb.co/x8wgx1r/image.gif)

#### 1.2 아파트 페이지 상세 화면

![](https://i.ibb.co/LZSwdTg/image.gif)

### 2. 원룸 페이지



#### 2.1 데이터 클러스트링 (zoom Level에 따라 다르게 표기)

![](https://i.ibb.co/L1ynsSB/image.gif)

#### 2.2 확대했을 때 원룸 페이지

![](https://i.ibb.co/D8fnDC4/2.gif)

![](https://i.ibb.co/VWykvWh/image.gif)

![](https://i.ibb.co/8c8Tx6v/2.gif)



이렇게 2차 프로젝트까지 끝이 났습니다. 2주라는 시간이 진짜 어떻게 끝났는지 모를만큼 빠르게 시간이 지나갔고 또 하나의 경험이 생겨서 기분이 좋습니다. 지도API는 언젠가 또 쓰게될 일이 있을 것같은데 이렇게 경험할 수 있어서 좋았고 조금 더 깊게 다뤘으면 더 좋았겠지만, 그건 또 다음에 다른 기회가 있을 것이라고 생각합니다. 함께할 수 있어서 즐거웠습니다 샤방팀분들 !

