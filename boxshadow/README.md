# 🌚 box-shadow

box-shadow는 요소에 그림자를 줄 때 사용하는 속성이다.  
h-offset, v-offset, blur, spread, color 값을 사용하며 반드시 순서를 맞춰서 사용해야한다!  
각각 x, y, 흐린 정도, 그림자 사이즈, 색상을 의미한다.

x, y축으로 얼마나 이동할지를 정하는 것은 흔히 수학에서 공부하는 x,y축 그래프를 아래로 뒤집어서 생각하면 된다.  
x 값에 음수를 주면 왼쪽, 양수를 주면 오른쪽으로 이동하고,  
y 값에 음수를 주면 위쪽, 양수를 주면 아래쪽으로 이동한다.

blur는 흐린정도를 의미하며 px단위를 사용한다.  
값이 커질수록 색깔이 더 흐려진다.

spread는 그림자 사이즈를 의미하며 px단위를 사용한다.  
값이 커질수록 그림자 크기가 커진다.

색상은 말그대로 그림자 색상을 의미한다.

말로 설명하는 것보다 예시를 보는게 빠르다!  
예제로 사용할 코드는 아래와 같다.  
button에 부여한 기본 설정은 생략하도록 하겠다.

```html
<body>
  <button class="confirm-button">Confirm</button>
  <button class="cancel-button">Cancel</button>
  <button class="neumor-button"></button>
</body>
```

첫번 째 버튼부터 살펴보자.  
적용된 스타일은 다음과 같다.

```css
.confirm-button {
  background-color: #13ce66;
  box-shadow: 0 10px 16px 0 rgba(19, 206, 102, 0.35);
}
```

값에 0을 넣을 때는 단위를 생략한다는 것을 알아두자!!

코드를 분석하면 다음과 같다.  
x축으로는 움직임이 없고, y축으로는 10px만큼 아래로 이동.  
16px만큼 blur 처리가 되어있고, 그림자 크기는 키우지 않는다.  
색상은 rgba로 투명도를 줘서 자연스러운 느낌을 만들었다.  
결과를 살펴보자.

<img width="191" alt="스크린샷 2022-03-14 오전 9 41 08" src="https://user-images.githubusercontent.com/86224851/158086992-cb9ce81e-0e4e-41cb-bbb4-bc4885cf2153.png">

아주 자연스러운 버튼이 만들어졌다.  
두번 째 버튼을 살펴보자.  
적용된 스타일은 다음과 같다.

```css
.cancel-button {
  background-color: #ff4949;
  transition: box-shadow 250ms ease-in;
}

.cancel-button:hover {
  box-shadow: 0 10px 16px 0 rgba(255, 73, 73, 0.35);
}
```

이번에는 hover 상태일 때 box-shadow가 나오도록 설정해줬다.  
코드 내용은 첫번 째 버튼과 색상 외에 완전 동일하므로 생략하겠다.  
이 버튼에서는 이런 식의 효과를 넣는 방법도 있다는 것에 집중하자.

<img src="https://user-images.githubusercontent.com/86224851/158087504-fcd95e10-7092-4c34-9f30-7a94f4141b19.gif">

이번에는 세번 째 버튼을 살펴보자.  
최근에 neumorphism이라는 디자인의 버튼이 꽤나 유행이라고 하는데 이를 적용해봤다.

```css
.neumor-button {
  background: #e0e0e0;
  box-shadow: 20px 20px 60px #bebebe, -20px -20px 60px #ffffff;
}
```

코드가 이전 두 버튼과 다르게 속성값 개수도 다르고, 두 개나 적혀있는 것을 볼 수 있다.  
여러 개의 box-shadow 효과를 넣고자할 때는 쉼표를 사용해서 구분하여 입력하면 된다.  
만약 box-shadow 속성에 5개 값이 아닌 4개 값만 적혀있다면 spread(그림자 크기)가 생략된 것이고,  
3개 값만 적혀있다면 blur(흐린 정도)까지 생략된 것이다.

결과를 살펴보자.

<img width="142" alt="스크린샷 2022-03-14 오전 9 56 54" src="https://user-images.githubusercontent.com/86224851/158087822-dab0b056-0946-44d6-9cdb-7dd57e1e94a5.png">

box-shadow가 두 개 적용된 것을 확인할 수 있다.  
만약 neumorphism을 더 커스텀해보고 싶다면 아래 사이트에서 세부 사항을 조정해보길 바란다.  
https://neumorphism.io/#e0e0e0

이상으로 box-shadow 기초를 마치도록하겠습니다.  
🥳 수고하셨습니다~
