# 📱 Media Query

세상에는 정말 다양한 전자 기기가 있고, 그 것들은 각각 다른 화면 크기를 가지고 있다.  
프론트 엔드 개발자는 이런 화면 크기의 변경도 고려해야한다.  
화면 크기에 따라 다른 스타일을 적용할 때 사용하는 것이 바로 media query이다.  
간단한 예시를 통해 화면 크기에 따라 스타일을 조절하는 법을 알아보자.

```html
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
</head>
<body>
  <div class="box"></div>
</body>
```

media query를 사용하기 위해서는 HTML에 viewport meta가 선언되어 있어야한다.  
또한, 반응형 웹사이트를 제작할 때는 보통 작은 화면부터 시작을 한다.  
모바일 기기 크기에서 시작하는 것이 알아보기 편하고,  
화면 크기를 키워나가면서 스타일을 바꿀 때도 생각하기 편하기 때문이다.  
따라서, 아래 css는 모바일 화면을 기준으로 작성한 것이라고 생각하자.

```css
.box {
  width: 100%;
  height: 100vh;
  /* vw, vh는 viewport의 width, height의 퍼센트를 의미한다. 즉, 지금은 viewport height의 100%를 의미. */
  background-color: tomato;
  font-size: 30px;
  font-weight: 700;
  color: white;
}

.box::after {
  content: "Mobile";
}
```

<img width="497" alt="스크린샷 2022-03-08 오후 8 52 13" src="https://user-images.githubusercontent.com/86224851/157233096-a87abd72-0c53-4eee-965f-924b041f1282.png">

width가 320px인 모바일 기기를 시작으로 점점 화면 크기를 키워보자.  
방법은 아래와 같다.  
css에 @media를 사용하면 다른 크기의 화면에 적용될 스타일을 입력할 수 있다.  
@media를 통해 생성된 공간에는 새로운 css 공간이 생겼다고 보면된다.

```css
@media screen and (min-width: 426px) {
  .box {
    background-color: yellow;
  }

  .box::after {
    content: "Tablet";
  }
}
```

screen은 화면을 의미한다. 화면의 크기를 인식하겠다는 것이다.  
저 공간에는 screen뿐만 아니라 다양한 기기들이 들어가는데, 정말정말 웬만하면 screen을 사용하는 경우가 십중팔구이기 때문에 넘어가도록 하겠다.  
min-width는 최소 넓이를 의미한다.  
width가 최소 426px일 때 부터는 이 스타일을 적용하겠다는 것이다.(426px 이상부터는 이 스타일을 적용한다.)  
처음 적었던 css 코드와는 다르게 굉장히 간소하다...?  
@media를 사용할 때는 바뀌는 부분만 적어주면 되기 때문이다!
결과를 살펴보자.

<img width="790" alt="스크린샷 2022-03-08 오후 9 01 14" src="https://user-images.githubusercontent.com/86224851/157234372-5a52dcb4-86fc-4551-9ce5-e7ef772d6bb2.png">

지정한 조건을 만족할 만큼 화면을 키워줬더니 @media에 적용된 스타일이 나타났다!  
또 다른 크기에도 적용해보자.

```css
@media screen and (min-width: 769px) {
  .box {
    background-color: blue;
  }

  .box::after {
    content: "Desktop";
  }
}
```

<img width="783" alt="스크린샷 2022-03-08 오후 9 03 42" src="https://user-images.githubusercontent.com/86224851/157234698-31ca22fc-a5c5-4cd6-b7db-95e43e8499d8.png">

더 큰 width에서의 스타일을 적용했더니 그에 맞춰 스타일이 변한 것을 알 수 있다.

기초적인 방법을 알았으니 실제로 적용을 해보자.  
media query는 방법에 대한 것이지 코드에 대한 것이 아니기 때문에 css 코드보다는 뭐가 달라지는지만 살펴보자.  
구체적인 코드는 파일에 첨부해놓을 것이니 여기서는 짧게 살펴보겠다.

```css
.banner {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  background-color: #ffc82c;
}

@media screen and (min-width: 768px) {
  .banner {
    top: 0;
    bottom: auto;
  }
}
```

위에서 media query를 사용할 때는 바뀌는 부분만 적어주면 된다고 했다.  
현재 코드에서는 bottom: 0; 을 top: 0;로 바꾸고자 하는 것 같다.  
그런데...html,css를 공부하면서 top과 bottom, left와 right는 둘 중 하나만 쓰는 것이 레이아웃에 혼란을 줄일 수 있다고 했다.  
따라서, 이미 선언한 bottom의 효력을 없애기 위해서 auto값을 지정한 것을 확인할 있다.  
이처럼 바뀌는 부분만 적는게 아니라, 이미 적혀있는 코드의 효력까지 생각해서 media query를 작성한다면 훨씬 덜 혼란스럽게 작업할 수 있을 것이다.
