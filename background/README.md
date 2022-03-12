# 🌌 Background

이번에는 배경을 설정하는 방법에 대해서 알아보자.
예제로 사용할 html 코드는 아래와 같다.

```html
<body>
  <div class="box"></div>
</body>
```

기본 설정으로 가져갈 css 코드는 아래와 같다.

```css
.box {
  width: 300px;
  height: 300px;
}
```

## background-color

이 부분은 사실 typography에서 했던 것과 동일하다.  
hex, rgb, rgba를 사용할 수 있다.  
완벽하게 동일한 내용이므로 생략하겠다.

## background-image

background-image는 배경으로 이미지를 넣고싶을 때 사용한다.  
반드시 url() 함수를 사용해서 이미지의 경로를 입력해줘야한다!  
두 가지 방법이 있는데, 하나는 자체적으로 가지고 있는 이미지를 사용하는 경우이고, 다른 하나는 외부 이미지 url을 가져와서 사용하는 경우이다.

우선, 자체적으로 가지고 있는 이미지를 사용하는 방법에 대해서 살펴보자.

```css
.box {
  background-image: url(./assets/icon-star.svg);
}
```

간단하다. 해당 이미지가 있는 파일 경로를 작성하면 된다.

다음으로, 외부 이미지 url을 가져와서 사용하는 방법을 살펴보자.

```css
.box {
  background-image: url(https://images.unsplash.com/photo-1646941382754-cc9dc609dc8b?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=687&q=80);
}
```

이 또한 간단하다. 이미지 링크를 그대로 입력해주면 된다.

## background-repeat

background-repeat는 배경 이미지의 반복을 설정한다.  
기본적으로 모든 배경 이미지는 반복이 된다.  
예시를 한번 봐보자.

<img width="311" alt="스크린샷 2022-03-11 오전 11 29 12" src="https://user-images.githubusercontent.com/86224851/157790671-7709286b-4e54-42b3-aa77-4b191f04e15b.png">

분명히 내가 입력한 이미지는 별이 하나만 나오는 이미지인데, .box에 지정해놓은 width, height에 맞춰 이미지를 무한 반복하는 것을 확인 할 수 있다.  
이런 현상을 막기 위해 아래와 같이 속성을 추가한다.

```css
.box {
  background-repeat: no-repeat;
}
```

repeat와 no-repeat 값을 사용할 수 있는데, 위 코드는 이미지의 반복을 허용하지 않겠다는 것이다.  
결과는 아래와 같다.

<img width="326" alt="스크린샷 2022-03-11 오전 11 38 00" src="https://user-images.githubusercontent.com/86224851/157791539-f5da597b-a746-495e-93e8-c7aa547570e2.png">

이미지의 무한 반복이 없어진 것이 확인 가능하다.

## background-size

background-size는 배경 이미지의 크기를 조절한다.  
사실 절대적인 크기라기보다는 이미지가 들어간 공간에 맞춰 어떻게 오려낼지를 정한다고 보는게 정확한 것 같다.  
크게 contain, cover, 사용자 설정값을 사용한다.  
아래와 같은 직사각형의 이미지가 있고, 이를 .box에 넣고자한다.  
아, 무료 이미지니까 저작권은 걱정말아주세요...

<img width="394" alt="스크린샷 2022-03-11 오전 11 45 12" src="https://user-images.githubusercontent.com/86224851/157792314-63f04c14-8984-44ea-bf2b-11f3f4317e97.png">

이 이미지를 .box의 배경 이미지로 넣은 결과는 아래와 같다.

<img width="307" alt="스크린샷 2022-03-11 오전 11 46 36" src="https://user-images.githubusercontent.com/86224851/157792433-e2cbdbac-525d-49aa-9111-49be372a2514.png">

도대체 이게 무슨 이미지인가 예상도 못 할 정도로 잘려있다.  
아무 설정도 하지않으면 이처럼 .box의 크기에 맞춰 그 부분만 잘린 이미지가 보이게 된다.  
이번에는 contain 속성을 사용해보도록 하겠다.  
적용 원리를 쉽게 파악하기 위해 배경색을 파란색으로 변경했다.

```css
.box {
  background-size: contain;
}
```

<img width="308" alt="스크린샷 2022-03-11 오전 11 49 46" src="https://user-images.githubusercontent.com/86224851/157792770-83f660dd-af49-45b0-abd2-f1642c2fa9b6.png">

전체 이미지가 .box 크기 안으로 맞춰져서 적용된 것을 확인 할 수 있다.  
이처럼 contain은 이미지가 들어갈 공간에 이미지의 모든 부분이 보일 수 있게 해준다.

이번에는 cover를 사용해보자.

```css
.box {
  background-size: cover;
}
```

<img width="311" alt="스크린샷 2022-03-11 오전 11 51 25" src="https://user-images.githubusercontent.com/86224851/157792945-0222eb93-5544-41eb-a0e7-41a13c7f3a9d.png">

이미지가 .box의 크기에 꽉 맞춰서 잘린 것을 확인 할 수 있다.  
아무 설정도 안 했을 때와 다른 점은 이미지의 특정 부분만 잘린게 아니라, 이미지를 최대한 .box 크기에 맞추고 남은 부분을 잘랐다는 점이다.

이번에는 내가 직접 크기를 설정해보자.

```css
.box {
  background-size: 50% 80%;
}
```

<img width="306" alt="스크린샷 2022-03-11 오전 11 55 44" src="https://user-images.githubusercontent.com/86224851/157793377-ade20ced-37ad-47c6-a433-dfe61f8ecae9.png">

width는 .box의 50%, height는 .box의 80%가 적용된 것을 확인 할 수 있다.  
여기에는 % 단위 말고도 다양한 값을 사용할 수 있다.

```css
.box {
  background-size: 100px 100px;
}
```

width, height를 각각 100px로 지정한 결과이다.

<img width="309" alt="스크린샷 2022-03-11 오전 11 59 08" src="https://user-images.githubusercontent.com/86224851/157793749-32a06b6d-d6e2-4a35-b3af-3bf897ac8179.png">

```css
.box {
  background-size: 70% auto;
}
```

width는 70%가 적용되었고, height는 auto 값으로 자동적으로 크기를 맞춰주었다.

<img width="304" alt="스크린샷 2022-03-11 오전 11 59 59" src="https://user-images.githubusercontent.com/86224851/157793862-8908833c-a78d-45d3-812f-691c95ac52d7.png">

```css
.box {
  background-size: auto 80%;
}
```

이번에는 width에 auto를 적용했고, height에 80
% 값을 넣었다.

<img width="306" alt="스크린샷 2022-03-11 오후 12 01 39" src="https://user-images.githubusercontent.com/86224851/157794036-9ac318e2-b7fe-4ae2-a615-b49236d974ad.png">

auto는 한쪽에 설정된 값에 맞춰 최대로 표현할 수 있는 범위까지를 자동적으로 설정해준다는 것을 알 수 있다.  
물론, auto 값을 width, height에 동시에 써버리면 이미지가 이상해진다...

## background-position

배경 이미지를 어떻게 위치시킬 것인지를 정한다.  
x축, y축 위치를 명시해 줘야하며,  
center, bottom, left, top, % 단위, px 단위 등등...다양한 값을 사용할 수 있다.

```css
.box {
  background-position: 10px 50px;
}
```

이 코드는 이미지를 top-left로부터 x축으로는 10px, y축으로는 50px을 이동시킨다.  
결과는 아래와 같다.

<img width="304" alt="스크린샷 2022-03-11 오후 7 04 25" src="https://user-images.githubusercontent.com/86224851/157846020-190f2f09-a5e1-4ed6-887f-1102a9c1b41b.png">

```css
.box {
  background-position: left bottom;
}
```

이 코드는 이미지를 x축 방향으로 왼쪽 정렬, y축 방향으로 아래 정렬을 한다.  
결과는 아래와 같다.

<img width="305" alt="스크린샷 2022-03-11 오후 7 06 10" src="https://user-images.githubusercontent.com/86224851/157846292-97e20789-1c7f-47f8-a85f-f80c3fa19b10.png">

```css
.box {
  background-position: center center;
}
```

이 코드는 이미지를 x축 방향으로 가운데 정렬, y축 방향으로 가운데 정렬을 한다.  
결과는 아래와 같다.

<img width="303" alt="스크린샷 2022-03-11 오후 7 07 15" src="https://user-images.githubusercontent.com/86224851/157846503-3d000b79-59b0-4795-9093-2b84cb0787f6.png">
  
이렇게 background에 관련된 속성들을 살펴보았다.  
🥳 수고하셨습니다~
