# ⌨️ Web Font

만약 작업 중에 새로운 폰트를 사용하였다면, 이는 사용자의 환경에 적용되지 않을 수 있다.  
지정해놓은 폰트가 사용자에게 없다면, 기본 폰트로 출력이 되기 때문이다.  
이런 문제를 해결하기 위해서는 폰트를 가져와서 사용하거나, 제작자가 직접 제공하거나 둘 중 하나를 반드시 해줘야한다.

## 폰트를 가져와서 쓰는 방법

다양한 곳에서 폰트를 다운 받을 수 있는데, 보통 https://fonts.google.com/ 에서 많이 다운받아 사용한다.  
오픈 소스라서 괜찮다!!  
이렇게 만들어져 있는 폰트를 가져와서 쓰는 방법은 link 태그를 이용하는 것이다.

어떤 단계를 거쳐서 사용되는지 처음부터 살펴보자.

1. 방금 위에서 언급한 사이트에 접속한다.
2. 원하는 폰트를 클릭한다.
3. "Select this style"을 클릭한다.  
   <img width="1440" alt="스크린샷 2022-03-10 오전 10 55 47" src="https://user-images.githubusercontent.com/86224851/157573061-d25e066d-f555-4973-807a-c37e4ab8553c.png">

4. "View your selected families"를 클릭한다.  
   <img width="1440" alt="스크린샷 2022-03-10 오전 10 58 38" src="https://user-images.githubusercontent.com/86224851/157573318-3f04fb54-fb07-4420-8032-b4d96719551b.png">

5. html에 작성해야할 부분과 css에 작성해야할 부분을 확인할 뒤 본인의 코드에 그대로 입력해준다.  
   <img width="1440" alt="스크린샷 2022-03-10 오전 11 01 53" src="https://user-images.githubusercontent.com/86224851/157573581-8e1a8a65-d07c-42d7-b1c3-02971fc8de05.png">

html과 css에는 아래와 같이 추가가 될 것이다.

```html
<head>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link
    href="https://fonts.googleapis.com/css2?family=Libre+Baskerville&display=swap"
    rel="stylesheet"
  />
</head>
```

```css
body {
  font-family: "Libre Baskerville", serif;
}
```

이렇게 작성을 마쳤으면 폰트가 적용이 된다.  
body 태그에 스타일을 적용하면 모든 요소에 일괄 적용되므로 보통 body 태그에 폰트를 입력한다.  
적용 전과 후를 비교해보자.  
첫번 째 사진이 적용 전이고, 두번 째 사진이 적용 후이다.

<img width="563" alt="스크린샷 2022-03-10 오전 11 09 58" src="https://user-images.githubusercontent.com/86224851/157574394-48baec9c-02c0-492d-84c0-21f9a9db5b89.png">

<img width="573" alt="스크린샷 2022-03-10 오전 11 09 10" src="https://user-images.githubusercontent.com/86224851/157574296-a13f6bf2-81cb-453c-a66b-fdb715fe9d3a.png">

변경된 폰트가 잘 적용된 것을 확인 할 수 있다.

## 직접 제공하는 방법

폰트를 직접 제공하는 방법은 제작자가 별도로 폰트 css 파일을 만들어서 서버에 올려놓고 사용하는 것을 말한다.  
항상 import를 해줘야 다른 곳에 있는 폰트를 사용할 수 있는데 두 가지 방법이 있다.  
하나는 html에 import를 하는 것이고, 다른 하나는 css에 import를 하는 것이다.

우선, 폰트 css 파일을 만드는 법부터 살펴보자.

```css
@font-face {
  font-family: "Kimbug";
  font-style: normal;
  font-weight: 400;
  src: url("./assets/font/NanumSquareRoundR.eot");
  src: url("./assets/font/NanumSquareRoundR.eot?#iefix") format("embedded-opentype"),
    url("./assets/font/NanumSquareRoundR.woff2") format("woff2"),
    url("./assets/font/NanumSquareRoundR.woff") format("woff"), url("./assets/font/NanumSquareRoundR.ttf")
      format("truetype");
}
```

font-family에는 앞으로 이 폰트를 사용할 때 어떤 이름으로 부를지를 적어준다.  
font-style에는 해당 폰트가 가지고 있는 font-style을 적어준다. 간혹 italic체 전용 폰트도 있으니 이 부분은 주의해서 사용하자!  
font-weight에는 해당 폰트 파일에 지정되어있는 폰트의 굵기를 적어준다. 파일명 끝에 R이 붙어있는걸 봐서는 regular이므로 400을 입력해줬다.  
src에는 내가 사용할 폰트를 지정한다.  
다만, 각각의 브라우저마다 지원하는 폰트 확장자가 다르기 때문에 format을 이용해서 지정을 해줘야한다.  
이를 편하게 작업할 수 있게 만들어주는 사이트가 있다.

https://css-tricks.com/snippets/css/using-font-face-in-css/

위 링크에 들어가면 브라우저마다 지정되어있는 확장자를 알려주고 코드로 미리 만들어놨으므로 유용하게 사용하자.

마지막으로 font-weight에 따라 위 코드를 똑같이 반복해주면 된다.  
파일명 끝 부분과 font-weight만 변경하면서 적어주면 된다.

폰트 css 파일을 제작했으니 import를 해보자.

우선, html에 import하는 방법에 대해 알아보겠다.  
매우 간단하다. 별도로 만든 폰트 css 파일을 html에 link 해주면 된다.

```html
<head>
  <link rel="stylesheet" href="./fonts.css" />
</head>
```

이제 다른 css 파일에서 작성자가 지정한 폰트를 사용할 수 있게 된다.

```css
body {
  font-family: "Kimbug", sans-serif;
}
```

작성자가 별도로 지정한 이름으로 사용되는 것을 확인 할 수 있다.  
결과를 살펴보자.

<img width="557" alt="스크린샷 2022-03-10 오전 11 34 12" src="https://user-images.githubusercontent.com/86224851/157577054-f269de91-019a-4747-af75-f86bca1b5484.png">

잘 적용된 것을 확인했다.

다음으로는 css에 import를 하는 방법을 알아보자.  
굉장히 간단하다.

```css
@import url("./fonts.css");

body {
  font-family: "Kimbug", sans-serif;
}
```

@import를 통해 폰트 css 파일을 연결해주면, 바로 사용할 수 있게 된다.  
적용된 화면은 바로 위 사진과 같으므로 생략하겠다.

지금까지 새로운 폰트를 사용자에게 제공하는 방법에 대해 알아보았습니다.  
🥳 수고하셨습니다.
