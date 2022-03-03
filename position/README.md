# Position

position은 요소의 이동을 위한 기준점을 잡아주는 기능을 한다.  
그 종류에는 static, relative, absolute, fixed, sticky가 있다.  
sticky는 아직 지원하지않는 브라우저가 많으므로 제외하고 살펴보도록 하겠다.

사용할 HTML 코드는 다음과 같다.

```html
<body>
  <div class="grandparent">
    <div class="parent">
      <div class="child red">Child</div>
      <div class="child yellow">Child</div>
      <div class="child blue">Child</div>
    </div>
  </div>
</body>
```

<img width="884" alt="스크린샷 2022-03-03 오전 10 08 52" src="https://user-images.githubusercontent.com/86224851/156476655-3ee03479-b3a8-48e2-8add-c3454cafa9ea.png">

## 1. static

모든 요소는 기본적으로 position 값이 static이다.  
HTML에 마크업한 요소는 별도 지정이 없으면 static이므로 별다른 특성은 없다.

## 2. relative

relative는 본인의 원래 위치의 left-top 모서리를 이동의 기준점으로 삼는다.  
예시를 통해 살펴보자.

```css
.yellow {
  background-color: yellow;
  position: relative;
  top: 20px;
  left: 20px;
}
```

<img width="885" alt="스크린샷 2022-03-03 오전 10 09 38" src="https://user-images.githubusercontent.com/86224851/156476720-3ea0571c-5c49-4ec4-b800-d2aa48c5717d.png">

.yellow가 본인의 원래 위치의 left-top 모서리를 기준으로 top과 left에서 각각 20px씩 떨어진 것을 확인 할 수 있다.  
이번에는 bottom과 right를 줘보겠다.

```css
.yellow {
  background-color: yellow;
  position: relative;
  bottom: 20px;
  right: 20px;
}
```

<img width="884" alt="스크린샷 2022-03-03 오전 10 14 57" src="https://user-images.githubusercontent.com/86224851/156477244-9f8c2b35-c04b-414c-9ed6-86ba5352a8ca.png">

.yellow가 본인의 원래 위치의 left-top 모서리를 기준으로 righ에서 20px 떨어졌고, bottom에서도 20px 떨어진 것을 확인 할 수 있다.  
사실 이 부분은 직관적으로 이해가 안되므로 웬만해서는 bottom은 여기서는 쓰지말아야할 것 같다...

relative는 float과 비슷하게 부모 요소로부터 공중으로 붕 뜬다. 다만, 본인의 원래 위치를 기억하고 있고, 부모나 형제 요소들 또한 이 요소의 원래 위치를 기억하고 있기 때문에 레이아웃의 붕괴는 일어나지않는다.

## 3. absolute

absolute는 자신이 기준으로 삼을 요소를 선택하여 작동하게 만든다.  
즉, absolute가 적용된 요소 자체가 어떤 기능을 하는 것이 아니라, 조건을 만족하는 다른 요소를 찾아서 그를 기준으로 삼는다는 것이다.  
그 조건이란 무엇인가??  
position 값이 static이 **아닌** 요소가 그것이다.  
absolute는 그 요소의 left-top 모서리를 기준으로 하여 작동하게 된다.

보통은 부모 요소에 relative를 부여하고 absolute를 사용한다.  
부모 요소에 absolute를 부여하면 부모 요소는 또 다시 absolute의 조건을 만족해야하는 루프에 빠져버리기 때문이다.  
예시를 통해 살펴보자.

```css
.parent {
  width: 400px;
  margin: 0 auto;
  background-color: #eff2f7;
  position: relative;
}

.red {
  background-color: red;
  position: absolute;
  left: 100px;
}
```

<img width="883" alt="스크린샷 2022-03-03 오전 10 33 35" src="https://user-images.githubusercontent.com/86224851/156479151-36054b22-6911-449e-a9a3-129d8fa9e3d9.png">

.red의 position이 abosolute이고 그 부모 요소인 .parent가 position이 relative이므로, 부모 요소를 기준으로 left에서 100px 떨어진 것을 볼 수 있다.  
이번에는 .parent 말고 .grandparent에 relative를 줘보겠다.

```css
.grandparent {
  width: 800px;
  margin: 0 auto;
  background-color: #1f2d3d;
  position: relative;
}
```

<img width="884" alt="스크린샷 2022-03-03 오전 10 43 02" src="https://user-images.githubusercontent.com/86224851/156480161-ba68e85b-54ea-4206-a89b-fc61425178a3.png">

이젠 확실히 absolute가 어떤 기준을 잡고 움직이는지 이해했다!

absolute도 사용 시 float과 유사한 현상이 발생한다.  
부모 요소가 자식 요소의 높이를 인식하지 못하게 되고, display 속성이 block 값으로 변경되며, 그런데 길막을 하지 못하는 block이 되어버린다는 것이다.

방금 봤던 예시를 살펴보면 .red가 붕 뜬 것을 볼 수 있다.  
다만 float과 다른 점은 텍스트나 인라인 요소들이 이 요소를 인식하지 않는다는 것이다! 그냥 뚫고 지나간다.

## 4. fixed

fixed는 absolute와 같은 현상이 발생한다.(float과 유사했던 현상들)  
다만, fixed는 viewport(브라우저 화면)를 기준점으로 해서 자신을 이동한다.  
따라서 스크롤을 해서 움직이는 화면이라고 할지라도 그 자리에 항상 고정되어 있다.

```css
.red {
  background-color: red;
  position: fixed;
  bottom: 0px;
}
```

<img width="885" alt="스크린샷 2022-03-03 오전 10 51 55" src="https://user-images.githubusercontent.com/86224851/156481040-22cd3404-5e9a-4f0d-8471-bc4bb3a34ced.png">

예시를 통해 viewport를 기준으로 요소가 이동한 것을 확인 할 수 있다.  
이 요소는 스크롤을 하더라도 계속 저 자리에 남아있다!

## z - index

z-index는 요소들의 수직방향(모니터를 뚫고 나오는 방향)으로의 레벨을 지정한다.  
요소들이 붕 떠버리면 당연히 붕 뜨지않은 요소들과 높이의 차이가 발생할 것이다. 물론 모니터 상에서는 판별하기 어렵지만 말이다.  
이 때, 이 높이라는 성질을 나타내는 것이 z-index이다.  
z-index의 값이 클수록 더 위쪽에 있다는 것을 말한다.
예시를 살펴보자.

```css
.red {
  background-color: red;
  position: absolute;
  left: 100px;
  z-index: 1;
}

.yellow {
  background-color: yellow;
  position: absolute;
  left: 50px;
}
```

<img width="883" alt="스크린샷 2022-03-03 오전 10 59 41" src="https://user-images.githubusercontent.com/86224851/156481821-2717226e-a0b2-4b40-86d9-6dd32eaaf4a0.png">

CSS는 위에서 아래로 흐르는 코드이므로 .yellow가 .red를 50px 덮어버리는 것이 정상이다.  
그런데 .red에 z-index를 부여해서 .yellow보다 값을 크게 만들어줬더니 .red가 .yellow를 덮어버린 것을 볼 수 있다.  
z-index는 별도로 설정하지 않으면 auto 값을 가지기 때문에, 이를 별도로 설정한 .red에 .yellow가 덮혀버린 것이다!

## 약간의 팁

position을 사용하다보면 자연스럽게 top, bottom, right, left를 사용하게된다.  
이 때 top을 사용하면 bottom은 쓰지말고, left를 사용하면 right는 쓰지않도록 하자.  
예를 들어, 하나의 요소에 right, left가 동시에 작성하면 이해하기도 어렵고, 코드만 더러워지기 때문이다.
