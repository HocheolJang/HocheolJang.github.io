---
title: "[프로젝트일지] 스타일쉐어 클론 프로젝트 3일차"
excerpt: "2주간 진행하는 스타일쉐어 프로젝트를 기록합니다"

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

- 스탠드업 미팅 진행
- 메인 페이지 컴포넌트 결합
  - Navbar, Jumbotron, 인기 상품, 인기 브랜드 결합 !
- 코드 리뷰 & 리팩토링 
  - Self Closing 수정
  - 반복되는 부분 map함수로 변경
  - Directory 조정
  - Common.scss, reset.scss 변경
  - 인기 브랜드 비율 조정중 !
- 컴포넌트 & 기능 추가
  - 점보트론 화면넘기는 arrow기능
  - 인기 브랜드 비율 조정
  - 트렌드 기획전 레이아웃
- 그 외
  - 목업 데이터 구축 (사진 등)



1. 메인페이지 결합

   ![](https://i.ibb.co/kK1HPt8/Kapture-2020-11-20-at-15-35-48.gif)

   Git push 하기 전에 한 번 결합해보고싶어서 Nav, Jumbotron, PopularProduct를 결합했다. 처음에는 좌우 정렬이 잘 안되어서 애를 먹었지만 다행히 잘 해결하고 현재는 위와 같이 예쁜 모습을 가지고 있다. 현재 해상도 문제때문인지 같은 크기를 줘도 약간 달라보이는 점이 있지만 이건 다시 수정하기로 했다. 그래도 다행히 그럴싸해보이는 페이지가 만들어지고 있는 것같아서 기분좋다. 3일동안 열심히 했던 보람이 있다. 사진, 카피도 다 내가 고르고 썼는데 아주 그럴싸하다...(지난 4년간 일했던게 그렇게 쓸모가 없진 않은 것같다 여기저기 쓸 데가 있다 ㅋㅋㅋ)

2. 점보트론 (광고판)

<img src="https://i.ibb.co/HTQ8c0c/ezgif-com-gif-maker.gif" />

```jsx
constructor() {
  super();
  this.state = {
    jumbotronItem: [],
  };
  this.slider = React.createRef(); // 리액트의 createRef 로 슬라이더 지정
}

previous = () => {
  this.slider.current.slickPrev(); // slider 기본 기능 추가
};
next = () => {
  this.slider.current.slickNext(); // slider 기본 기능 추가
};

// 중간 생략

<img
  className="slideBtnLeft"
  src="images/icon/prev0.png"
  alt="prev"
  onClick={this.previous} // 화살표 눌렀을 때 함수 호출
  />
<img
  className="slideBtnRight"
  src="images/icon/next0.png"
  alt="next"
  onClick={this.next} // 화살표 눌렀을 때 함수 호출
  />
```

 현지님의 도움으로 해결했다. (늘 감사하지만 이 자리를 빌어 더 감사합니다) React-slick의 공식문서가 워낙 오래되었다 보니 최근의 문법을 따라오지 못하는 것도 많고 예전에는 되던 것이 지금은 안되는 것도 많다. 그래서 약간의 문법이나 방법의 수정이 필요한데 현지님이 도와줬다. 

![](https://i.ibb.co/HDmG65G/2020-11-19-9-16-59.png)

공식문서에 따르면 일반적인 데이터 플로우에서 벗어나 직접적으로 자식을 수정하는 경우가 있는데 이럴 때 ref와 dom을 사용해서 할 수 있다고 한다. constructor에 특정한 값을 ref로 만들고 DOM 노드를 얻기 위해 "current" 프로퍼티에 접근한다. 그 이후에 slider에 기본적으로 가지고 있던 slickNext와 slickPrev를 사용한다. 아직 100% 이해한 것은 아니지만 이렇게 접근이 필요할 때 또 쓸 수 있도록 노력해봐야겠다.

3. 인기 상품 

```jsx
<div className="cardList">
  {popularProductList.map((product) => {
    return (
      <div className="card">
        <div className="productImgBox">
          <img
            className="productImg"
            alt="제품사진"
            src={product.src}
            ></img>
        </div>
        <div className="productDescBox">
          <div>
            <span className="brandName">{product.brandName}</span>
          </div>
          <div className="productName">
            <span>{product.productName}</span>
          </div>
          <div className="discountPriceBox">
            <span className="discount">{product.discount}</span>
            <span className="productPrice">
              {product.productPrice}원
            </span>
          </div>
          <div className="likeReviewBox">
            <span className="productLike">
              좋아요<span>{product.productLike}</span>
            </span>
            <span className="productReview">
              후기
              <span>{product.productReview}</span>
            </span>
          </div>
        </div>
      </div>
    );
  })}
</div>
```

map으로 전체적으로 가벼워졌다. 추후에 api받아서 바로 사용할 수 있도록 준비해둔 상태! 백엔드분들 api만 만들어주시면 됩니다 ㅎㅎㅎㅎ 물론 아직 tab은 많이 구현한거 아니지만...tab별로 다른 화면 보여지도록 그 기능도 추가할 예정입니다...(되겠죠?)

## 오늘 느낀점

```jsx
class Home extends Component {
  render() {
    return (
      <>
        <Navbar />
        <Jumbotron />
        <PopularProduct />
        <PopularBrand />
        <Trend />
      </>
    );
  }
}

export default Home;
```

딱 컴포넌트 합치고 npm start로 화면 볼 때의 기분이란.......하아......너무 좋아ㅏㅏㅏㅏㅏㅏㅏ 딱 순서대로 잘 떨어지더라...혹시 겹치면 어쩌지..? 안맞으면 어쩌지 엄청 걱정했었는데 다행히 잘 맞았다...헤헤 기분이 좋은 하루 ! 그대신 자만하지말고 얼른얼른 더 치고 나가자 분명 나중에 되면 또 시간이 부족하겠지...꾸준하게 하되 더 빠르게 할 수 있도록 노력하자!!!!
오늘도 우리 팀원들 모두 고생 많았고 내일도 화이팅입니다!