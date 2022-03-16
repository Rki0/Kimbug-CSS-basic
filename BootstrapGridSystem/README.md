# Bootstrap Grid System

디자이너가 프론트엔드 개발자에게 시안을 줄 때 아무렇게나 막 디자인해서 주는 것이 아니다.  
보통 grid system을 사용해서 요소의 크기를 조절하고 배치해서 디자인을 한다.  
Grid system이란 화면을 몇 개의 column으로 분할해서 사용하는 것을 말한다.  
container, column, gutter가 주요 개념으로 사용된다.

container는 grid system이 적용된 영역 전체를 의미한다.  
보통 12칸으로 화면을 분할해서 사용한다.  
분할된 화면의 한 칸을 column이라고 한다.  
보통 이 column을 기준으로 요소 사이즈를 잡는다. 예를들어 이건 column 3개 크기로 하자~.  
요소의 크기를 정해서 나열을 했으면 각 요소에 간격을 주게 되는데, 이게 gutter라고 불린다.  
우리가 아는 padding과 유사한 개념이라고 생각하면 편하다.

이러한 grid system을 쉽게 구현할 수 있게 도와주는 css 프레임워크가 바로 Bootstrap이다!  
Bootstrap은 12칸 분할을 기준으로 하며, 하나의 row에 12개의 column이 들어가 있다.

Bootstrap을 사용하려면 css를 링크하거나 js파일을 링크하는 방법이 있다.  
사용하고자 기능에 따라 css 링크만 해도 되는 경우가 있고, 본문에서는 그 방법만 다뤄볼 것이다.

```html
<head>
  <link
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css"
    rel="stylesheet"
    integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3"
    crossorigin="anonymous"
  />
  <link rel="stylesheet" href="./style.css" />
</head>
```

Bootstrap에서 가져온 css 링크를 본인이 사용하고자하는 css 파일 가장 위에 복붙해주면 사용할 수 있다.

Bootstrap에는 규칙이 있다. 항상 아래와 같은 구조를 따라야 한다는 것이다.

```html
<body>
  <div class="container">
    <div class="row">
      <div class="col"></div>
    </div>
  </div>
</body>
```

항상 .container -> .row -> .col의 순서로 요소를 작성하며, 따로 선언하고싶은 클래스가 있다면 반드시 .col 내부에 작성해야만 한다!  
예시를 통해 살펴보자.

```html
<body>
  <div class="container">
    <div class="row">
      <div class="col-1">
        <p class="my-class">col-1</p>
      </div>
    </div>
  </div>
</body>
```

.my-class를 .col 내부에 선언한 것을 볼 수 있다.  
또한, col-1 이라고 적혀 있는데, 이는 12칸으로 나눠진 grid에서 1칸만 사용하겠다는 뜻이다.  
예를들어, col-2는 2칸, col-6는 6칸을 사용하겠다는 의미가 된다.

Bootstrap은 12칸을 기본 grid로 하다고 했었다.  
그렇다면, col-1과 col-12를 하나의 row에 작성하면 어떻게 될까?

```html
<body>
  <div class="container">
    <div class="row">
      <div class="col-1">
        <p class="my-class">col-1</p>
      </div>
      <div class="col-12">
        <p>col-12</p>
      </div>
    </div>
  </div>
</body>
```

<img width="1440" alt="스크린샷 2022-03-16 오후 3 30 49" src="https://user-images.githubusercontent.com/86224851/158530153-aec388dc-6e14-4aa6-a3f8-f7d38879ab95.png">

자동으로 12칸을 가지는 요소는 다른 줄에 표시되는 것을 확인 할 수 있다.  
만약, col-11로 했다면 같은 줄에 표시되었을 것이다.

Bootstrap은 자체적으로 반응형 미디어 쿼리를 적용해놔서 화면 크기에 맞춰 요소가 조절된다.  
변화가 발생하는 화면 크기에 대한 자세한 설명은 Bootstrap 홈페이지에서 쉽게 확인 가능하다.  
가령, 아래와 같이 col을 배치했다고 하자.

```html
<body>
  <div class="container">
    <div class="row">
      <div class="col-5">
        <p>col-5</p>
      </div>
      <div class="col-3">
        <p>col-3</p>
      </div>
      <div class="col-4">
        <p>col-4</p>
      </div>
    </div>
  </div>
</body>
```

일반적인 랩탑 화면에서는 아래와 같이 표현될 것이다.

<img width="1440" alt="스크린샷 2022-03-16 오후 3 42 07" src="https://user-images.githubusercontent.com/86224851/158531630-da72bf3d-99eb-49c0-aa4e-60f1485cd06b.png">

여기서 화면을 점점 줄여나가면 자동적으로 칸 크기가 줄어들어서 요소의 크기가 자동으로 조절된다.

<img src="https://user-images.githubusercontent.com/86224851/158532219-bc6729c3-0dca-427a-8d5d-ae775fddaa8f.gif">

col-5, 3, 4를 보면 화면이 줄어들 수록 배율이 자동적으로 조정되는 것을 확인 할 수 있다.  
이렇게 화면 크기에 따라 미디어 쿼리가 적용되 있는데, 특정 화면 크기마다 col의 크기를 변경하는 것도 가능하다.  
아래 코드를 살펴보자.

```html
<body>
  <div class="container">
    <div class="row">
      <div class="col-12 col-sm-6 col-md-4 col-lg-3 col-xl-2">
        <p>column</p>
      </div>
    </div>
  </div>
</body>
```

sm, md, lg, xl이 col에 붙어있는 것을 볼 수 있다.  
sm = small = 576px, md = medium = 768px, lg = large = 992px, xl = X-large = 1200px를 의미한다.  
각각 화면 크기를 의미하는 것으로, break points라고 부른다.  
위 코드를 해석하면 다음과 같다.  
모바일 화면에서는 이 col이 12칸을 차지하고, 576px이 넘어가면 6칸, 768px이 넘어가면 4칸, 992px이 넘어가면 3칸, 1200px이 넘어가면 2칸을 차지하게 만들어라~ 는 의미이다.  
실제 화면에 어떤 식으로 적용되는지 살펴보자.

<img src="https://user-images.githubusercontent.com/86224851/158533630-576f9039-5aff-429a-b9de-81621da85ecd.gif">

화면 크기를 늘리면서 break points를 지날 때마다 col의 칸에 변화가 생기는 것을 확인 할 수 있다.  
이런 특징을 활용해서 아래와 같은 방식으로도 사용 할 수 있다.

```html
<body>
  <div class="container">
    <div class="row">
      <div class="col-12 col-md-6 col-lg-4">
        <p>column</p>
      </div>
      <div class="col-12 col-md-6 col-lg-4">
        <p>column</p>
      </div>
    </div>
  </div>
</body>
```

각각의 p가 모바일 화면에서는 12칸을 전부 차지하므로 두 줄로 표시되지만,  
md에서는 각각 6칸을 차지하므로 1줄에 표시될 것이고,  
lg에서는 각각 4칸을 차지하므로 1줄에 표시되고 칸도 줄어든다.  
실제 화면을 보면서 어떻게 동작하는지 살펴보자.

<img src="https://user-images.githubusercontent.com/86224851/158534498-064a97f2-31d7-4e22-8d31-d8d0fadf0657.gif">

이렇게 Bootstrap에서의 Grid system을 알아보았다.  
정말 흔하게 사용되는 프레임워크이므로 숙지할 필요가 있으며, 앞으로 잘 활용해보도록 하자.  
🥳 수고하셨습니다~
