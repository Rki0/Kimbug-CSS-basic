# 🥑 opacity, overflow, transform, visibility

이번에는 가끔씩 사용되는 css 속성에 대해서 알아보자.  
간단한 기능이거나 많이 사용되지 않는 속성들이라서 한번에 묶어서 설명을 진행한다.

# opacity

opacity는 불투명도를 조절하는 속성이다.  
0 ~ 1 사이의 값을 가지며, 0일수록 투명, 1일수록 불투명해진다.  
예시를 통해 살펴보자.

```css
.box {
  width: 300px;
  height: 300px;
  background-color: black;
  opacity: 0.5;
}
```

<img width="304" alt="스크린샷 2022-03-14 오후 8 37 15" src="https://user-images.githubusercontent.com/86224851/158164386-25334608-cae5-429a-a9b5-cde7a150ebab.png">

분명 배경 색이 black임에도 회색빛이 나는 것을 확인할 수 있다.  
opacity를 0.5로 설정해서 절반 정도의 투명도 효과를 부여했기 때문이다.

# overflow

overflow는 크기가 정해진 요소가 있을 때, 그에 속하는 자식, 자손 요소가 그 크기를 벗어난다면  
벗어난 컨텐츠를 어떤 식으로 처리할지를 정하는 속성이다.  
visible, auto, scroll, hidden 값을 사용할 수 있다.

visible은 요소가 선언되었을 때 기본적으로 가지고 있는 값이다.  
이 값은 넘쳐버린 부분을 그대로 그냥 보여준다.  
예시를 살펴보자.

```css
p {
  width: 500px;
  height: 400px;
  background-color: #0066ff;
  overflow: visible;
}
```

<img width="510" alt="스크린샷 2022-03-14 오후 8 46 49" src="https://user-images.githubusercontent.com/86224851/158165784-9a816243-f09e-4075-93d4-1979ea54b8c7.png">

설정된 범위를 넘어버린 컨텐츠를 전부 그대로 보여주는 것을 확인할 수 있다.  
모든 요소는 visible을 기본 값으로 가지므로 참고하자.

그런데..이렇게 visible 값을 유지한 채로 다른 요소들을 추가해버리면 아래와 같은 상황이 발생한다.

<img width="931" alt="스크린샷 2022-03-14 오후 9 14 31" src="https://user-images.githubusercontent.com/86224851/158170004-e84b2a05-5efd-4e2d-a9ad-b5c2baf08230.png">

컨텐츠가 넘처흘러도 그대로 보여주기 때문에 다른 요소 영역까지 침범해버리는 것이다.  
이를 막기 위해 등장한 개념이 바로 auto, scroll이다.

auto, scroll은 매우 비슷한 기능이다.  
컨텐츠가 넘쳐흘렀을 때 알아서 해라, 넘쳐흘렀을 때 스크롤 표시로 조절 할 수 있게 해라 라는 의미이다.  
두 값이 같은 기능을 하므로 하나만 설명하겠다.

```css
p {
  width: 500px;
  height: 400px;
  background-color: #0066ff;
  overflow: scroll;
}
```

<img src="https://user-images.githubusercontent.com/86224851/158285644-39a3ca1d-3080-4806-a8a6-11499edbf0f6.gif">

visible 값을 사용했을 때, 넘쳐흐른 컨텐츠가 모두 보였던데 반해  
이번에는 주어진 크기만큼만 컨텐츠를 보여주고, 넘어가는 부분은 스크롤을 움직여 확인 할 수 있게 되었다.

hidden은 넘쳐흘렀을 때 그 부분은 다 잘라서 보이지 않게한다.

```css
p {
  width: 500px;
  height: 400px;
  background-color: #0066ff;
  overflow: hidden;
}
```

<img width="504" alt="스크린샷 2022-03-14 오후 9 01 31" src="https://user-images.githubusercontent.com/86224851/158168105-8174473f-095b-4fec-a45b-986398daa787.png">

주어진 크기를 넘어간 컨텐츠가 전부 잘려서 안 보이는 것을 확인 할 수 있다.

추가적으로 overflow-x, overflow-y를 사용해서 특정 축에만 overflow를 지정할 수도 있다.  
p 태그를 감싸고 div 태그에 이를 적용해보겠다.  
div가 p보다 크기가 작다는 것을 눈여겨 보자.

```css
.box {
  width: 300px;
  height: 300px;
  overflow-x: scroll;
  overflow-y: hidden;
}

p {
  width: 500px;
  height: 400px;
  background-color: #0066ff;
}
```

<img src="https://user-images.githubusercontent.com/86224851/158285845-b6f1b995-ccb7-428e-81cc-d4c96e055a6e.gif">

우선 .box의 크기만큼 p 태그의 컨텐츠가 잘려있는 것을 볼 수 있다.  
x축 방향으로는 컨텐츠가 스크롤을 활용해 볼 수 있게 되어있으며,  
y축 방향으로는 넘쳐흐른 컨텐츠가 보이지 않게된 것을 확인 할 수 있다.

# transform

transform은 이 속성에서 제공하는 함수들에 값을 넣어서 다양한 효과를 이용할 수 있다.  
이 속성은 다른 요소에 영향을 미치지 않는다는 것이 포인트이다!  
변화가 생겼음에도 불구하고 원래 있던 위치를 모든 요소가 알고 있기 때문이다.  
이 속성에는 사용 가능한 값이 너무 많으므로 필요할 때 찾아서 보는게 낫다.  
여기서는 대표적으로 쓰인 3가지를 살펴보겠다.

translate(x,y)는 요소를 내가 원하는 방향으로 위치시키고 싶을 때 사용한다. 즉, 요소를 옮긴다.  
아래로 뒤집어놓은 x,y축 그래프 방향으로 이동을 한다.  
양수 값 x는 오른쪽, 양수 값 y는 아래쪽을 의미한다는 뜻이다.  
px, % 단위를 사용하며, % 단위를 사용할 때는 자기 자신의 사이즈를 기준으로 한다는 것을 기억하자!  
x는 본인의 width를, y는 본인의 height를 기준으로 한다!(% 단위 사용 시)  
예시를 살펴보자.

```css
.box {
  width: 300px;
  height: 300px;
  transform: translate(100px, 100px);
}
```

<img width="415" alt="스크린샷 2022-03-14 오후 9 34 36" src="https://user-images.githubusercontent.com/86224851/158173055-e6034d21-8048-4bbf-9732-e735f3a13825.png">

.box가 자기 본래 위치에서 우로 100px, 아래로 100px만큼 이동한 것을 확인 할 수 있다.  
또한, 다른 요소에 전혀 영향을 미치지 않는 것도 확인 가능하다.  
이번에는 % 단위를 사용해보자.  
100%는 본인의 크기 만큼 움직이는 것이므로 아래 코드는 대각선 방향으로 자기 크기만큼 이동했을 것이다.

```css
.box {
  transform: translate(100%, 100%);
}
```

<img width="613" alt="스크린샷 2022-03-14 오후 9 37 23" src="https://user-images.githubusercontent.com/86224851/158173503-92a85d67-d430-47b5-a501-ba38fd1d8b2f.png">

자신의 width만큼 우로, 자신의 height만큼 아래로 이동한 것을 확인 할 수 있다.

translateX, translateY를 사용해서 하나의 축에만 효과를 줄 수도 있다.

scale(N)은 N의 배율만큼 사이즈를 조절한다는 것이다.  
가령, 1이면 자신의 사이즈를 유지하고, 2는 두 배 커지고, 0.5는 1/2 크기로 줄어든다.

```css
.box {
  transform: scale(2);
}
```

<img width="456" alt="스크린샷 2022-03-14 오후 9 40 22" src="https://user-images.githubusercontent.com/86224851/158173971-2c8ee351-197e-4fff-baca-883723b9b26a.png">

width, height가 2배씩 늘어난 것을 확인 할 수 있다.

scale(x,y)로 사용하면 x 값은 width에 배율이, y 값은 height에 배율이 적용된다.

```css
.box {
  transform: scale(1, 2);
}
```

위 코드는 width는 그대로 유지하고, height를 2배로 키우겠다는 것이다.

<img width="312" alt="스크린샷 2022-03-14 오후 9 43 11" src="https://user-images.githubusercontent.com/86224851/158174389-25120bcd-a055-44a5-9779-ef8ee1983854.png">

코드 설명과 같은 결과가 나온 것을 확인 할 수 있다.

rotate(Ndeg)는 요소를 특정 각도만큼 회전할 때 사용된다.  
deg단위를 사용하며, 45deg는 45도 만큼 요소를 회전하고, 360deg는 360도 만큼 요소를 회전시키는 것을 의미한다.

```css
.box {
  transform: rotate(45deg);
}
```

<img width="385" alt="스크린샷 2022-03-14 오후 9 45 33" src="https://user-images.githubusercontent.com/86224851/158174721-d365c435-a9bf-4efb-b1bd-8ef2339a74ab.png">

45도만큼 요소가 회전된 것을 확인 할 수 있다.

# visibility

visibility는 요소를 보이게 하느냐, 안 보이게 하느냐를 결정하는 속성이다.  
각각 visible, hidden 값을 사용한다.

기본적으로 요소는 선언 시 눈에 보이므로 visible이 기본 값이다.  
hidden을 사용해보자.

```css
.box {
  width: 300px;
  height: 300px;
  background-color: black;
  opacity: 0.5;
  visibility: hidden;
}
```

<img width="386" alt="스크린샷 2022-03-14 오후 9 51 07" src="https://user-images.githubusercontent.com/86224851/158175622-05a0b7a0-d1a2-4d98-842d-b7325e67cab5.png">

hidden 값을 사용하자 시야에서 사라진 것을 확인 할 수 있다.  
그런데!!!! 말그대로 시야에서만 사라진 것이지 차지하고 있던 자리는 그대로 유지되고 있다!  
이 것이 display: none;과 visibility: hidden;의 차이이다.  
display: none;은 요소가 차지하던 자리마저도 없애버리는 반면,  
visibility: hidden;은 요소가 차지하는 자리는 없애지않는다.

이상으로 간단한 기능의 속성들에 대해서 알아보았다.  
🥳 수고하셨습니다~
